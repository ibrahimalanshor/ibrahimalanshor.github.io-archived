---
title: Laravel Eloquent One To Many Relationship
date: 2020-09-22 19:50:00 +0700
layout: post
categories: laravel
---

Melanjutkan postingan kemarin, kali ini saya akan membahas salah satu bentuk relasi dalam Laravel Eloquent, yaitu `One To Many`.

Jika relasi `One To One` kemarin adalah relasi dimana satu data di tabel memiliki satu data di tabel lainya, relasi `One To Many` kali ini adalah relasi dimana  satu data di tabel memiliki banyak data di tabel lainya.

Contohnya, seorang user memiliki banyak foto.

Langsung saja, berikut langkah-langkah membuat relasi `One To Many`.

## Membuat Model Dan Migration

Pertama kita buat model `User` dan `Photo` beserta migrasinya.

```bash
php artisan make:model User -m
php artisan make:model Photo -m
```

Lalu, kita akan mengisi skema tabel migrasinya.

```php
Schema::create('users', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->timestamps();
});
```

```php
Schema::create('photos', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->timestamps();
    $table->foreignId('user_id')->constrained()->onDelete('cascade');
});
```

Lalu kita jalankan perintah migrasi.

```bash
php artisan migrate
```

## Membuat Relasi

Buka model `User`. Lalu buat sebuah fungsi untuk relasi ke model `Photo`.

```php
public function photos()
{
    return $this->hasMany(Photo::class);
}
```

### Inverse

Kita juga akan membuat fungsi untuk relasi terbalik di model `Photo`.

```php
public function user()
{
    return $this->belongsTo(User::class);
}
```

## Penggunaan

Untuk menggunakannya, kita tinggal mengakses properti dinamis dari fungsi yang kita buat tadi.

Contoh disini saya akan menampilkan daftar photo yang dimiliki user.

```php
$user = User::find(1);

foreach($user->photos as $photo){
    echo $photo->name;
}
```

Contoh lagi, disini saya akan menampilkan photo beserta pemiliknya.

```php
$photo = Photo::find(1);

echo $photo->user->name;
```

Silahkan dicoba.