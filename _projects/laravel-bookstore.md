---
title: Bookstore
layout: post
img: bookstore.png
---

![Bookstore]({{ site.url }}/img/bookstore.png)

Aplikasi toko buku berbasis web, dibuat dengan Laravel 8, Tailwind, dan AdminLTE.

Fitur sudah selesai, namun masih banyak serangga males mgodonf. 

## Fitur

* Admin
	* Auth
	* Dashboard
	* Master Buku, Kategori, Supplier, User
	* History Stok, Stock In, Stock Out
	* Transaksi
	* Setting
* Guest
	* View Book
* User
	* Auth
	* Add To Cart
	* Make Transaction

## Dependencies

* Laravel 8
* Admin LTE
* Bootstrap
* Jquery
* Tailwind

## UI Design

Ngambil di dribble

https://dribbble.com/shots/6847102-Book-Store

## Instalasi

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-bookstore.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-bookstore
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