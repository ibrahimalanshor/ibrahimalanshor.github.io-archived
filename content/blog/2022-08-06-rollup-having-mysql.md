---
layout: post
title: "MySQL ROLLUP AND GROUPING"
tags: [mysql]
date: 2022-08-06 20:00:00 +0700
---

`ROLLUP` adalah modifier pada `GROUP BY` clause yang menambahkan ringkasan hasil dari clause `GROUP BY`.

Contoh.

```sql
SELECT price harga, SUM(price) total, COUNT(price) jumlah
FROM foods
GROUP BY price
WITH ROLLUP;
-- +-------+-------+--------+
-- | harga | total | jumlah |
-- +-------+-------+--------+
-- |  3000 |  3000 |      1 |
-- |  6000 | 12000 |      2 |
-- | 10000 | 30000 |      3 |
-- |  NULL | 45000 |      6 |
-- +-------+-------+--------+
```

`WITH ROLLUP` akan menambahkan ringkasan hasil group berisi nilai `NULL` dengan hasil ringkasanya. 


## GROUPING

`GROUPING` adalah fungsi untuk mengecek apakah row tertentu merepresentasikan ringkasan yang dihasilkan dari `WITH ROLLUP`.

```sql
SELECT price harga, SUM(price) total, COUNT(price) jumlah, GROUPING(price) `apakah ringkasan`
FROM foods
GROUP BY price
WITH ROLLUP;
-- +-------+-------+--------+------------------+
-- | harga | total | jumlah | apakah ringkasan |
-- +-------+-------+--------+------------------+
-- |  3000 |  3000 |      1 |                0 |
-- |  6000 | 12000 |      2 |                0 |
-- | 10000 | 30000 |      3 |                0 |
-- |  NULL | 45000 |      6 |                1 |
-- +-------+-------+--------+------------------+
```

Fungis `GROUPING` akan mengembalikan nilai `1` jika pengecekannya benar, jika tidak mengembalikan `0`.