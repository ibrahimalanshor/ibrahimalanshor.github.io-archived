---
layout: post
title: "Cara Mengatur DNS Nameserver Ubuntu"
tags: [dns, linux, ubuntu]
date: 2022-05-04 12:00:00 +0700
---

DNS adalah sebuah sistem yang menyimpan informasi data domain dalam jaringan. DNS akan mencari alamat IP dari domain yang kita minta.

DNS server bawaaan ISP bisa jadi lambat, tidak stabil dan tidak terlalu privat, untuk mengatasinya anda dapat menggunakan DNS server dari pihak ketiga.

Berikut beberapa DNS server publik gratis yang dapat anda gunakan.

* Cloudflare DNS:   1.1.1.1 dan 1.0.0.1
* Google DNS:   8.8.8.8 dan 8.8.4.4
* Comodo Secure:   8.26.56.26 dan 8.20.247.20
* Open DNS:  208.67.222.222 dan 208.67.220.220

Pada Ubuntu, konfigurasi DNS server terdapat pada file `/etc/resolv.conf`, buka file tersebut untuk mengubah DNS server.

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Ubah nameserver sesuai dengan DNS server yang anda inginkan.