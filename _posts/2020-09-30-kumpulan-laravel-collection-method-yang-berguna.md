---
title: Kumpulan Laravel Collection Method Yang Berguna
date: 2020-09-30 20:00:00 +0700
categories: laravel
layout: post
---

Di penghujung bulan september, saya membawa kumpulan method di collection laravel yang berguna.

Laravel sendiri memiliki fitur yang bernama collection. Dimana fitur dapat membantu programmer dalam memanipulasi sebuah data berbentuk `array`.

Dengan collection, pekerjaan yang berhubungan dengan array akan lebih mudah.

**Collection** memiliki banyak method yang bisa kita gunakan. Dengan banyaknya method tersebut membuat saya terkadang malas atau sulit untuk mencari method yang dibutuhkan.

Untuk itu saya sudah mengumpulkan method-method yang ada pada collection laravel yang menurut saya paling berguna.

Langsung saja, berikut daftarnya.

## Pluck

Method pluck menampilkan isi dari array berdasarkan `key` yang diberikan.

Contoh, disini saya memiliki sebuah collection `$data` yang berisi array sebuah data beberapa orang.

```php
$data = collect([
    ['id' => '1', 'nama' => 'Ibrahim'],
    ['id' => '2', 'nama' => 'Sarah']
]);
```

Lalu saya akan mengambil `nama` dari data tersebut.

```php
$plucked = $data->pluck('nama');

// ['Ibrahim', 'Sarah']
```