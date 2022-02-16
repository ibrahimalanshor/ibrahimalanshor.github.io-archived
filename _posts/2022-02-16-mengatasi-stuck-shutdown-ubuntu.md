---
layout: "post"
title: "Cara Mengatasi Ubuntu Suspend/Shutdown Stuck"
date: 2022-02-16 09:00:00 +0700
---

Setelah menginstal ubuntu, saya mengalami pengalaman stuck pada saat suspend/shutdown.

Layar hitam, indikator HDD menyala, dan kipas berputar kencang.

Setelah melakukan beberapa upaya, akhirnya masalah tersebut selesai dengan menurunkan versi Grub.

Caranya pada saat booting, terdapat beberapa pilihan boot, pilih __'Advanced Options'__, kemudian pilih kernel yang dibawahnya.

Pada kasus saya saya menurunkan ke __5.11.0.27__.

Setelah booting cek versi kernel lewat terminal dengan komando

```bash
uname -r
```

Pada beberapa kasus, laptop akan langsung booting ke ubuntu tanpa menampilkan pilihan boot, sehingga cara di atas tidak bisa digunakan.

Untuk mengatasinya anda dapat mencoba cara lain yang akan saya bahas pada lain waktu.