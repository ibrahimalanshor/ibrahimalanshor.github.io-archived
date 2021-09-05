---
title: Laravel 8 Inventaris
layout: post
img: laravel-inventaris.png
date: 2020-12-01
---

Aplkasi inventaris sederhana dibuat dengan Laravel 8.

## Fitur

* Auth
* Dashboard
* CRUD Barang, Kategori Barang, Pengguna.
* CRUD Suplier, Cetak PDF.
* Barang Masuk dan Keluar
* Peminjaman, Cetak PDF Peminjaman
* Laporan, Cetak PDF Laporan
* Ganti Password
* Pengaturan

## Dependencies

* Laravel 8
* Cool Admin
* Jquery
* Bootstrap

## Instalasi

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-inventaris.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-inventaris
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