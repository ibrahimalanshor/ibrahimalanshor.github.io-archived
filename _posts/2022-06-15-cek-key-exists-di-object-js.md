---
layout: post
title: "Cara Cek Apakah Sebuah Key Ada di Sebuah Objek Javascript"
tags: [javascript]
date: 2022-06-15 16:00:00 +0700
---

Untuk mengecek apakah sebuah key ada di sebuah objek javascript, gunakan operator `in`.

```js
const key = 'nama'
const obj = {
  nama: 'ole'
}

console.log(key in obj) // true
console.log('umur' in obj) // false
```

Perlu diperhatikan operator `in` melakukan operasi pengecekan terhadap semua key pada objek termasuk `prototype chain` objek tersebut.

Gunakan method `hasOwnProperty` pada objek untuk mengecek keynya saja.

```js
const key = 'nama'
const obj = {
  nama: 'ole'
}

console.log(obj.hasOwnProperty(key)) // true
console.log(obj.hasOwnProperty('umur')) // false
```

Jika anda menggunakan `eslint` method `hasOwnProperty` mungkin akan memberikan error dari aturan `no-prototype-builtins`.

Gunakan cara di bawah ini untuk mengatasinya.

```js
const key = 'nama'
const obj = {
  nama: 'ole'
}

console.log(Object.prototype.hasOwnProperty.call(obj, key)) // true
console.log(Object.prototype.hasOwnProperty.call(obj, 'umur')) // false
```