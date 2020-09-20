---
title: Beberapa Masalah Pada Multiple Authentication Guard Laravel
layout: post
date: 2020-09-20 16:15:00 +0700
categories: laravel
---

Setelah berhasil membuat fitur *multiple authentication guard* pada Laravel kemarin.

Ada beberapa masalah yang muncul pada fitur tersebut.

Berikut akan saya sebutkan masalahnya beserta penyelesaianya.

## Redirect If Authenticated

Masalah pertama adalah ketika ada user yang sudah login dan kemudian mengakses route yang memiliki middleware guest.

Laravel akan otomatis mengalihkan kita ke `/home`.

Contohnya ketika kita sudah login ke guard admin, dan kita mencoba mengakses halaman login admin, maka laravel akan mengalihkan kita ke `/home`.

Padahal mungkin kita ingin alamat redirectnya adalah ke `/admin`,  atau dashboard admin.

Untuk mengaturnya, silahkan buka file `app/Http/Middleware/RedirectIfAuthenticated.php`. Dan ganti fungsi `handle` menjadi seperti berikut.

```php
public function handle($request, Closure $next, $guard = null)
{
    if ($guard == 'admin' && Auth::guard('admin')->check()) {
        return redirect('/admin');
    }
    if (Auth::guard($guard)->check()) {
        return redirect('/user');
    }

    return $next($request);
}
```

Silahkan sesuaikan dengan aplikasi anda.

## Authentication Exeption Handler

Masalah berikutnya adalah ketika ada non-loged user mencoba mengakses route yang memiliki middleware auth.

Maka Laravel mengalihkan kita ke `login`.

Contohnya ketika kita belum login dan mengakses halaman `admin/post` maka kita akan dialihkan ke halaman login user.

Padahal seharusnya kita dialihkan ke halaman login admin.

Untuk mengaturnya silahkan buka file `app/Exception/Handler.php`.

Gunakan `AuthenticationException` lalu buat sebuah fungsi baru untuk menangani user yang mencoba masuk ke halaman yang terautentikasi.

```php
use Illuminate\Auth\AuthenticationException;

public function unauthenticated($request, AuthenticationException $exception)
{
    if ($request->expectsJson()) {
        return response()->json(['error' => 'Unauthenticated.'], 401);
    }
    if ($request->is('admin') || $request->is('admin/*')) {
        return redirect()->guest('admin/login');
    }
    return redirect()->guest(route('login'));
}
```

Silahkan sesuaikan dengan aplikasi anda.