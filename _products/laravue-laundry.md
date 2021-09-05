---
title: Laravel Vue Laundry
layout: post
img: laravue-laundry.png
date: 2021-07-22
---

Aplikasi Laundry dengan Laravel 8 dan Vue JS, sudah selesai namun masih banyak bug dan fitur yang perlu dibuat, males

## Fitur

* Admin
    * Auth
    * Dashboard
    * Master Pengguna
    * Edit Profil
    * Pengaturan
* Petugas
    * Auth
    * Dashboard
    * Master Paket, Pelanggan, Transaksi 
    * Transaksi Baru, Detail Transaksi
    * Edit Profil

## Dependencies

* Laravel 8
* Vue JS
* Buefy

## Instalasi

Pertama clone repo ini.

```bash
git clone https://github.com/ibrahimalanshor/laravue-laundry.git
```

Masuk ke folder hasil clone.

```bash
cd laravue-laundry
```

Salin `env.example` ke `env`. Sesuaikan konfigurasi database anda.

Pasang *dependencies*.

```bash
composer install
npm install && npm run dev
```

Generate app key.

```bash
php artisan key:generate
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