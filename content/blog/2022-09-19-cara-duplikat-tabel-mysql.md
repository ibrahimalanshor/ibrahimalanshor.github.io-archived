---
layout: post
title: "Cara Duplikat Tabel MySQL"
tags: [mysql]
date: 2022-09-18 20:00:00 +0700
---

Sebagai contoh disini ada tabel `users`.

```bash
mysql> DESCRIBE users;
+--------+-----------------------+------+-----+---------+----------------+
| Field  | Type                  | Null | Key | Default | Extra          |
+--------+-----------------------+------+-----+---------+----------------+
| id     | int                   | NO   | PRI | NULL    | auto_increment |
| name   | varchar(255)          | NO   |     | NULL    |                |
| gender | enum('male','female') | NO   | MUL | NULL    |                |
+--------+-----------------------+------+-----+---------+----------------+
3 rows in set (0,00 sec)

mysql> SELECT * FROM users;
+----+------+--------+
| id | name | gender |
+----+------+--------+
|  1 | Jim  | male   |
|  2 | Wen  | female |
+----+------+--------+
2 rows in set (0,00 sec)
```

Kemudian saya ingin menduplikat atau menyalin tabel tersebut, terdapat 2 cara yang dapat dilakukan.

## 1. CREATE TABLE ... AS SELECT

Cara pertama menggunakan sintak berikut.

```sql
CREATE TABLE nama_tabel AS SELECT * FROM sumber_tabel;
```

Contoh.

```sql
CREATE TABLE users_clone AS SELECT * FROM users;
```

Hasilnya.

```bash
mysql> DESCRIBE users_clone;
+--------+-----------------------+------+-----+---------+-------+
| Field  | Type                  | Null | Key | Default | Extra |
+--------+-----------------------+------+-----+---------+-------+
| id     | int                   | NO   |     | 0       |       |
| name   | varchar(255)          | NO   |     | NULL    |       |
| gender | enum('male','female') | NO   |     | NULL    |       |
+--------+-----------------------+------+-----+---------+-------+
3 rows in set (0,01 sec)
```

Tabel baru yang diduplikat hanya akan mewarisi definisi struktur kolom dasar, pengaturan null, dan nilai default dari tabel sumber, dia tidak mewarisi index dan definisi auto increment.

Selain menyalin defnisi struktur tabel sumber, cara ini juga menyalin isi data pada tabel sumber ke tabel baru.

```bash
mysql> SELECT * FROM users_clone;
+----+------+--------+
| id | name | gender |
+----+------+--------+
|  1 | Jim  | male   |
|  2 | Wen  | female |
+----+------+--------+
2 rows in set (0,00 sec)
```

## 2. CREATE TABLE ... LIKE

Cara kedua menggunakan sintak berikut.

```sql
CREATE TABLE nama_tabel LIKE sumber_tabel;
```

Contoh.

```sql
CREATE TABLE users_copy LIKE users;
```

Hasilnya.

```bash
mysql> DESCRIBE users_copy;
+--------+-----------------------+------+-----+---------+----------------+
| Field  | Type                  | Null | Key | Default | Extra          |
+--------+-----------------------+------+-----+---------+----------------+
| id     | int                   | NO   | PRI | NULL    | auto_increment |
| name   | varchar(255)          | NO   |     | NULL    |                |
| gender | enum('male','female') | NO   | MUL | NULL    |                |
+--------+-----------------------+------+-----+---------+----------------+
3 rows in set (0,01 sec)
```

Tabel baru yang diduplikat akan memiliki struktur yang sama persis dengan tabel sumber, tapi tidak menyalin datanya.

Untuk menyalin datanya, anda perlu menjalankan query lainnya.

```sql
INSERT INTO users_copy SELECT * FROM users;
```

Hasilnya.

```bash
mysql> SELECT * FROM users_copy;
+----+------+--------+
| id | name | gender |
+----+------+--------+
|  1 | Jim  | male   |
|  2 | Wen  | female |
+----+------+--------+
2 rows in set (0,00 sec)
```