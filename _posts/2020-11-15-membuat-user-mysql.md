---
layout: post
title: Cara Membuat User MySQL
date: 2020-11-15 20:27:00 +0700
categories: database mysql
---

Di __MySQL__ kita dapat membuat user. User tersebut dapat diberi akses untuk mengakses database yang ditentukan.

Hal ini bertujuan untuk membatasi aktivitas user yang berkaitan dengan database, tentunya agar lebih aman.

## Masuk Ke Shell MySQL

Langkah pertama untuk membuat user di database adalah masuk ke *shell MySQL*.

Pilih salah satu perintah, jika error coba perintah dibawahnya.

```bash
mysql -u root -p
mysql -u root
sudo mysql
```

## Membuat User

Untuk membuat user, gunakan perintah berikut.

```sql
CREATE USER 'nama';
```

Contoh.

```sql
CREATE USER 'ibrahim';
```

## Membuat User dengan Password

Untuk membuat user dengan password, gunakan perintah berikut.

```sql
CREATE USER 'nama' IDENTIFIED BY 'password';
```

Contoh.

```sql
CREATE USER 'ibrahim' IDENTIFIED BY 'gu4k3c3';
```

## Membuat User dengan Batasan IP Address

Untuk membuat user dengan password, gunakan perintah berikut.

```sql
CREATE USER 'nama'@'ip atau host' IDENTIFIED BY 'password';
```

Contoh.

```sql
CREATE USER 'ibrahim'@'localhost' IDENTIFIED BY 'gu4k3c3';
```