---
layout: post
title: "Alter Table: Change vs Modify Column MySQL"
tags: [mysql, database]
date: 2022-06-04 14:00:00 +0700
---

Untuk mengubah kolom pada tabel MySQL yang sudah terlanjur dibuat, saya biasanya menggunakan perintah alter table `CHANGE` atau `MODIFY`.

## CHANGE

Perintah `CHANGE` dapat digunakan untuk mengubah nama kolom, tipe data, ukuran, atribut, dsb.

```sql
ALTER TABLE pegawai CHANGE COLUMN nama nama_pegawai VARCHAR(50) NOT NULL;
```

## MODIFY

Perintah `MODIFY` memiliki kegunaan seperti `CHANGE`, kecuali mengubah nama kolom.

```sql
ALTER TABLE pegawai MODIFY COLUMN nama VARCHAR(50) NOT NULL;
```