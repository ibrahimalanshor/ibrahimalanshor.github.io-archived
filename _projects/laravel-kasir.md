---
title: Laravel 8 Kasir
layout: post
img: laravel-kasir.png
---

![Laravel 8 Kasir]({{ site.url }}/img/laravel-kasir.png)

Aplkasi kasir sederhana dibuat dengan Laravel 8.

## Fitur

* Auth
* Dashboard
* CRUD Barang, Kategori Barang, Pengguna.
* Stok Masuk Dan Keluar
* Buat Tranksaksi dan Cetak Transaksi
* Laporan Transaksi
* Ganti Password
* Pengaturan

## Dependencies

* Laravel 8
* Sufee Admin
* Jquery
* Bootstrap

## Instalasi

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-8-kasir.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-8-kasir
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