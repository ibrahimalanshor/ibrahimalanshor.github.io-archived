---
layout: post
title: "MySQL Subquery"
tags: [mysql]
date: 2022-08-07 17:00:00 +0700
---

Subquery (inner query) adalah kueri di dalam kueri lain (outer query).

## Kasus

Tabel `foods` terdiri dari kolom, `name`, `level`, dan `price`.

```sql
SELECT * FROM foods;
-- +----+---------+-------+-------+
-- | id | name    | level | price |
-- +----+---------+-------+-------+
-- |  1 | chicken |     1 |  6000 |
-- |  2 | tempe   |     1 | 10000 |
-- |  3 | telor   |     2 |  6000 |
-- |  4 | bakso   |     1 | 10000 |
-- |  5 | soto    |     2 | 10000 |
-- |  6 | indomie |     3 |  3000 |
-- |  7 | roti    |     3 |  4000 |
-- +----+---------+-------+-------+
```

## Contoh 1

Menampilkan data di table `foods` yang harganya lebih dari rata-rata harga di table `foods`.

```sql
-- Rata rata harga
SELECT AVG(price) FROM foods;
-- +------------+
-- | AVG(price) |
-- +------------+
-- |  7000.0000 |
-- +------------+

-- Data yang harganya lebih dari rata-rata harga
SELECT name, price FROM foods
WHERE price > (
  SELECT AVG(price)
  FROM foods
);
-- +-------+-------+
-- | name  | price |
-- +-------+-------+
-- | tempe | 10000 |
-- | bakso | 10000 |
-- | soto  | 10000 |
-- +-------+-------+
```

## Contoh 2

Menampilkan data di table `foods` yang harganya lebih dari rata-rata harga di setiap level yang sama pada table `foods`.

```sql
-- Rata rata harga di setiap level
SELECT level, AVG(price) FROM foods GROUP BY level;
-- +-------+------------+
-- | level | AVG(price) |
-- +-------+------------+
-- |     1 |  8666.6667 |
-- |     2 |  8000.0000 |
-- |     3 |  3500.0000 |
-- +-------+------------+

-- Data yang harganya lebih dari rata-rata harga di level yang sama
SELECT name, level, price
FROM foods outer_foods
WHERE price > (
  SELECT AVG(price)
  FROM foods inner_foods
  WHERE inner_foods.level = outer_foods.level
);
-- +-------+-------+-------+
-- | name  | level | price |
-- +-------+-------+-------+
-- | tempe |     1 | 10000 |
-- | bakso |     1 | 10000 |
-- | soto  |     2 | 10000 |
-- | roti  |     3 |  4000 |
-- +-------+-------+-------+
```

> Contoh ke 2 disebut dengan `correlated subquery` yang artinya subkueri tersebut bergantung pada outer kuerinya, jika dijalankan secara independen akan menghasilkan error.