---
layout: post
title: "Mempermanenkan Pinia State"
tags: [vue, pinia]
date: 2022-08-21 19:00:00 +0700
---

Terkadang ada beberapa situasi yang mengharuskan sebuah state pinia harus permanen, contohnya token jwt yang disimpan di state pinia.

Agar token tersebut tidak hilang ketika halaman di _refresh_, maka state token tersebut harus dipermanenkan, contohnya di `localStorage`.

Untuk melakukannya anda dapat menggunakan plugin [pinia-plugin-persistedstate](https://github.com/prazdevs/pinia-plugin-persistedstate).

Caranya sangat mudah, pertama instal plugin tersebut.

```bash
npm i pinia-plugin-persistedstate
```

> Pastikan anda sudah menginstal pinia.

Kemudian impor dan gunakan plugin tersebut pada pinia.

```js
import { createPinia } from 'pinia'
import piniaPluginPersistedstate from 'pinia-plugin-persistedstate'

const pinia = createPinia()
pinia.use(piniaPluginPersistedstate)
```

Kemudian pilih state yang akan dipermanenkan, tambahkan properti `persist` dengan nilai true untuk mempermanenkan state tersebut.

Contoh disini saya akan mempermanenkan state `auth`.

```js
import { defineStore } from 'pinia'

export const useAuth = defineStore('auth', {
  state: () => ({
    token: 'secret'
  }),
  persist: true,
})
```

Secara default plugin ini akan menyimpan state di `localStorage`, anda juga dapat memodifikasinya sesuai kebutuhan anda. Caranya bisa dilihat di [dokumentasi plugin ini](https://prazdevs.github.io/pinia-plugin-persistedstate/guide/config.html)