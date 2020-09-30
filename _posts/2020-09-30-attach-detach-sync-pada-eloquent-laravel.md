---
title: Attach, Detach, Sync Pada Eloquent Laravel
date: 2020-09-30 20:30:00 +0700
categories: laravel
layout: post
---

Laravel Eloquent menyediakan beberapa method tambahan dalam pengerjaan relasi `Many To Many`.

Method tersebut salah tiganya yang tertera pada judul.

Langsung saja kita bahas satu persatu method tambahan tersebut.

## Attach

Method ini digunakan untuk menambahkan data relasi dari dua buah tabel ke pivot tabel.

Contohnya, disini saya memiliki tabel `post` yang berelasi dengan tabel `kategori`.

Saya akan memasukan beberapa kategori ke dalam relasi post.

```php
$post = Post::findOrFail(1);

$post->kategori()->attach([1, 2, 3]);
```

## Detach

Method ini merupakan kebalikan dari method `attach`, yaitu membuang data dari relasi.

Contohnya saya akan membuang beberapa kategori dari post.

```php
$post = Post::findOrFail(1);

$post->kategori()->detach([1, 2, 3]);
```

## Sync

Method ini digunakan untuk menyeimbangkan atau memperbaharui relasi antar tabel.

Contoh saya akan memperbarui data relasi post dan kategori.

```php
$post = Post::findOrFail(1);

$post->kategori->sync([1, 4, 5]);
```

Semua id yang tidak dimasukan akan dibuang.

Sekian, silahkan dicoba.