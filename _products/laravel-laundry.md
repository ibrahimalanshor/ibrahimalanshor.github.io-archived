---
title: Laravel 8 Laundry
layout: post
img: laravel-laundry.png
date: 2021-01-11
---

Laundry dibuat dengan Laravel 8.

## Fitur

* Admin
	* Auth
	* Pengaturan
	* CRUD Petugas
	* Semua
* Petugas
	* Auth
	* Dashboard
	* CRUD Pelangga, Paket
	* Transaksi

## Dependencies

* Laravel 8
* Bootstrap 4
* Jquery
* Select2
* SB Admin 2

## Instalation

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-laundry.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-laundry
```

Salin `env.example` ke `env`. Sesuaikan konfigurasi database anda.

Pasang *dependencies*.

```bash
composer install
```

Pasang NPM.

```bash
npm install && npm run dev
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