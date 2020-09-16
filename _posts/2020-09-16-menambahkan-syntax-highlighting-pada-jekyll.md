---
layout: post
title: Menambahkan Syntax Highlighting Pada Jekyll
categories: jekyll
date: 2020-09-16 10:16:00 +0700
---

Untuk menulis sebuah artikel pemrograman, kita membutuhkan sebuah alat yang bernama **Syntax Highlight**.

Syntax Highlight berguna memberi tanda atau memberi **style** tersendiri pada kode yang ditentukan.

Sehingga pembaca menjadi lebih nyaman dalam membacanya.

Di Jekyll kita dapat menggunakan **Rouge** sebagai alat penunjangnya.

Kita tidak perlu repot-repot menginstalnya, karena modul tersebut merupakan modul default di Jekyll.

Yang perlu kita lakukan adalah memberi style pada **Rouge** tersebut.

## Menambahkan Artikel

Pertama-tama buat sebuah artikel, dan isi kontenya dengan syntax pemrograman, contohnya HTML.

```markdown
​```html
	<b>Saya suka omong kosong</b>
​```
```

Simpan coba lihat hasilnya.

Maka akan kelihatan putih polos.

## Memberi Style

Untuk memberi stylenya kita bisa membuat sendiri style cssnya.

Atau kalian bisa menggunakan **Pygments**.

Anda bisa mendownloadnya [disini](http://jwarby.github.io/jekyll-pygments-themes/languages/javascript.html).

Setelah didownload langsung saja pasang CSSnya.

Dan artikelmu sudah ter-*highlight*.