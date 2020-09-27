---
title: Cara Menambahkan Element Baru Pada Request Laravel
layout: post
date: 2020-09-27 20:30:00 +0700
categories: laravel
---

Dalam sebuah pemrosesan sebuah request terkadang kita ingin menambahkan elemen baru pada request tersebut.

Contohnya sebuah kita ingin menambahkan elemen `user_id` pada pemrosesan request `post`.

Untuk menambahkanya kita bisa menggunakan salah satu *method* di *collections* laravel, yaitu **merge**.

Disini saya memiliki sebuah `$request` yang berisi data-data dari form request.

```php
$request->all();

/*
    'post' => 'Saya Suka Ancaman',
    'category' => 'blog'
*/
```

 Lalu saya tambahkan elemen `user_id` yang sudah saya masukan di array `$data`.

```php
$data = [
    'user_id' => 2
];

$request->merge($data);
```

Dan saya tambahkan dengan menggunakan method `merge`.

```php
$request->all();

/*
    'post' => 'Saya Suka Ancaman',
    'category' => 'blog',
    'user_id' => 2
*/
```

Silahkan dicoba.