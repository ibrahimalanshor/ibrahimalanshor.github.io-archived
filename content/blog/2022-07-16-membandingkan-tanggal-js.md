---
layout: post
title: "Membandingkan Tanggal di Javascript"
tags: [javascript]
date: 2022-07-16 20:30:00 +0700
---

Untuk membandingkan dua tanggal di javascript, anda dapat langsung membandingkan dua objek tersebut dengan operator `>`, `<`, `<=`, `>=`.

```js
const date1 = new Date('2022-07-15')
const date2 = new Date('2022-07-20')

console.log(date1 > date2) // false
console.log(date1 < date2) // true
console.log(date1 >= date2) // false
console.log(date1 <= date2) // true
```

Jika ingin membandingkan dengan operator `==`, `!=` `===`, `!==`, gunakan nilai milisekon dari kedua tanggalnya baru dibandingkan dengan operasi tersebut.

Untuk mendapatkan nilai milisekon dari objek tanggal gunakan method `getTime`.

```js
const date1 = new Date('2022-07-15')
const date2 = new Date('2022-07-15')

console.log(date1 === date2) // false (tidak tepat)
console.log(date1.getTime() === date2.getTime()) // true
```