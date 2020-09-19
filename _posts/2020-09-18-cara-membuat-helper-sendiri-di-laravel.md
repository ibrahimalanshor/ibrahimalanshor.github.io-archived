---
title: Cara Membuat Helper Sendiri Di Laravel
layout: post
date: 2020-09-18 19:25:00 +0700
categories: laravel
---

**Helper** adalah kumpulan fungsi-fungsi yang dibuat untuk memudahkan proses *programming*.

Laravel sendiri sudah menyediakan berbagai macam **helper**, seperti `route()`, `redirect`, dll.

Tapi terkadang kita juga membutuhkan helper-helper tertentu yang belum disediakan Laravel.

Seperti helper untuk membuat class otomatis pada menu ketika menu tersebut diakses, dll.

Untuk itu mari kita belajar cara membuat **Helper** sendiri. 

## Buat File helpers.php

Petama buat sebuah folder dengan nama `Helper` di app.

Lalu buat sebuah file dengan nama `helpers.php` di folder tersebut.

File ini berguna untuk menampung semua helper buatan kita.

## Menambahkan Fungsi

Tambahkan fungsi helper yang akan kalian gunakan di file `helpers.php`.

Contoh disini saya membuat sebuah fungsi untuk mengkonversi tanggal.

```php
function tanggal($tanggal){
    return date('d-m-Y', strtotime($tanggal));
}
```

## Konfigurasi Composer

Setelah fungsi dibuat, saatnya kita menambahkan file helper yang kita buat ke `autoload composer`.

Buka file `composer.json`, lalu tambahkan kode berikut di bagian `autoload`.

```json
"autoload": {
        "psr-4": {
            ...
        },
        "files": [
            "app/Helpers/helpers.php"
        ]
    },
```

## Jalankan dump-autoload

Langkah terakhir, jalankan perintah berikut di terminal.

```bash
composer dump-autoload
```

## Penggunaan

Untuk penggunaanya seperti helper bawaan Laravel.

Contoh, disini saya menggunakan helper yang saya buat di `blade`.

```php
{% raw %}{{ tanggal(2020-09-18) }}{% endraw %}
```

Maka hasilnya

```
18-09-2020
```

Silahkan mencoba. 