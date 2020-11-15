---
layout: post
title: Cara Instal LAMP Server Di Linux
date: 2020-11-15 10:52:00 +0700
categories: linux server
---

__LAMP__ (Linux, Apache, Mysql, PHP) adalah perangkat untuk membuat sebuah server website dinamis di Linux.

Lampp memiliki kegunaan yang sama dengan __XAMPP__ di Windows.

Langsung saja, berikut langkah-langkah instalasinya.

## Instal Apache

__Apache__ merupakan salah satu web server yang populer dan sering digunakan. Apache memiliki dokumentasi yang lengkap, dan juga kemudahan konfigurasinya.

Untuk menginstalnya, kita bisa menggunakan *ubuntu package manager* atau APT.

```bash
sudo apt update
sudo apt install apache2
```

Jika sudah selesai, mari kita cek apakah apache sudah terinstal dengan mengunjungi alamat IP server anda di browser.

```
http://ip_server_atau_domain
```

![Apache Default Page]({{ site.url }}/img/apache.png)

## Install MySQL

__MySQL__ merupakan sistem manajemen basis data relasional yang digunakan untuk mengelola database pada sistem.

```bash
sudo apt install mysql-server
```

## Install PHP

__PHP__ merupakan bahasa pemrograman *server-side* yang digunakan untuk membangun sebuah website yang dinamis.

```bash
sudo apt install php libapache2-mod-php php-mysql
```

## Penutup

Untuk kendala atau permasalahan dalam proses instalasi silahkan cari sendiri atau tunggu artikel saya selanjutnya.