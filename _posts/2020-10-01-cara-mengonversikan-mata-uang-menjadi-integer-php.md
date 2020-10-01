---
title: Cara Mengonversikan Mata Uang Menjadi Integer PHP
date: 2020-10-01 19:30:00 +0700
layout: post
categories: php
---

Untuk keperluan manipulasi data yang berupa uang, terkadang kita membutuhkan sebuah alat untuk mengonversi mata uang menjadi integer agar bisa dimanipulasi.

Di PHP kita bisa melakukan hal tersebut dengan memanfaatkan `regex`.

```php
$uang = "Rp 40.000";
$uangInt = (int) preg_replace("/[^0-9]/","",$uang);
echo $uangInt;

// 40000
```

Silahkan dicoba.