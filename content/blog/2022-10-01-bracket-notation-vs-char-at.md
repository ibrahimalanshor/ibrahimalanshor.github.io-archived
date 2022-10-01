---
layout: post
title: "String Bracket Notation [] vs String Char At Javascript"
tags: [js]
date: 2022-10-01 20:00:00 +0700
---

Ada 2 cara untuk mengakses karakter pada string berdasarkan index-nya pada javascript:

- Bracket Notation, `string[index]`
- CharAt Method, `string.charAt[index]`

Contoh penggunaan.

```js
const str = 'today is sunday'

console.log( str[2] ) // d
console.log( str.charAt(2) ) // d
````

Berikut perbedaan kedua cara tersebut.

## 1. Dukungan Browser

`charAt` method adalah standar original dan dapat bekerja di semua browser, sedangkan __Bracket Notation__ baru didukung di ES 5 dan beberapa browser seperti IE 7 di bawahnya tidak mendukungnya.

## 2. charAt Mengkonversi Argumen Ke Integer

__Bracket Notation__ mengembalikan karakter di index yang ditentukan pada string, jika index tersebut tidak ada dikembalikan `undefined`.

```js
const str = 'today is sunday'

console.log( str[2] ) // d 
console.log( str[10] ) // u
console.log( str[2.23] ) // undefined
console.log( str[100] ) // undefined
console.log( str[null] ) // undefined 
console.log( str[undefined] ) // undefined 
console.log( str['index'] ) // undefined 
console.log( str[NaN] ) // undefined 
console.log( str[{}] ) // undefined 
console.log( str[Math] ) // undefined 
console.log( str[true] ) // undefined 
```

Sedangkan `charAt` method mengkonversi argumen yang dikirimkan ke integer, kemudian dikembalikan karakter pada string yang index-nya sesuai dengan hasil konversi argumen tersebut, jika tidak ditemukan dikembalikan string kosong `""`.

```js
const str = 'today is sunday'

console.log( str.charAt(2) ) // d 
console.log( str.charAt(10) ) // u
console.log( str.charAt(2.23) ) // d
console.log( str.charAt(100) ) // ""
console.log( str.charAt(null) ) // t 
console.log( str.charAt(undefined) ) // t 
console.log( str.charAt('index') ) // t 
console.log( str.charAt(NaN) ) // t 
console.log( str.charAt({}) ) // t 
console.log( str.charAt(true) ) // o 
```

Karena `null`, `undefined`, `index`, dst adalah `NaN` maka ketika dikonversi ke integer menjadi `0` dan `true` menjadi `1`.