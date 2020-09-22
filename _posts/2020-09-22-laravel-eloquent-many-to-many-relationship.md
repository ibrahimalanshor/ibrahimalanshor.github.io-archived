---
title: Laravel Eloquent Many To Many Relationship
date: 2020-09-22 20:00:00 +0700
layout: post
categories: laravel
---

Melanjutkan seri macam-macam relasi Eloquent Laravel kemarin, disini saya akan membahas bentuk relasi `Many To Many`.

Relasi ini cukup rumit, karena kita harus membuat sebuah tabel lagi sebagai `Pivot` table yang menghubungkan kedua tabel.

Relasi ini berarti sebuah data di tabel memiliki banyak data di tabel lainya, begitu juga sebaliknya.

Contohnya seorang user memiliki banyak role, begitu juga sebaliknya sebuah role memiliki banyak user.

Langsung saja berikut implementasinya.

## Membuat Model Dan Migration

Seperti biasa, kita akan membuat model `User`, `Role`, dan `RoleUser` beserta migrasinya.

Model `RoleUser` disini digunakan sebagai `pivot table`.

```bash
php artisan make:model User -m
php artisan make:model Role -m
php artisan make:model RoleUser
```

Lalu kita lanjut dengan mengatur skema tabelnya.

```php
Schema::create('users', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->timestamps();
});
```

```php
Schema::create('roles', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->timestamps();
});
```

```php
Schema::create('role_user', function (Blueprint $table) {
    $table->id();
    $table->bigInteger('user_id')->unsigned();
    $table->bigInteger('role_id')->unsigned();
    $table->timestamps();
});
```

## Membuat Relasi

Buka model `User`, dan buat sebuah fungsi untuk relasi ke model `Role`.

```php
public function roles()
{
    return $this->belongsToMany(Role::class);
}
```

Lanjut, buka model `Role` dan buat fungsi untuk relasi ke model `User`.

```php
public function users()
{
    return $this->belongsToMany(User::class);
}
```

## Penggunaan

Untuk menggunakanya, seperti biasa kita tinggal mengakses properti dinamik dari fungsi yang kita sudah buat.

Contoh saya akan menampilkan role yang dimiliki user.

```php
$user = User::find(1);

foreach($user->roles as $role){
    echo $role->name;
}
```

Contoh lagi saya akan menampilkan user apa saja yang menggunakan role ini.

```php
$role = Role::find(1);

foreach($role->users as $user){
    echo $user->name;
}
```

Silahkan mencoba.