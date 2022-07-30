---
layout: post
title: "MySQL SELECT DISTINCT"
tags: [mysql]
date: 2022-07-30 20:30:00 +0700
---

`DISTINCT` kalusa digunakan pada `SELECT` statement untuk menghilangkan baris yang duplikat.

```sql
-- Semua users
SELECT name from users;
-- +------+
-- | name |
-- +------+
-- | dev  |
-- | NULL |
-- | NULL |
-- | sing |
-- | dev  |
-- | dev  |
-- | sing |
-- | sing |
-- | sing |
-- +------+

-- Hapus nama yang duplikat
SELECT DISTINCT name from users;
-- +------+
-- | name |
-- +------+
-- | dev  |
-- | NULL |
-- | sing |
-- +------+
```
