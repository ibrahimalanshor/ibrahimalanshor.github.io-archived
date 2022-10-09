---
layout: post
title: "MySQL Boolean"
tags: [mysql]
date: 2022-10-09 20:30:00 +0700
---

Tipe kolom `BOOLEAN` pada mysql sebenarnya adalah sinonim dari `TINYINT(1)`, dengan nilai `0` adalah `false` dan nilai selain `1` adalah `true`.

Contoh saya membuat tabel `users` dengan ada kolom status dengan tipe `BOOLEAN`.

```sql
CREATE TABLE users (
  id INTEGER NOT NULL AUTO_INCREMENT,
  status BOOLEAN NOT NULL,
  PRIMARY KEY (id)
);
```

Ketika saya lihat struktur table `users` yang dibuat, kolom status menjadi bertipe `TINYINT(1)`.

```sql
DESCRIBE users;
/* 
+--------+------------+------+-----+---------+----------------+
| Field  | Type       | Null | Key | Default | Extra          |
+--------+------------+------+-----+---------+----------------+
| id     | int        | NO   | PRI | NULL    | auto_increment |
| status | tinyint(1) | NO   |     | NULL    |                |
+--------+------------+------+-----+---------+----------------+
*/
```

Karena bertipe `TINYINT` kolom status dapat diisi dengan nilai angka dan juga nilai boolean.

```sql
INSERT INTO users
  (status)
VALUES
  (true), (false), (1), (0), (2), (8);
```

Hasilnya.

```sql
SELECT * FROM users;
/*
+----+--------+
| id | status |
+----+--------+
|  1 |      1 |
|  2 |      0 |
|  3 |      1 |
|  4 |      0 |
|  5 |      2 |
|  6 |      8 |
+----+--------+
*/
```

Dapat dilihat `true` dan `false` otomatis akan dikonversi menjadi 1 dan 0.

## Boolean Operator

Untuk melakukan operasi pada kolom bertipe boolean anda dapet menggunakan equal atau `IS` operator.

```sql
SELECT * FROM users WHERE status = true;
/*
+----+--------+
| id | status |
+----+--------+
|  1 |      1 |
|  3 |      1 |
+----+--------+
*/
SELECT * FROM users WHERE status IS true;
/*
+----+--------+
| id | status |
+----+--------+
|  1 |      1 |
|  3 |      1 |
|  5 |      2 |
|  6 |      8 |
+----+--------+
*/
```

Ketika menggunakan equal operator dengan nilai konstanta `TRUE` atau `FALSE` nilai tersebut akan dievaluasi ke `1` atau `0`, sehingga nilai selain itu tidak tampil.