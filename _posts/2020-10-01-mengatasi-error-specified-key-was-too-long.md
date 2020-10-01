---
title: Mengatasi Error Specified Key Was Too Long Laravel
layout: post
categories: laravel
date: 2020-10-01 19:00:00 +0700
---

Ada perubahan pada default database character set laravel, dimana sekarang laravel menggunakan **utf8mb4**.

Bagi yang masih menggunakan *MariaDB* atau *MySQL* dengan versi `5.7.7` kebawah akan mengalami error ketika hendak melakukan migrasi database.

Errornya seperti berikut ini.

> [Illuminate\Database\QueryException]
>  SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key  was too long; max key length is 767 bytes (SQL: alter table 'users' add unique 'users_email_unique'('email'))

Untuk mengatasinya, kita hanya perlu mengatur `defaultStringLength` di file `AppServiceProvider.php` laravel.

```php
use Illuminate\Database\Schema\Builder;

public function boot()
{
    Builder::defaultStringLength(191);
}
```

Silahkan dicoba.