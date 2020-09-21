---
title: Laravel Eloquent One To One Relationship
date: 2020-09-21 19:30:00 +0700
categories: laravel
layout: post
---

Dalam pembuatan skema database terkadang diperlukan relasi antar tabel. Contohnya sebuah tabel `posts` memiliki banyak hubungan dengan tabel `comments`. 

`Eloquent` sudah menyediakan berbagai macam metode untuk menangani dan memudahkan proses pembuatan relasi antar tabel tersebut.

Dan kali ini saya akan membahas salah satunya, yaitu `One To One`.

Relasi `One To One` adalah relasi sederhana. Relasi ini menghubungkan antara satu tabel dengan tabel lainya.

Maksudnya 1 data dari tabel akan memiliki relasi dengan 1 data di tabel lainnya.

Contoh seorang user memiliki satu nomer telepon, begitu juga sebaliknya.

Langsung saja berikut langkah-langkah membuatnya.

## Membuat Model dan Migration

Langkah pertama, kita akan membuat model dan migrasi database-nya dulu.

Disini aya akan membuat dua buah tabel, tabel `users` dan tabel `phones` beserta migrasinya.

```bash
php artisan make:model User -m
php artisan make:model Phone -m
```

Buka file user migration-nya, lalu buat skema tabelnya.

```php
Schema::create('users', function (Blueprint $table) {
    $table->id();
    $table->string('name');
});
```

```php
Schema::create('phones', function (Blueprint $table) {
    $table->id();
    $table->string('no');
    $table->foreignId('user_id')->constrained()->onDelete('cascade');
});
```

Lalu kita jalankan migration-nya.

```bash
php artisan migrate
```

## Membuat Relasi

Buka model `User`, lalu buat sebuah function untuk relasi ke model `Phone`.

```php
public function phone()
{
    return $this->hasOne(Phone::class);
}
```

Buka model `Phone`, lalu kita lakukan kebalikanya.

```php
public function user()
{
    return $this->hasOne(User::class);
}
```

## Penggunaan

Untuk menggunakanya kita tinggal memanggil fungsi yang sudah kita buat di model tadi.

Contoh.

```php
$userPhone = User::find(1)->phone
```

Begitu juga sebaliknya

```php
$phoneUser = Phone::find(1)->user
```

Silahkan dicoba.

