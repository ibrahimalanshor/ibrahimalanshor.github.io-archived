---
layout: post
title: addEventListener VS on Events Javascript
date: 2020-11-17 20:23:00 +0700
categories: javascript
---

Event adalah peristiwa yang terjadi pada element HTML.

Untuk menangani event pada javascript, kita dapat menggunakan dua cara yaitu __addEventListener__ dan __on__.

Keduanya ini memiliki fungsi yang sama yaitu menangani event pada javascript.

Contoh penggunaan.

## on

```js
const button = document.querySelector('button')
button.onclick = () => alert('On And On')
```
## addEventListener

```js
const button = document.querySelector('button')
button.addEventListener('click', () => alert('ada apa dengan algoritma'))
```

Mungkin kalian terbiasa menggunakan __on__ karena lebih singkat.

Padahal keduanya memiliki perbedaan dan fungsi yang lebih spesifik.

## addEventListener vs On

Perhatikan kode berikut

```js
const button1 = document.querySelector('#button1')
const button2 = document.querySelector('#button2')

const handler1 = () => alert('handler1')
const handler2 = () => alert('handler2')

button1.onclick = handler1
button1.onclick = handler2

button2.addEventListener('click', handler1)
button2.addEventListener('click', handler2)
```

Ketika `button1` di-klik maka akan muncul satu alert. Sedangkan ketika `button2` muncul dua alert.

Padahal di `button1` terdapat dua *handler*, tetapi kenapa hanya satu yang berjalan.

Dari sini kita dapat jawaban perbedaan kedua fungsi ini, yaitu __addEventListener__ dapat menagani banyak *event* dalam satu elemen, sedangkan __on__ tidak.