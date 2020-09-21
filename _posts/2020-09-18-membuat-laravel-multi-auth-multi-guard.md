---
title: Membuat Multiple Authentication Guard Pada Laravel
layout: post
date: 2020-09-18 19:45:00 +0700
categories: laravel
---

Secara *default* Laravel menyediakan dua buah `guard`, yaitu web dan user.

**Guard** sendiri adalah penjaga atau jenis autentikasi pada aplikasi Laravel.

Kita bisa membuat guard kita sendiri. Contohnya kita ingin membuat guard untuk admin, atau guard untuk writer.

Disini saya akan membuat sebuah guard bernama `admin`. Yang digunakan untuk autentikasi admin.

Langsung saja, berikut langkah-langkahnya.

## Membuat Admin Model Dan Migration

Pertama saya akan mebuat model untuk tabel admin.

```bash
php artisan make:model Admin -m
```

Lalu saya akan mengisi kolom migrasi tabel admin seperti pada tabel user.

```php
Schema::create('admin', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->string('email')->unique();
    $table->string('password');
    $table->rememberToken();
    $table->timestamps();
});
```

Lalu saya migrasi.

```bash
php artisan migrate
```

## Mengatur Model Admin

Setelah membuat model admin, saya akan mengatur model tersebut agar bisa diautentikasi.

Saya akan mengaturnya mirip-mirip dengan model user.

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Foundation\Auth\User as Authenticatable;
use Illuminate\Notifications\Notifiable;

class Admin extends Authenticatable
{
    use HasFactory, Notifiable;

    protected $table = 'admin';
}

```

## Membuat Guard Admin

Buka file `config/auth.php`. Lalu tambahkan kode berikut di bagian `guards`.

```php
'guards' => [
    'web' => [
        'driver' => 'session',
        'provider' => 'users',
    ],

    // Tambahkan Guard admin
    'admin' => [
        'driver' => 'session',
        'provider' => 'admins'
    ],

    'api' => [
        'driver' => 'token',
        'provider' => 'users',
        'hash' => false,
    ],
],
```

Lalu tambahkan kode berikut di bagian `providers`.

```php
'providers' => [
    'users' => [
        'driver' => 'eloquent',
        'model' => App\Models\User::class,
    ],
	
    // Tambahkan Kode Berikut
    'admins' => [
        'driver' => 'eloquent',
        'model' => App\Models\Admin::class
    ]
],
```

## Membuat Login Controller Admin

Setelah membuat guard, kita akan membuat controller untuk login admin.

Buat sebuah controller dengan perintah artisan.

```bash
php artisan make:controller Admin/Auth/LoginController
```

Lalu buat sebuah `function construct` untuk mengatur middleware, dimana hanya *non-loged* admin yang hanya bisa mengakses method di controller ini, kecuali method `logout`.  

```php
public function __construct()
{
    $this->middleware('guest:admin', ['except' => 'logout']);
}
```



Lalu buat beberepa method di controller tersebut.

### Login Form Function

```php
public function showLoginForm()
{
    return view('admin.auth.login');
}
```



### Login Function

```php
use Auth;

public function login(Request $request)
{
    $request->validate([
        'email' => 'required|email|exists:admin',
        'password' => 'required'
    ]);

    if (Auth::guard('admin')->attempt($request->only('email', 'password'), $request->get('remember'))) {
        return redirect('admin');
    }

    return back()->withInput($request->only('email', 'remember'));
}

```

### Logout Function

```php
public function logout()
{
    Auth::guard('admin')->logout();
    return redirect('/');
}
```



## Membuat Route Login Admin

Lalu kita akan membuat route untuk login admin.

Buka file `routes/web.php`. Lalu tambahkan route untuk login admin.

```php
use App\Http\Controllers\Admin\Auth\LoginController;

Route::get('/admin/login', [LoginController::class, 'showLoginForm']);
Route::post('/admin/login', [LoginController::class, 'login'])->name('admin.login');
```

## Membuat View Login Admin

Langkah terakhir kita akan membuat view untuk login admin.

Buat sebuah file blade `login.php` di `resources/views/admin/auth`.

Isi dengan form login seperti kode berikut.

```html
<form method="POST" action="{% raw %}{{ route('admin.login') }}{% endraw %}">
    <h3>Admin Login</h3>
    <hr>
    @csrf

    <div class="form-group">
        <label for="email">{% raw %}{{ __('E-Mail Address') }}{% endraw %}</label>

        <input id="email" type="email" class="form-control @error('email') is-invalid @enderror" name="email" value="{% raw %}{{ old('email') }}{% endraw %}" required autocomplete="email" autofocus>

        @error('email')
        <span class="invalid-feedback" role="alert">
            <strong>{% raw %}{{ $message }}{% endraw %}</strong>
        </span>
        @enderror
    </div>

    <div class="form-group">
        <label for="password">{% raw %}{{ __('Password') }}{% endraw %}</label>

        <input id="password" type="password" class="form-control @error('password') is-invalid @enderror" name="password" required autocomplete="current-password">

        @error('password')
        <span class="invalid-feedback" role="alert">
            <strong>{% raw %}{{ $message }}{% endraw %}</strong>
        </span>
        @enderror
    </div>

    <div class="form-check form-group">
        <input class="form-check-input" type="checkbox" name="remember" id="remember" {% raw %}{{ old('remember') ? 'checked' : '' }}{% endraw %}>

        <label class="form-check-label" for="remember">
            {% raw %}{{ __('Remember Me') }}{% endraw %}
        </label>
    </div>

    <button type="submit" class="btn btn-primary btn-block mb-2">
        {% raw %}{{ __('Login') }}{% endraw %}
    </button>
</form>
```

## Penutup

Silahkan Mencoba.