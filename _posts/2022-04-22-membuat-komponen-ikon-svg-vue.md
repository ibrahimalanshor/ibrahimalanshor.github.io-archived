---
layout: 'post'
title: 'Membuat Komponen Ikon SVG Vue'
date: 2022-04-22 09:45:00 +0700
---

Ikon merupakan salah satu komponen penting pada sebuah website.

[https://heroicons.com/](https://heroicons.com/) menyediakan berbagai macam ikon svg yang dapat digunakan secara gratis.

Untuk menggunakannya pada Vue anda dapat membuat komponen agar lebih mudah menggunakannnya.

Contoh Archive.vue

```html
<template>
  <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
    <path stroke-linecap="round" stroke-linejoin="round" d="M5 8h14M5 8a2 2 0 110-4h14a2 2 0 110 4M5 8v10a2 2 0 002 2h10a2 2 0 002-2V8m-9 4h4" />
  </svg>
</template>
```

Gunakan.

```html
<template>
  <div>
    <Archive />
  </div>
</template>

<script setup>
import Archive from './Archive.vue'
</script>
```