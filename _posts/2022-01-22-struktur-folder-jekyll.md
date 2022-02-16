---
layout: "post"
title: "Struktur Folder Jekyll"
date: 2022-01-22 09:20:00 +0700
---

Jekyll adalah _static site generator_ yang dibuat dengan menggunakan bahasa pemrograman Ruby.

Jekyll memiliki struktur folder/direktori untuk memisahkan berkas-berkas berdasarkan fungsinya.

Berikut adalah struktur folder jekyll.

```
_includes
_layouts
_posts
_site
assets
_config.yml
index.html
```

Berikut penjelasanya masing-masing.

## Folder _includes

Berisi potongan-potongan bagian website yang dapat digunakan berulang-ulang pada template jekyll.

Biasanya berisi file `head.html`, `navbar.html`, `footer.html`, dsb.

## Folder _layouts

Berisi layout/tata letak dari template jekyll.

Layout digunakan mengatur tata letak setiap halaman jekyll yang diatur pada _front matter_.

Biasanya berisi file `default.html`, `post.html`, `page.html`, dsb.

## Folder _posts

Berisi kumpulan postingan yang ditampilkan.

Format file postingan, `TAHUN-BULAN-TANGGAL-JUDUL.md`.

Contoh.

* 2022-01-22-install-jekyll-ubuntu.md
* 2022-01-22-struktur-folder-jekyll.md

## Folder _site

Berisi hasil kompilasi jekyll dalam bentuk website statis.

## Folder assets

Berisi kumpulan asset statis seperti gambar, css, js, dsb.

## File _config.yml

File konfigurasi jekyll.

Disini tempat mengatur data-data yang dapat digunakan pada jekyll, seperti judul, deskripsi, plugin, dll.

## File index.html

Beranda situs atau halaman awal yang akan ditampilkan.