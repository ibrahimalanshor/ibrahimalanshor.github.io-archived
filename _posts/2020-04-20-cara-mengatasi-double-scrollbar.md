---
layout: 'post'
title: 'Cara Mengatasi Double Scrollbar'
date: 2022-04-21 11:30:00 +0700
---

Secara default ketika konten di dalam `body` panjangnya lebih dari 100% maka akan muncul scrollbar horizontal atau vertikal.

Masalah muncul ketika membuat elemen lain yang ukuran tinggi atau lebarnya sama dengan body, kemudian di dalam elemen tersebut muncul scrollbar yang mengakibatkan scrollbar menjadi double milik `body` dan elemen tersebut.

Untuk mengatasinya dapat dengan cara menyembunyikan scrollbar pada body.

```css
body.no-scroll {
  overflow: hidden
}
```

Contoh penggunaanya pada saat menampilkan modal.

```js
modalToggle.addEventListener('click', () => {
  document.body.classList.add('no-scroll')
  
  modal.classList.add('open')
})

modalClose.addEventListener('click', () => {
  document.body.classList.remove('no-scroll')
  
  modal.classList.remove('open')
})
```