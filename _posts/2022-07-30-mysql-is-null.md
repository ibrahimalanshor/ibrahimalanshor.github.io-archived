---
layout: post
title: "MySQL IS NULL Operator"
tags: [mysql]
date: 2022-07-30 20:00:00 +0700
---

`NULL` adalah nilai yang tidak diketahui, tidak ada nilainya, tidak ada isinya, atau yang hilang.

Untuk mengecek sebuah nilai apakah `NULL`, gunakan operator `IS NULL` dan kebalikannya dengan `IS NOT NULL`.

```sql
SELECT 1 IS NULL, 0 IS NULL, '' IS NOT NULL, 'test' IS NOT NULL;
-- +-----------+-----------+----------------+--------------------+
-- | 1 IS NULL | 0 IS NULL | '' IS NOT NULL | 'test' IS NOT NULL |
-- +-----------+-----------+----------------+--------------------+
-- |         0 |         0 |              1 |                  1 |
-- +-----------+-----------+----------------+--------------------+
```

`0` dan string kosong `''` bukanlah `NULL`.

Operator `IS NULL` dan `IS NOT NULL` juga dapat digunakan di `WHERE` untuk menampilkan data yang nilainya `NULL` atau sebaliknya.

```sql
SELECT id, name FROM users WHERE name IS NULL;
-- +----+------+
-- | id | name |
-- +----+------+
-- |  2 | NULL |
-- |  3 | NULL |
-- +----+------+
SELECT id, name FROM users WHERE name IS NOT NULL;
-- +----+------+
-- | id | name |
-- +----+------+
-- |  1 | rin  |
-- |  4 | sane |
-- |  5 | bag  |
-- |  6 | mag  |
-- +----+------+
```