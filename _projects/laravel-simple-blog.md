---
title: Laravel 8 Simple Blog
layout: post
img: laravel-simple-blog.png
---

![Laravel 8 Simple Blog]({{ site.url }}/img/laravel-simple-blog.png)

Simple Blog dibuat dengan Laravel 8.

## Fitur

* Admin
	* Auth
	* Dashboard
	* CRUD Post, Category, Comment, Files, User
	* Site Setting
* User
	* Auth
	* Dashboard
	* CRUD Post, Category, Comment, Files
	* Profile
* Guest
	* Home
	* Category
	* Post
	* Comment

## Dependencies

* Laravel 8
* Bootstrap 4
* Jquery
* CKEditor
* Select2

## Instalation

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravel-8-simple-blog.git
```

Masuk ke folder hasil clone.

```bash
cd laravel-8-simple-blog
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