---
title: Laravel 8 Perpustakaan
layout: post
img: laravel-perpustakaan.png
---

![Laravel 8 Perpustakaan]({{ site.url }}/img/laravel-perpustakaan.png)

Aplkasi perpustakaan sederhana dibuat dengan Laravel 8.

## Fitur

* Auth
* Dashboard
* CRUD Buku, Kategori, Member.
* Tambah dan kurangi stok buku.
* Peminjaman
* Pengaturan
* Profile

## Dependencies

* Laravel 8
* SB Admin 2
* Jquery
* Bootstrap

## Instalation

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-8-perpustakaan.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-8-perpustakaan
```

Salin `env.example` ke `env`. Sesuaikan konfigurasi database anda.

Pasang *dependencies*.

```bash
composer install
```

Generate app key.

```bash
php artisan key:Generate
```

Hubungkan storage ke public.

```bash
php artisan storage:link
```

Migrasi dan seed database.

```bash
php artisan migrate --seed
```

Run app and enjoy.

```
php artisan serve
```