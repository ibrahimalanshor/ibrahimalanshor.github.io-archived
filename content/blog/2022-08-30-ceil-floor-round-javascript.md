---
layout: post
title: "Ceil Vs Floor Vs Round Pada Javascript"
tags: [javascript]
date: 2022-08-30 20:45:00 +0700
---

`Math` adalah objek bawaan javascript yang memiliki properti dan metode untuk kebutuhan perhitungan matematika.

Terdapat 3 metod statis pada objek `Math` yaitu `ceil`, `floor`, dan `round`, yang memiliki fungsi yang sama yaitu membulatkan suatu angka tapi dengan hasil yang berbeda.

Berikut contohnya.

```js
console.log( Math.ceil(4.2) ) // 5
console.log( Math.floor(4.9) ) // 4
console.log( Math.round(4.4) ) // 4
console.log( Math.round(4.6) ) // 5
console.log( Math.round(4.5) ) // 5
```

## Math.ceil

`Math.ceil` akan membulatkan angka ke atas atau ke angka terdekat yang lebih besar dari angka itu sendiri.

```js
console.log( Math.ceil(4.5) ) // 5
console.log( Math.ceil(1.5) ) // 2
console.log( Math.ceil(1.1) ) // 2
console.log( Math.ceil(1.1111) ) // 2
console.log( Math.ceil(0.000001) ) // 1
console.log( Math.ceil(-1) ) // -1
console.log( Math.ceil(-2.5) ) // -2
console.log( Math.ceil(-3.9999) ) // -3
```

## Math.floor

`Math.floor` akan membulatkan angka ke bawah atau ke angka terdekat yang lebih kecil dari angka itu sendiri.

```js
console.log( Math.floor(4.5) ) // 4
console.log( Math.floor(1.5) ) // 1
console.log( Math.floor(1.9) ) // 1
console.log( Math.floor(1.9999) ) // 1
console.log( Math.floor(0.99999) ) // 0
console.log( Math.floor(-1) ) // -1
console.log( Math.floor(-2.5) ) // -3
console.log( Math.floor(-3.9999) ) // -4
```

## Math.round

`Math.round` akan membulatkan angka ke angka terdekat, jika angka setelah koma lebih dari `0.5` maka akan dibulatkan ke atas, jika kurang akan dibulatkan ke bawah.

```js
console.log( Math.round(4.5) ) // 5
console.log( Math.round(4.49) ) // 4
console.log( Math.round(1.1) ) // 1
console.log( Math.round(1.9999) ) // 2
console.log( Math.round(0.99999) ) // 1
console.log( Math.round(-1) ) // -1
console.log( Math.round(-2.5) ) // -2
console.log( Math.round(-3.0999) ) // -3
```