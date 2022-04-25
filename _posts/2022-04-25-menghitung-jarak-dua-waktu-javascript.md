---
layout: 'post'
title: 'Menghitung Jarak Dua Waktu Javascript'
date: 2022-04-25 11:00:00 +0700
---

## Siapkan Waktu Target

```js
// Waktu Sekarang
const date1 = new Date('2022-04-25T11:00:00')

// Waktu Kemudian
const date2 = new Date('2022-05-17T15:00:00')
```

## Hitung Jarak

Ubah dua waktu menjadi millisecond, jarak dihasilkan dari pengurangan millisecond dua waktu tersebut

```js
const diff = date2.getTime() - date1.getTime()
```

## Ubah Ke Bentuk Lain

Bagi jarak ke dalam bentuk waktu tertentu, misal ke hari, jam, menit, dsb.

``` js
const day = Math.floor(diff / (1000 * 60 * 60 * 24))
const hour = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
const minute = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60))
const second = Math.floor((diff % (1000 * 60)) / (1000))

console.log('Diff in day : ', day)
console.log('Diff in hour : ', hour)
console.log('Diff in minute : ', minute)
console.log('Diff in second : ', second)
```

```bash
'Diff in day : ' 22
'Diff in hour : ' 4
'Diff in minute : ' 0
'Diff in second : ' 0
```