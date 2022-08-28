---
layout: post
title: "Cara Menggunakan Transaction Pada Mongoose"
tags: [mongoose]
date: 2022-06-21 09:30:00 +0700
---

Transaction adalah cara untuk menangani beberapa proses operasi database dalam satu proses. Sehingga jika ada satu proses yang bermasalah atau gagal, proses yang lainnya akan digagalkan atau dikembalikan seperti semula.

Jika anda menggunakan mongoose, mongoose menyediakan fitur transaction yang memungkinkan anda untuk mengeksekusi beberapa opereasi dan membatalkan semua operasi jika salah satunya gagal.

Langsung saja berikut cara menggunakan transaction pada mongoose.

> Pastikan anda sudah membuat koneksi mongoose dan menyiapkan sebuah model collection.

## Impor Model dan Modul startSession dari Mongoose

```js
const account = require('../models/account')
const history = require('../models/history')
const { startSession } = require('mongoose')
```

## Buat Client Session

Mongoose Session digunakan untuk memulai mongodb session untuk mendapatkan fitur transactions.

```js
function addBalance(id, amount) {
  const session = await startSession()  
}
```

## Mulai Transaksi

Mulai transaksi dengan method `startTransaction` pada session, simpan transaksi dengan `commitTransaction`, gagalkan transaksi dengan `abortTransaction`, dan tutup sesi dengan `endSession`.

Tambahkan `session` pada setiap operasi.

```js 
try {
  session.startTransaction()

  await history.create([
    { amount }
  ], { session })

  await account.updateOne(
    { _id: id },
    {
      $inc: {
        balance: amount
      }
    },
    { session }
  )

  await session.commitTransaction()

  session.endSession()
} catch (err) {
  await session.abortTransaction()
  session.endSession()
  console.log(err)
}
```

## Kode Akhir

Jika proses meng-update balance model `account` gagal, maka data yang disimpan pada model `history` sebelumnya akan dikembalikan.

```js
const account = require('../models/account')
const history = require('../models/history')
const { startSession } = require('mongoose')

function addBalance(id, amount) {
  const session = await startSession()
  
  try {
    session.startTransaction()

    await history.create([
      { amount }
    ], { session })

    await account.updateOne(
      { _id: id },
      {
        $inc: {
          balance: amount
        }
      },
      { session }
    )

    await session.commitTransaction()

    session.endSession()
  } catch (err) {
    await session.abortTransaction()
    session.endSession()
    console.log(err)
  }
}
```