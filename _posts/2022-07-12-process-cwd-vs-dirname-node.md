---
layout: post
title: "process.cwd vs __dirname Node JS"
tags: [javascript, node]
date: 2022-07-12 20:20:00 +0700
---

Keduanya memiliki fungsi yang mirip,

- `process.cwd()` mengembalikan working directory proses node berjalan
- `__dirname` mengembalikan nama directory dari modul/file yang sedang digunakan


Contoh sebuah file `/home/user/Documents/index.js`

```js
console.log(process.cwd())
console.log(__dirname)
```

Jika saya menjalankan file tersebut di `/home/user/Documents/`, akan menampilkan:

```bash
> node index.js
/home/user/Documents
/home/user/Documents
```

Jika saya menjalankan file tersebut di `/home/`, akan menampilkan:

```bash
> node user/Documents/index.js
/home
/home/user/Documents
```