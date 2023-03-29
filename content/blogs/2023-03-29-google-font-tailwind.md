---
title: Menggunakan Google Font Di Tailwind
date: 2023-03-29 21:00:00 +0700
images: ['/images/blogs/google-font-tailwind/thumbnail.jpg']
---

Siapkan font dari Google Font yang akan digunakan, disini saya menggunakan `Playfair Display`.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;500;700&display=swap" rel="stylesheet">
```

Ada beberapa cara untuk menggunakan font dari google font di tailwind.

## Cara 1 : Menambahkan Font di Font Family Utility

Cara ini akan menambahkan google font di font-family utility class pada tailwind.

Untuk memulainya, buka file konfigurasi tailwind `tailwind.config.js`.

Tambahkan google font yang sudah disiapkan di `theme.fontFamily`.

```js
module.exports = {
  theme: {
    fontFamily: {
      'playfair-display': ['Playfair Display', 'serif'],
    }
  }
}
```

Untuk menggunakannya, bisa dengan menambahkan class `font-${nama-font-family}`.

```html
<h1 class="font-playfair-display">Whereas recognition of the inherent dignity</h1>
```

## Cara 2 : Extend Default Font Family

Cara ini akan menambahkan google font di default font family tailwind, default font family tailwind adalah `sans`.

Untuk memulainya, buka file konfigurasi tailwind `tailwind.config.js`.

Tambahkan google font di `theme.exted.fontFamily.sans`.

```js
import defaultTheme from 'tailwindcss/defaultTheme'

module.exports = {
  theme: {
    extend: {
      fontFamily: {
        'sans': ['Playfair Display', ...defaultTheme.fontFamily.sans],
      },
    }
  }
}
```

Secara otomatis, font default pada tailwind sudah ditambah google font.

## Cara 3 : Menggunakan Direktif Layer Base

Cara ini secara eksplisit mengatur font pada selector tertentu dengan menambahkannya di css.

Untuk memulainya, buka file css tailwind yang berisi direktif dari layer-layer utama tailwind.

Kemudian tambahkan font dari google font menggunakan properti `font-family` pada selector yang diinginkan, misal disini saya menambahkannya pada selector `html` di layer `@layer base`.

```
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  html {
    font-family: Playfair Display, system-ui, sans-serif;
  }
}
```

## Cara 4 : Menggunakan Arbitrary Value

Dengan cara ini, anda tinggal memasukan nama google-font sebagai value pada arbitrary value untuk utility class font.

```html
<p class="font-['Playfair_Display']">Whereas recognition of the inherent dignity</p>
```