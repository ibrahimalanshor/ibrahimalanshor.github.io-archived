---
layout: post
title: "Komunikasi Antar Komponen Vue 3 dengan Mitt"
tags: [vue]
date: 2022-06-22 20:30:00 +0700
---

Untuk berkomunikasi antar komponen vue 3, anda dapat menggunakan library [mitt](https://github.com/developit/mitt).

## Install

```bash
npm install --save mitt
```

## Tambahkan Mitt Ke Main Vue

```js
import { createApp } from 'vue';
import App from './App.vue';
// Import Mitt
import mitt from 'mitt';

const app = createApp(App);
// Inisialisasi mitt
const emitter = mitt();

// Provide mitt agar dapat digunakan di componen di bawahnya
app.provide('emitter', emitter);
app.mount('#app');
```

## Kirim Pesan ke Komponen Lain

```vue
<!-- src/Form.vue -->
<template>
  <!-- template -->
</template>

<script setup>
// Inject Emitter
import { inject } from 'vue'
const emitter = inject('emitter')

// Kirim Pesan
emitter.emit('alert', { msg: 'hello' })
</script>
```

## Terima Pesan di Komponen Lain

```vue
<!-- src/Table.vue -->
<template>
  <!-- template -->
</template>

<script setup>
// Inject Emitter
import { inject } from 'vue'
const emitter = inject('emitter')

// Terima Pesan
emitter.on('alert', (e) => {
  console.log(e.msg)
})
</script>
```