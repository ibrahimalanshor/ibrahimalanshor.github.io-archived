---
layout: post
title: "Cara Mengambil Ekstensi dari String Node JS"
tags: [node]
date: 2022-07-12 20:00:00 +0700
---

Untuk mengambil ekstensi dari sebuah string pada node js, gunakan method `extname` dari modul `path`.

Method ini akan mengembalikan ekstensi terakhir beserta `.` dari sebuah string, jika argumen bukan string akan melempar error, jika tidak ada ekstensi akan mengembalikan string kosong.

```js
const path = require('path')

const png = path.extname('image.png') // .png
const js = path.extname('script.js') // .js
const html = path.extname('index.html') // .html
const css = path.extname('style.min.css') // .css
const empty = path.extname('index') // ''
const error = path.extname(12) // throw ERR_INVALID_ARG_TYPE
```