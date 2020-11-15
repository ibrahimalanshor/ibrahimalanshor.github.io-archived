---
layout: post
title: Cara Instal phpMyAdmin Di Linux
date: 2020-11-15 19:58:00 +0700
categories: linux database
---

__phpMyAdmin__ adalah sebuah aplikasi berbasis web yang digunakan untuk mengelola database MySQL.

Berikut langkah-langkah instalasinya.

## Install phpMyAdmin

Langsung install phpMyAdmin menggunakan apt.

```bash
sudo apt update
sudo apt install phpMyAdmin
```

Setelah itu anda akan diminta untuk memilih jenis web server. Pilihlah sesuai jenis server komputer anda, defaultnya __apache2__.

## Penggunaan

Untuk menggunakan phpMyAdmin, anda bisa langsung mengakses webnya.

```
http://ip-server-atau-domain/phpmyadmin
```

![phpMyAdmin]({{ site.url }}/img/phpmyadmin.png)