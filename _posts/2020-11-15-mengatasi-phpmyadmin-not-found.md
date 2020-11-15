---
layout: post
title: phpmyadmin Was Not Found In This Server
date: 2020-11-15 20:10:00 +0700
categories: linux database
---

Pada proses instalasi __phpMyAdmin__, saya beberapa kali menemukan kendala setelah instalasi selesai. Yaitu pada saat mencoba mengakses web-nya.

![phpMyAdmin Was Not Found In This Server]({{ site.url }}/img/phpmyadmin-not-found.png)

Setelah saya telusuri, ternyata hal ini disebabkan karena konfigurasi phpmyadmin belum dimasukan ke server *Apache*.

Untuk mengatasinya ada dua cara yang bisa dilakukan, yaitu menambahkan konfigurasi phpmyadmin ke apache dan membuat *symbolic link*.

## Menambahkan Konfigurasi phpMyAdmin

Buka berkas konfigurasi apache dengan kode editor kalian, disini saya menggunakan *nano*.

```bash
sudo nano /etc/apache2/apache2.conf
```

Lalu tambahkan kode berikut di baris terakhir berkasi tersebut.

```bash
Include /etc/phpmyadmin/apache.conf
```

Restart apache.

```bash
sudo systemctl restart apache2
```

## Membuat Symbolic Link

Cara kedua yaitu membuat Symbolic Link, cara ini mudah sekali, hanya dengan satu perintah. 

```bash
sudo ln -s /usr/share/phpmyadmin /var/www/html/admin/phpmyadmin
```