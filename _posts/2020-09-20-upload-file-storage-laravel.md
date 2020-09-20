---
title: Upload File Dengan Storage Di Laravel
date: 2020-09-20 17:25:00 +0700
layout: post
categories: laravel
---

Kita dapat dengan mudah mengupload file di Laravel, yaitu dengan memanfaatkan fitur Laravel **Filesystem Storage**.

Dengan **Storage** kita dapat membuat mengupload hanya dengan beberapa langkah.

Langsung saja berikut tutorialnya.

## Controller

Disini saya sudah menyiapkan sebuah fungsi bernama `store` yang digunakan untuk mengupload file.

```php
use Illuminate\Support\Facades\Storage;

public function store(Request $request)
{
}
```

Lalu saya akan membuat variabel `$file` yang menampung request file dan `fileName` yang berisi nama yang dicampur dengan waktu dan ekstensinya.

```php
public function store(Request $request)
{
    $file = $request->file;
    $fileName = pathinfo($file->getClientOriginalName(), PATHINFO_FILENAME);
    $fileName = $fileName.'_'.time().'.'.$file->getClientOriginalExtension();
}
```

Kemudian saya akan menggunakan `Storage` untuk menyimpan file tersebut.

```php
public function store(Request $request)
{
    $file = $request->file;
    $fileName = pathinfo($file->getClientOriginalName(), PATHINFO_FILENAME);
    $fileName = $fileName.'_'.time().'.'.$file->getClientOriginalExtension();

    Storage::putFileAs('public/images', $file, $fileName);
}
```

## Symbolic Link

Selanjutnya kita akan membuat `symbolic link` storage ke public, agar file di storage dapat diakses public.

Jalankan perintah artisan berikut di terminal.

```bash
php artisan storage:link
```

## Penggunaan

Contoh penggunaan.

```php
<img src="{% raw %}{{ asset("storage/imgages/$file") }}{% endraw %}">
```

Silahkan mencoba. 