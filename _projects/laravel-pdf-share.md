---
title: PDF Share
layout: post
img: pdf-share.png
---

![PDF Share]({{ site.url }}/img/pdf-share.png)

Share your pdf

## Fitur

* Admin
	* Auth
	* Dashboard
	* Melihat dan menghapus PDF
	* Melihat dan menghapus pengguna
	* Pengaturan
* User
	* Auth
	* Dashboard
	* CRUD PDF
	* Edit Profile
* Guest
	* Melihat dan mendownload PDF
	* Melihar profil pengguna

## Dependencies

* Laravel 8
* AdminLTE
* Bootstrap
* Jquery

## Instalasi

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-pdf-share.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-pdf-share
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