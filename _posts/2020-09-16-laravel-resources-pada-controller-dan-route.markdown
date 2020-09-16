---
layout: post
title:  "Laravel Resources Pada Controller Dan Route"
date:   2020-09-16 07:58:16 +0700
categories: laravel php
---

**Laravel Resources** adalah fitur untuk memudahkan membuat sebuah skema *CRUD* sederhana pada aplikasi Laravel.

Dengan fitur ini, kita dapat membuat sebuah CRUD sederhana dengan cepat, hanya dengan beberapa langkah.

Berikut langkah-langkahnya.

## Membuat Controllers

Pertama buka *terminal*, lalu jalankan sebuah perintah untuk membuat controller seperti biasa. Lalu tambahkan *flag* `-r`.

Contoh.

```bash
php artisan make:controller HomeController -r
```

Flag `-r` disini berarti **resources**. Yang berarti controller yang kita buat sudah memiliki resources untuk crud sederhana.

Coba cek controller yang baru saja dibuat. Maka akan ada 6 method yang sudah dibuat lengkap dengan parameter dan penjelasanya.

Tugas kita hanya perlu membuat logika programnya.  

## Membuat Route

Setelah membuat controller, kita akan membuat route yang menuju ke controller yang baru saja kita buat.

Laravel sudah menyediakan sebuah method untuk memudahkanya yaitu **resources**.

Caranya seperti biasa, kita membuat route dengan method resources.

Contoh.

```php
Route::resources('/home', HomeController::class);
```

`/home` adalah alamat url routenya.

`HomeController::class` adalah class controllernya.

Simpan lalu kita coba cek list route pada aplikasi Laravel kita.

Caranya dengan menjalankan perintah artisan berikut di terminal.

```bash
php artisan route:list
```

Maka akan muncul route-route yang berhubungan dengan controller yang tadi dibuat.

## Parameter Tambahan

Kita dapat menambahkan beberapa parameter tambahan untuk membantu atau memperjelas route kita.

Parameter tersebut sudah disediakan laravel. Berikut daftarnya.

### Only

Parameter ini digunakan untuk membatasi method yang digunakan pada controller.

Contohnya ketika kita hanya ingin menggunakan method `create` dan method `store`. Maka kita dapat menggunakan parameter ini.

Contoh

```php
Route::resource('/home', HomeController::class, ['only' => ['create', 'store']]);
```

### Except

Parameter ini digunakan untuk mengecualikan method yang digunakan pada controller.

Contohnya ketika kita tidak ingin menggunakan method `destroy`.

```php
Route::resource('/home', HomeController::class, ['except' => ['destroy']]);
```

## Penutup

Oke sekian penjelasan mengenai **Laravel Resources**.

Semoga Bermanfaat.