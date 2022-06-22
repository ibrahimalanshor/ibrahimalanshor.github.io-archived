---
layout: post
title: "Substring vs Substr vs Slice di Javascript"
tags: [javascript]
date: 2022-06-22 20:00:00 +0700
---

Ketiga method `substring`, `substr`, dan `slice` dapat digunakan untuk mengambil atau memotong sebagian string.

## Substring

Substring membutuhkan 2 parameter, `index awal` dan `index akhir`, mengembalikan bagian dari string dimulai dari `index awal` sampai dengan sebelum `index akhir`.

```js
const str = 'Today is wednesday'

console.log(str.substring(6, 8)) // is
```

Jika `index akhir` tidak ditambahkan, akan mengembalikan string dari `index awal` sampai akhir string.

```js
const str = 'Today is wednesday'

console.log(str.substring(6)) // is wednesday
```

Jika nilai `index awal` atau `index akhir` negatif, keduanya akan diubah menjadi `0`.

Jika nilai `index akhir` lebih besar dari `index akhir`, posisi keduanya akan ditukar.

```js
const str = 'Today is wednesday'

console.log(str.substring(5, -6)) // Today
```

## Substr

Substr membutuhkan 2 parameter, `index awal` dan `jumlah karakter yang akan diambil`, mengembalikan bagian dari string dimulai dari `index awal` sampai dengan `jumlah karakter yang akan diambil`.

```js
const str = 'Today is wednesday'

console.log(str.substr(6, 2)) // is
```

Jika nilai `index awal` negatif, `index awal` akan dihitung dari belakang atau akhir string.

```js
const str = 'Today is wednesday'

console.log(str.substr(-12, 2)) // is
```

> Method `substr` sudah tidak direkomendasikan oleh [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr) karena sudah deprecated.

## Slice

Sama seperti `substring`, method `slice` menerima dua parameter `index awal` dan `index akhir`, dengan tambahan `slice` mendukung nilai negatif dari `index awal` dan `index akhir`.

Sama seperti `substr`, jika nilai `index awal` ataun `index akhir` negatif, perhitungan akan dimulai dari belakang atau akhir string.

```js
const str = 'Today is wednesday'

console.log(str.slice(6, 8)) // is
console.log(str.slice(-12, 8)) // is
console.log(str.slice(-12, -10)) // is
console.log(str.slice(6)) // is wednesday
```