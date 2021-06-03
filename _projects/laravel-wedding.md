---
title: Wedding
layout: post
img: wedding.png
---

![Wedding]({{ site.url }}/img/wedding.png)

Aplikasi undangan pernikahan berbasis web, dibuat dengan Laravel 8, Bootstrap, dan SB Admin.

Fitur sudah selesai, namun masih banyak serangga males mgodonf. 

## Fitur

* Admin
	* Auth
	* Dashboard
	* Edit Tema
	* Edit Menu
	* Edit Data Pernikahan dan Pasangan
	* Manajemen RSVP
* Guest
	* Banner
	* Tentang Pasangan
	* Cerita Pasangan
	* Gallery
	* Lokasi
	* Konfirmasi Kehadiran

## Dependencies

* Laravel 8
* Sbadmin
* Bootstrap
* Jquery

## Instalasi

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-wedding.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-wedding
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