---
title: Cara Mengonversi Integer Menjadi Mata Uang PHP
layout: post
date: 2020-10-02 19:50:00 +0700
categories: php
---

Setelah kemarin saya memberikan tutorial cara mengonversi mata uang ke integer php, kali ini saya akan memberikan kebalikanya, yaitu mengonversi dari integer menjadi mata uang.

PHP sendiri sudah menyediakan sebuah fungsi khusus untuk masalah ini, jadi kita tidak perlu repot-repot membuat fungsinya.

Nama fungsinya adalah `number_format`. Fungsi ini mengonversi integer yang diberikan menjadi mata uang, dengan ketentuan yang ditentukan.

Contoh.

```php
$uang = 10000;
echo number_format($uang, 2);

// 10,000.00
```

Parameter setelah integer dapat kita isi dengan jumlah digit dibelakang uang.

```php
$uang = 10000;
echo number_format($uang, 4);

// 10,000.0000
```

Kita juga dapat mengganti koma menjadi titik.

```php
$uang = 10000;
echo number_format($uang, 2, ',', '.');

// 10.000,00
```

Silahkan dicoba.