---
layout: post
title: "Cara Menggunakan Enum Pada Mongoose"
tags: [mongoose]
date: 2022-06-21 09:00:00 +0700
---

Enum pada database umumnya digunakan untuk memberikan tipe data khusus pada kolom yang nilainya sudah ditentukan sebelumnya yang berupa sekumpulan konstanta.

Jadi nilai yang akan dimasukan ke kolom dengan tipe data enum harus ada di konstanta yang ditentukan pada kolom enum tersebut.

Anda juga dapat menggunakan enum pada mongoose, enum pada mongoose bukanlah tipe data melainkan `validator` untuk tipe data `String`.

Enum dibuat dengan menambahkan properti enum berupa array berisi data konstanta pada `path` yang ditentukan.

Contoh.

```js
const { Schema } = require('mongoose')

const UserSchema = new Schema({
  role: {
    type: String,
    enum: ['admin', 'operator', 'user']
  }
})
```

Atau bisa menggunakan `object syntax` yang juga dapat digunakan untuk menentukan pesan error.

Contoh.

```js
const { Schema } = require('mongoose')

const UserSchema = new Schema({
  role: {
    type: String,
    enum: {
      values: ['admin', 'operator', 'user'],
      message: '{VALUE} is not supported'
    }
  }
})
```

Sumber : [https://mongoosejs.com/docs/validation.html](https://mongoosejs.com/docs/validation.html)