---
title: Kumpulan PHP String Function Yang Berguna
layout: post
date: 2020-09-17 19:50:00 +0700
categories: php
---

Berikut adalah PHP String Function yang berguna dalam kegiatan *programming*.

## substr

Function ini berfungsi untuk memotong atau mengambil beberapa bagian dari sebuah `string`.

Syntax

```php
substr($string, $start, $length)
```

- `$string` : wajib. Berisi string yang akan dipotong.
- `$start` : wajib. Berisi posisi dimulainya proses pemotongan.
- `$length`: optional. Berisi jumlah/total huruf yang akan dipotong.

Contoh penggunaan.

```php
echo substr("Saya suka omong kosong", 15);
echo "<br>";
echo substr("Saya suka omong kosong", 15, 5);
```

Hasilnya.

```
kosong
koso
```

## strpos

Function ini berfungsi untuk mencari posisi pertama sebuah karakter atau huruf didalam `string`.

Syntax

```php
strpos($string, $find, $start)
```

- `$string`: wajib. String yang akan dicari.
- `$find`: wajib. Kata kunci.
- `$start`: optional. Posisi dimulainya pencarian.

Contoh.

```php
echo strpos("Saya suka omong kosong", "suka");
```

Hasilnya

```
5
```

## strtolower & strtoupper

Kedua fungsi ini digunakan untuk mengonversi string menjadi `uppercase` (huruf besar) atau `lowercase` (huruf kecil).

Contoh.

```php
echo strtoupper('Saya Suka Omong Kosong');
echo "<br>";
echo strtolower('Saya Suka Omong Kosong');
```

Hasilnya.

```
SAYA SUKA OMONG KOSONG
saya suka omong kosong
```

## str_replace

Fungsi ini digunakan untuk mengganti beberapa karakter pada sebuah `string` dengan karakter lainnya.

Syntax.

```php
str_replace($find, $replace, $string, $count)
```

- `$find`: wajib. Karakter yang akan diganti.
- `$replace`: wajib. Karakter yang akan mengganti variabel `find`.
- `$string`: wajib. String yang akan diganti.
- `$count`: optional. Berapa banyak string yang akan diganti. 

Contoh.

```php
echo str_replace("suka","benci","Saya suka omong kosong");
```

Hasilnya.

```php
Saya benci omong kosong
```

