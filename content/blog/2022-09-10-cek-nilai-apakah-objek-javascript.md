---
layout: post
title: "Cek Apakah Nilai Adalah Sebuah Objek Javascript"
tags: [javascript]
date: 2022-09-10 20:30:00 +0700
---

Pertama, gunakan operator `typeof` untuk mendapatkan tipe data dari nilai / variabel yang akan kita cek.

```js
function cekApakahObjek(value) {
  return typeof value === 'object'
}

console.log( cekApakahObjek({}) ) // true
console.log( cekApakahObjek({ prop: 'value' }) ) // true
console.log( cekApakahObjek('string') ) // false
console.log( cekApakahObjek(13) ) // false
console.log( cekApakahObjek(false) ) // false
```

Cara ini tidak tepat, jika kita ingin menganggap `array` dan `null` bukanlah objek, karena pada javascript `null` dan `array` adalah objek.

```js
function cekApakahObjek(value) {
  return typeof value === 'object'
}

console.log( cekApakahObjek(null) ) // true
console.log( cekApakahObjek([]) ) // true
console.log( cekApakahObjek([1,2,3]) ) // true
```

Untuk mengatasinya cek jika nilai tersebut sebuah array atau bukan menggunakan `Array.isArray` dan nilai tersebut null atau bukan bersamaan dengan operator `typeof`.

```js
function cekApakahObjek(value) {
  return typeof value === 'object' && value !== null && !Array.isArray(value)
}

console.log( cekApakahObjek({}) ) // true
console.log( cekApakahObjek({ prop: 'value' }) ) // true
console.log( cekApakahObjek('string') ) // false
console.log( cekApakahObjek(13) ) // false
console.log( cekApakahObjek(false) ) // false
console.log( cekApakahObjek(null) ) // false
console.log( cekApakahObjek([]) ) // false
console.log( cekApakahObjek([1,2,3]) ) // false
```

Cara lain, gunakan method `toString` pada prototype `Object` kemudian dipanggil dengan mengirimkan nilai / variabel yang akan dicek. Jika hasilnya `[object Object]` maka nilai / variabel itu adalah objek.

```js
function cekApakahObjek(value) {
  return Object.prototype.toString.call(value) === '[object Object]'
}

console.log( cekApakahObjek({}) ) // true
console.log( cekApakahObjek({ prop: 'value' }) ) // true
console.log( cekApakahObjek('string') ) // false
console.log( cekApakahObjek(13) ) // false
console.log( cekApakahObjek(false) ) // false
console.log( cekApakahObjek(null) ) // false
console.log( cekApakahObjek([]) ) // false
console.log( cekApakahObjek([1,2,3]) ) // false
```