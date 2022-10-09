---
layout: post
title: "Cara Parse Command Line Argument Node"
tags: [node]
date: 2022-10-09 20:00:00 +0700
---

Command Line Argumen adalah semua yang dikirimkan ketika menjalankan sebuah program pada shell setelah nama program.

Pada node semua argumen yang pada shell akan ditampung di objek global `process` pada properti `argv` dalam bentuk array.

Contoh file `argv.js`:

```js
console.log(process.argv)
```

Kemudian jalankan file tersebut dengan mengirimkan beberapa argumen.

```bash
node argv.js satu dua tiga empat
[
  '/usr/local/bin/node',
  '/home/ibrahimalanshor/test/argv.js',
  'satu',
  'dua',
  'tiga',
  'empat'
]
```

Dapat diperhatikan dua elemen pertama argumen adalah `node` dan path dari program dijalankan, untuk mengambil hanya argumen setelah nama program, gunakan `slice` method pada array argumen.

Ubah file `argv.js`:

```js
console.log(process.argv.slice(2))
```

Coba jalankan lagi.

```bash
node argv.js satu dua tiga empat
[ 'satu', 'dua', 'tiga', 'empat' ]
```