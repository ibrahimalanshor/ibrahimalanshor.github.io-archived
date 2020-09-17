---
title: Menampilkan Paragraf Pertama Pada PHP
date: 2020-09-17 08:00 +0700
layout: post
categories: php
---

Untuk keperluan *blogging*, paragraf pertama merupakan hal yang penting.

Biasanya paragraf pertama digunakan untuk menampilkan *post excerpt* atau cuplikan post.

Cuplikan post biasanya diambil dari paragraf pertama dari artikel tersebut.

Untuk membuatnya kita bisa menggunakan dua *function bawaan PHP*, yaitu `substr` dan `strpos`.

**substr** berguna untuk memotong *string* menjadi bagian yang ditentukan.

**strpos** berguna untuk mengambil posisi dari sebuah kalimat/kata dari sebuah *string*.

Logikanya kita akan mengambil posisi tag `p` pertama, lalu kita akan memotong isi dari artikel, dengan spesifikasi dari posisi tag `p` yang kita ambil.

Berikut adalah contoh codenya.

Disini saya memiliki sebuah variabel `konten` yang berisi dua buah paragraf. Anggap saja ini adalah konten artikel. 

```php
<?php
    $konten = "
        <p>Saya suka omong kosong</p>
        <p>Saya suka primata pemberani</p>
    ";
?>
```

Saya membuat sebuah variabel `start` yang berisi index dari tag `p`, dan juga variabel `end` yang berisi index dari penutup tag `p`.

Lalu saya membuat variabel `cuplikan` yang berisi potongan konten dengan spesifikasi variabel yang didefinisikan sebelumnya.

```php
<?php
    $start = strpos($konten, "<p>"); 
    $end = strpos($konten, "</p>");
    $cuplikan = substr($konten, $start, $end-$start+4);
?>
```

Isi dari variabel `cuplikan` akan menampilkan "Saya suka omong kosong".

Silahkan dicoba.