---
layout: post
title: "MySQL HAVING VS WHERE Clause"
tags: [mysql]
date: 2022-08-06 11:00:00 +0700
---

Clause `HAVING` dan `WHERE` memiliki fungsi yang mirip tetapi berbeda, yaitu untuk memfilter data berdasarkan kondisi tertentu.

`WHERE` digunakan untuk memfilter data pada tabel yang akan diproses.

Sementara `HAVING` digunakan untuk memfilter data pada hasil proses group tabel.

Contoh menampilkan data pada tabel `foods` yang harganya lebih dari `1000` menggunakan `WHERE`.
 
```sql
SELECT name, price FROM foods WHERE price > 1000;
-- +---------+-------+
-- | name    | price |
-- +---------+-------+
-- | chicken |  6000 |
-- | tempe   | 10000 |
-- | telor   |  6000 |
-- | bakso   | 10000 |
-- | soto    | 10000 |
-- | indomie |  3000 |
-- +---------+-------+
```

Contoh menampilkan data pada tabel `foods` yang dikelompokan berdasarkan harganya dan jumlah anggota kelompoknya lebih dari `1` menggunakan `HAVING`.

```sql
SELECT price, COUNT(*) total FROM foods GROUP BY price HAVING total > 1;
-- +-------+-------+
-- | price | total |
-- +-------+-------+
-- |  6000 |     2 |
-- | 10000 |     3 |
-- +-------+-------+
```

Untuk menggunakan `WHERE` clause harus menggunakan kondisi berdasarkan nama kolom pada tabel tujuan, sedangkan `HAVING` dapat menggunakan nama kolom, alias atau fungsi agregasi.

```sql
SELECT name `nama_menu`, price `harga_jual` from foods WHERE `harga_jual` > 5000;
-- ERROR 1054 (42S22): Unknown column 'harga_jual' in 'where clause'

SELECT name `nama_menu`, price `harga_jual` from foods HAVING `harga_jual` > 5000;
-- +-----------+------------+
-- | nama_menu | harga_jual |
-- +-----------+------------+
-- | chicken   |       6000 |
-- | tempe     |      10000 |
-- | telor     |       6000 |
-- | bakso     |      10000 |
-- | soto      |      10000 |
-- +-----------+------------+
```