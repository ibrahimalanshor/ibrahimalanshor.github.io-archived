---
title: Mengetengahkan Image Pada HTML
layout: post
date: 2020-09-16 11:00
categories: html
---

Secara *default*, gambar di HTML akan berada disebelah kanan.

Untuk mengetengahkannya kita perlu menggunakan `css`.

Berikut codenya.

```css
img{
    display: block;
    margin: 0 auto;
}
```

Atribut `display: block` mengatur `img` agar bisa diberikan atribut `margin`.

Atribut `margin: 0 auto` mengatur agar `img` berada di tengah.

Silahkan dicoba.