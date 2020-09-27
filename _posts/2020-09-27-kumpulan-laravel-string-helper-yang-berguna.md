---
title: Kumpulan Laravel String Helper Yang Berguna
layout: post
date: 2020-09-27 20:00:00 +0700
categories: laravel
---

Salah satu fitur unggulan laravel yang memudahkan proses programming adalah `Helper`.

Sesuai namanya `Helper` adalah pembantu proses programming, helper berisi kumpulan fungsi yang biasanya digunakan dalam programming.

Laravel Sendiri memiliki puluhan `Helper` siap pakai.

Karena jumlahnya yang banyak, tidak jarang saya menjadi malas atau kesulitan saat mencari helper yang saya ingin gunakan. Atau terkadang menjadi tidak tahu kalau ada helper yang berguna diantara tumpukan helper tersebut.

Maka dari itu saya sudah mengumpulkan helper-helper yang sekiranya lebih berguna dibandingkan helper lainya.

## Str::random

Fungsi helper ini untuk menghasilkan sebuah string acak dengan jumlah yang ditentukan.

Saya biasanya menggunakan helper ini untuk membuat kode unik, token, dll.

Contoh penggunaan.

```php
use Illuminate\Support\Str;

$token = Str::random(6);
// KN8ASN
```

## Str::slug

Fungsi helper ini untuk menghasilkan sebuah "URL Friendly" dari sebuah string.

Saya biasanya menggunakan helper ini untuk membuat slug pada postingan.

Contoh penggunaan.

```php
use Illuminate\Support\Str;

$slug = Str::slug('Saya Suka Omong Kosong', '-');
// saya-suka-omong-kosong
```

