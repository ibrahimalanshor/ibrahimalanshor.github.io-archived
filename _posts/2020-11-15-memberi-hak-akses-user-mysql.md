---
layout: post
title: Cara Memberi Hak Akes Pada User MySQL
date: 2020-11-15 20:47:00 +0700
categories: database mysql
---

Seperti yang saya singgung kemarin, setiap user __MySQL__ dapat memiliki akses ke database yang ditentutkan.

Hal ini berguna untuk keamanan sebuah database, jadi kita dapat membatasi pergerakan atau aktivitas user pada database kita.

Berikut daftar hak akses yang dapat dimiliki user.

- __ALL__ - memberikan hak akses penuh
- __CREATE__ - memberikan hak akses untuk membuat database dan tabel
- __DROP__ - memberikan hak akses untuk menghapus database dan tabel
- __SELECT__ - memberikan hak akses untuk membaca database
- __INSERT__ - memberikan hak akses untuk memasukan data ke tabel
- __DELETE__ - memberikan hak akses untuk menghapus data dari tabel
- __UPDATE__ - memberikan hak akses untuk memperbarui data dari tabel


Untuk memerikan hak akses kepada user, gunakan sintaks berikut.

```sql
GRANT hak_akses TO nama_database.nama_tabel TO 'nama_user'@'lokasi';
```

Contoh.

```sql
GRANT ALL TO *.* TO 'ibrahim'@'localhost';
```