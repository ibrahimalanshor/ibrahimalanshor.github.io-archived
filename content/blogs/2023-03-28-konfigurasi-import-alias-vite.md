---
title: Konfigurasi Import Alias di Vite
date: 2023-03-28 17:00:00 +0700
images: ['/images/blogs/vite-import-alias/thumbnail.jpg']
---

Pernahkah anda menjumpai import file yang begitu panjang seperti kode di bawah ini?

```vue
import MyComponent from '../../../components/my-component.vue'
```

Ketika file `my-component.vue` dipindah ke direktori lain, maka semua file yang mengimpor file `my-component.vue` akan terjadi error, dan harus diubah lokasi impornya untuk mengatasi error-nya.

Untuk mengatasi kejadian tersebut, anda dapat mengkonfigurasi import alias pada vite agar tidak ada masalah ketika terjadi perubahan direktori pada file yang diimpor.

Sehingga nanti bentuk import file-nya menjadi seperti berikut.

```vue
import MyComponent from '@/components/my-component.vue'
```

Untuk melakukannya, tambahkan objek `resolve.alias` pada konfigurasi vite di file `vite.config.js`.

```js
import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';
import path from 'path';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  resolve: {
    alias: {
      '@': path.resolve('./src'),
    },
  },
});
```

Contoh diatas, `@` akan menjadi alias untuk direktori `./src`.

Anda juga dapat menambahkan alias-alias lain, contoh:

```js
import { defineConfig } from 'vite';
import vue from '@vitejs/plugin-vue';
import path from 'path';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  resolve: {
    alias: {
      '@': path.resolve('./src'),
      '@api': path.resolve('./src/api'),
      '@store': path.resolve('./src/store'),
      '@router': path.resolve('./src/router')
    },
  },
});
```

Kemudian alias-alias tersebut dapat digunakan untuk import file.

```vue
import MyComponent from '@/components/my-component.vue'
import UserApi from '@api/user.api.js'
import UserStore from '@store/user.store.js'
```