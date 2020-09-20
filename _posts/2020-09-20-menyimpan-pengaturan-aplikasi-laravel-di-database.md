---
title: Menyimpan Pengaturan Aplikasi Laravel Di Database
layout: post
categories: laravel
date: 2020-09-20 16:40:00 +0700
---

Terkadang dalam sebuah sistem aplikasi Laravel kita membutuhkan sebuah fitur bernama pengaturan.

Fitur yang menampung data-data mengenai sistem tersebut.

Seperti nama aplikasi, deskripsi, dll.

Untuk membuatnya kita bisa menggunakan database sebagai penyimpanan data-data tersebut.

Berikut langkah-langkahnya.

## Buat Setting Model Dan Migration

Buat sebuah model `Setting` beserta migrasinya dengan perintah artisan.

```bash
php artisan make:model Setting -m
```

Lalu buka file migration yang baru saja dibuat, dan buat skema tabelnya sesuai data sistem anda. 

```php
public function up()
{
    Schema::create('setting', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->text('description');
        $table->timestamps();
    });
}
```

Lalu jalankan migrasi.

```bash
php artisan migrate
```

## Seeding Pengaturan Default

Kita akan mengisi tabel pengaturan dengan menggunakan seeder.

```bash
php artisan make:seeder SiteSeeder
```

Lalu isi seeder tersebut sesuai data aplikasi kita.

```php
use Illuminate\Support\Facades\DB;

public function run()
{
    DB::table('site')->insert([
        'name' => 'Blog',
        'description' => 'Simple Blog',
    ]);
}
```

Lalu kita jalankan seedernya.

```bash
php artisan db:seed --class=SiteSeeder
```

## Tambahkan Cache Setting

Agar data yang diload lebih cepat, kita akan men-cache data site di `AppServiceProfider`.

Buka file `app/Providers/AppServiceProviders.php`, tambahkan kode berikut di `function` boot.

```php
use App\Models\Site;

public function boot()
{
    if (Schema::hasTable('site')) {
        Cache::forever('setting', Site::first());
    }
}
```

## Buat Helper Setting

Langkah terakhir kita akan membuat sebuah helper untuk menampilkan data aplikasi kita.

Tambahkan fungsi berikut di file `helper` kalian.

```php
function site($key)
{
    return Cache::get('setting')->$key;
}
```

## Penggunaan

Untuk menggunakanya anda tinggal memanggil helper `site(nama-data)` di aplikasi anda.

Contoh penggunaan di blade.

```php
Nama site : {% raw %}{{ site('name') }}{% endraw %}
```

Hasilnya.

```
Nama site : Blog
```

Silahkan dicoba.