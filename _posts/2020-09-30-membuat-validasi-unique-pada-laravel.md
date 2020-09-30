---
title: Membuat Validasi Unique Pada Laravel
date: 2020-09-30 20:20:00 +0700
layout: post
categories: laravel
---

Laravel memiliki berbagai metode validasi yang sangat bervariasi.

Salah satunya `unique`.

Metode ini akan mengecek inputan user apakah sudah ada atau belum di database.

Langsung saja berikut tutorialnya.

## Buat Validasi

Disini saya akan memvalidasi kolom title untuk memastikan data tersebut belum ada di database.

```php
public function store(Request $request)
{
    $request->validate([
        'title' => 'required|string|unique:posts'
    ]);
}
```

## Unique Update

Ada sedikit masalah dalam penggunaan metode `unique` disaat saya memperbarui data.

Untuk mengatasinya kita bisa menambah beberapa parameter tambahan.

```php
public function update(Request $request, $id)
{
    $request->validate([
        'title' => 'required|string|max:255:unique:posts,title,'.$id
    ]);
}
```

Silahkan dicoba.