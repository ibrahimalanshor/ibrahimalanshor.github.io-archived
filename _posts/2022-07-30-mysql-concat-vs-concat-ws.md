---
layout: post
title: "MySQL CONCAT VS CONCAT_WS Function"
tags: [mysql]
date: 2022-07-30 21:00:00 +0700
---

Fungsi `CONCAT` dan `CONCAT_WS` sama-sama digunakan untuk menggabungkan beberapa string menjadi satu.

Perbedaannya, `CONCAT_WS` dapat menambahkan separator di setiap string yang akan digabungkan.

Separator pada `CONCAT_WS` diletakan di argumen pertama fungsi.

```sql
-- CONCAT
SELECT CONCAT(id, name) `id name` FROM mysql_null;
-- +---------+
-- | id name |
-- +---------+
-- | 1dev    |
-- | NULL    |
-- | NULL    |
-- | 4sing   |
-- | 5dev    |
-- | 6dev    |
-- | 7sing   |
-- | 8sing   |
-- | 9sing   |
-- +---------+

-- CONCAT WS
SELECT CONCAT_WS(' = ', id, name) `id = name` FROM mysql_null;
-- +-----------+
-- | id = name |
-- +-----------+
-- | 1 = dev   |
-- | 2         |
-- | 3         |
-- | 4 = sing  |
-- | 5 = dev   |
-- | 6 = dev   |
-- | 7 = sing  |
-- | 8 = sing  |
-- | 9 = sing  |
-- +-----------+
```

Dapat dilihat juga perbedaan lainnya, jika data pada kolom yang akan digabungkan nilainya `NULL`, `CONCAT` akan mengembalikan `NULL`, `CONCAT_WS` tetap melakukan penggabungan.