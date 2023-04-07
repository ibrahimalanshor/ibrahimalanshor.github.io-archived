---
title: Javascript Remove Array Element By Value
date: 2023-04-07 16:30:00 +0700
images: ['/images/blogs/remove-array-element/thumbnail.jpg']
---

Untuk menghapus elemen tertentu pada array berdasarkan nilainya, ada dua cara yang dapat digunakan.

## Menggunakan Splice Method

`splice` method dapat digunakan untuk menghapus elemen pada array, dengan memasukkan index dari elemen yang akan dihapus pada argument pertama method `splice`.

Cara ini akan mengubah isi dari array yang akan dihapus elementnya. 

Untuk mendapatkan index dari elemen tertentu, anda dapat menggunakan `indexOf` atau `findIndex` method.

Contoh

```js
const arr = [1, 2, 3, 4]

// mendapatkan index dari angka 3
const deleteIndex = arr.indexOf(3)
// menghapus angka 3
arr.splice(deleteIndex, 1)

console.log(arr)
// [1, 2, 4]
```

Contoh array yang berisi objek.

```js
const arr = [
    { name: 'Amd' },
    { name: 'See' },
    { name: 'Losg' },
    { name: 'Err' }
]

// mendapatkan index dari nama 'See'
const deleteIndex = arr.findIndex(item => item.name === 'See')
// menghapus objek dengan properti nama = 'See'
arr.splice(deleteIndex, 1)

console.log(arr)
// [
//    { name: 'Amd' },
//    { name: 'Losg' },
//    { name: 'Err' }
// ]
```

## Menggunakan Filter Method

`filter` method dapat digunakan untuk menghapus elemen pada array dengan memfilter array dari elemen yang akan dihapus.

Cara ini tidak akan mengubah original array dan akan mengembalikan array yang baru.

Contoh.

```js
const arr = [1, 2, 3, 4]

// menghapus angka 3
const newArr = arr.filter(item => item !== 3)

console.log(newArr)
// [1, 2, 4]
```

Contoh array yang berisi objek.

```js
const arr = [
    { name: 'Amd' },
    { name: 'See' },
    { name: 'Losg' },
    { name: 'Err' }
]

// menghapus objek dengan properti nama = 'See'
const newArr = arr.filter(item => item.name !== 'See')

console.log(newArr)
// [
//    { name: 'Amd' },
//    { name: 'Losg' },
//    { name: 'Err' }
// ]
```