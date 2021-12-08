---
layout: post
title: "Perbedaan Logical OR dan Nullish Coalescing Operator Pada Javascript"
---

Nullish Coalescing merupakan salah satu operator baru pada Javascript yang fungsinya mirip dengan Logical OR, yaitu mengembalikan nilai yang di kanan jika nilai yang di kiri berada pada kondisi tertentu.

Sebelum itu mari kita simak pengertian keduanya terlebih dahulu.

## Logical OR (||)

Logical OR pada javascript adalah operasi logika yang mengembalikan nilai yang di kanan jka nilai yang dikiri bernilai `false`, `0` atau `''`.

Contoh.

```javascript
const nyawa = -10
const hidup = nyawa > 1
const status = hidup || 'Mati'

console.log(status)
// Mati

const nilai = 0
const hasil = nilai || 10

console.log(hasil)
// 10

const nama = ''
const username = nama || 'Anonymous'

console.log(username)
// Anonymous
```

## Nullish Coalescing Operator (??)

Nullish Coalescing Operator pada javascript adalah operasi logika yang mengembalikan nilai yang di kanan jka nilai yang dikiri bernilai `null` atau `undefined`.

Contoh.

```javascript
const nyawa = -10
const hidup = nyawa > 1
const status = hidup ?? 'Mati'

console.log(status)
// false

const nilai = 0
const hasil = nilai ?? 10

console.log(hasil)
// 0

const nama = ''
const username = nama ?? 'Anonymous'

console.log(username)
// ''
```

## Perbedaan Logical OR dan Nullish Coalescing Operator

Perbedaanya terletak pada kondisi yang harus dipenuhi agar nilai yang kanan dikembalikan.

Logical OR mengembalikan nilai yang di kanan jika nilai yang di kiri bernilai `false`, `0`, atau `''`.

Sedangkan Nullish Coalescing Operator mengembalikan nilai yang di kanan jika nilai yang di kiri bernilai `undefined`, atau `null`.