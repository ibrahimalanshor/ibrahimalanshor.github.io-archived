---
title: Cara Menambahkan Class Active Pada Menu Sesuai Route Laravel
date: 2020-09-17 19:28:00 +0700
categories: bootstrap, php, laravel
layout: post
---

**Class Active** digunakan untuk menandai class yang active.

Di laravel kita bisa membuat sebuah function untuk membuat class active otomatis pada menu sesuai dengan route yang sedang aktif.

Berikut langkahnya.

## Buat Sebuah Function Helper

Pertama buat sebuah function di `helper`.

Disini saya membuat sebuah function dengan nama `active`, dengan sebuah parameter `route`.

```php
function active($route){
    //
}
```

Disini saya akan memanfaatkan `helper` bawaan laravel yang berfungsi mengecek route yang sedang aktif. Yaitu `request()->is('nama-route')`.

Lalu saya akan membuat sebuah `return` yang mengembalikan nilai `true` jika parameter `route` sesuai dengan route yang aktif. Dan `false` jika sebaliknya.

```php
function active($route){
    return request()->is($route) ? 'active' : '';
}
```

### Prefix Route

Untuk memberikan prefix pada nama route, kita bisa memodifikasi nilai `route` dengan nama `prefix`-nya.

```php
function active($route){
    $route = 'admin/'.$route;
    return request()->is($route) ? 'active' : '';
}
```

### Route Bercabang

Untuk mengecek route yang bercabang, kita bisa menambahkan logika `OR` pada saat mengembalikan nilai.

```php
function active($route){
    $route = 'admin/'.$route;
    return request()->is($route) | $request()->is($route.'/*') ? 'active' : '';
}
```

## Penggunaan

Untuk menggunakanya anda hanya tinggal menaruhnya di atribut `class` pada `menu`.

```html
<li class="nav-item"><a href="" class="nav-link {% raw %}{{ active('post') }}{% endraw %}">Post</a></li>
```

Silahkan mencoba.