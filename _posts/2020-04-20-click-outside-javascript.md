---
layout: 'post'
title: 'Cara Mendeteksi Click Outisde Javascript'
date: 2022-04-21 11:00:00 +0700
---

Deteksi click outside sering digunakan pada beberapa komponen seperti dropdown, modal, dll.

Contoh pada modal, ketika modal sedang ditampilkan, modal dapat ditutup dengan mengklik bagian diluar area kotak modal.

Mendeteksi click outside dapat dilakukan dengan cara menambahkan event listener klik pada `document`, jika bagian pada document yang di klik tidak ada di dalam element modal, maka klik tersebut adalah click outside.

```js
const modal = document.querySelector('.modal')

document.addEventListener('click', e => {
  if (!e.target.contains(modal)) {
    // Tutup Modal
    modal.classList.remove('open')
  }
})
```