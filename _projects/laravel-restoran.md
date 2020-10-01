---
title: Laravel 8 Restoran
layout: post
---

![Laravel 8 Restoran]({{ site.url }}/img/laravel-restoran.png)

Aplkasi restoran sederhana dibuat dengan Laravel 8.

## Fitur

* Admin
	* Auth
	* Dashboard
	* CRUD Menu, Meja, Kategori, User
	* Site Setting
* User
	* Auth
	* Dashboard
	* Membuat, menghapus, membayar, mencetak pesanan.
	* Melihat meja
	* Profile

## Dependencies

* Laravel 8
* Concept Master
* Jquery
* Bootstrap

## Instalation

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-8-restoran.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-8-restoran
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