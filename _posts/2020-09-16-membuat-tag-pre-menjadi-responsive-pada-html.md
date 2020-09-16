---
title: Membuat Tag Pre Menjadi Responsive Pada HTML
layout: post
date: 2020-09-16 10:46:00 +0700
categories: laravel
---

**Tag Pre**  adalah tag HTML yang digunakan untuk membuat sebuah teks *pre-formatting*. Atau teks tanpa pemformatan.

Artinya text didalam tag `pre` tidak mengalami pemformatan.

Tag `pre` biasanya digunakan untuk menampilkan puisi, code, syntax, dll.

Namun, ada beberapa masalah dalam penggunaan tag `pre`, yaitu masalah `responsivitas`.

Biasanya isi dari tag `pre` tidak menurun jika teks tersebut belum berganti baris, walaupun teks tersebut sudah keluar dari bingkai layar.

Contoh.

![Pre Tidak Responsive]({{ site.url }}/img/pre-responsive.png)

Bisa dilihat code `pre` tersebut lari keluar bingkai layar.

Nah, untuk memperbaikinya kita perlu memberikan style css pada tag `pre` tersebut.

```css
pre{
    white-space: pre-wrap;
}
```

Simpan, dan silahkan dicoba.