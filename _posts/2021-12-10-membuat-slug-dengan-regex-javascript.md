---
layout: post
title: "Cara Membuat Slug Dengan Regex Javascript"
---

Slug adalah sebuah teks yang biasanya digunakan sebagai url dari sebuah artikel atau postingan pada sebuah website.

Contoh Slug :

* /membuat-slug-regex-javascript
* /membuat-game-javascript
* /belajar-html5

Slug berfungsi untuk menyederhanakan url agar lebih mudah diingat ketika akan mengaksesnya.

Slug biasanya dibangun dari __judul artikel/post__ dengan aturan tertentu.

Pada umumnya slug berasal dari judul artikel kemudian di huruf kecilkan semua, lalu diubah spasinya menjadi strip (-).

Untuk membuat slug, anda dapat memanfaatkan __regex__ untuk menghilangkan dan mengubah karakter pada teks judul.

Berikut adalah fungsi regex untuk membuat slug pada javascript.

```javascript
const slugify = title => {
  return title.toLowerCase()
    .replace(/\s+/g, '-')
    .replace(/[^\w\-]/g, '')
    .replace(/\-\-+/g, '-')
    .replace(/^-+/, '')
    .replace(/-+$/, '')
}

console.log(slugify('Tutorial Dual Boot Linux Mint dan Windows 10'))
// tutorial-dual-boot-linux-mint-dan-windows-10

console.log(slugify('Tutorial    Instal <x> $$ ----Windows'))
// tutorial-install-x-windows

console.log(slugify('--    Instal <x> $$ ----Windows--'))
// install-x-windows
```

Langkah-langkah

1. Ubah teks menjadi huruf kecil semua
2. Ganti semua spasi dengan strip (-)
3. Hilangkan semua karakter kecuali huruf, angka, dan strip (-)
4. Hilangkan semua dobel strip (-)
5. Hilangkan strip (-) yang ada di awal teks
6. Hilangkan strip (-) yang ada di akhir teks