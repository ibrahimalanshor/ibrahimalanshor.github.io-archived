---
layout: post
title: "Window Match Media Javascript"
tags: [javascript]
date: 2022-09-11 19:00:00 +0700
---

`matchMedia` adalah method global window yang mengembalikan objek `MediaQueryList`.

Metod ini dapat digunakan untuk menentukan apakah dokumen sesuai dengan query string yang ditentukan.

Metod ini juga dapat digunakan untuk mendeteksi ketika terdapat perubahan pada media query.

Contoh Penggunaan.

## Cek Apakah User Menggunakan Dark Mode

Objek `MediaQueryList` yang dikembalikan metod `matchMedia` memiliki properti `matches` yang bernilai `true` jika dokumen sesuai dengan media query argumen.

```js
const isDarkMode = window.matchMedia('(prefers-color-scheme: dark)').matches

console.log(isDarkMode ? 'using dark mode' : 'using light mode')
```

## Memantau Perubahan Pada Ukuran Layar

Objek `MediaQueryList` yang dikembalikan metod `matchMedia` juga dapat digunakan untuk memantau perubahan pada dokumen sesuai media query argumen, dengan memberikan event listener `change` pada objek tersebut.

```js
const isMobileScreen = window.matchMedia('(max-width: 576px)')

isMobileScreen.addEventListener('change', e => {
  console.log(e.matches ? 'mobile screen' : 'desktop screen')
})
```