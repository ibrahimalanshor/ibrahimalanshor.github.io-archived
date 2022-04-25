---
layout: 'post'
title: 'Setup Vite dan Tailwind CSS Untuk Project Vue'
date: 2022-04-25 11:30:00 +0700
---

## 1. Setup Vite

Vite adalah build tool untuk membantu pengembangan proyek aplikasi front end secara cepat dan mudah.

```bash
npm create vite@latest nama-project -- --template vue

# Masuk Ke Folder
cd nama-project

# Install Depedensi
npm install
```

## 2. Setup Tailwind CSS

Install tailwind dan beberapa tool lain, kemudian buat konfigurasi tailwindcss.

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

## 3. Konfigurasi Path Template

Buka file `tailwind.config.js`, isi content dengan path file yang menggunakan tailwind.

```js
module.exports = {
  content: [
    "./index.html",
    "./src/**/*.{vue,js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## 4. Buat File Tailwind

Buat file di `src/assets/css/style.css`, isi dengan konten berikut.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## 5. Tambahkan Pada Aplikasi Vue

Buka file `main.js`, impor file tailwind.

```js
import { createApp } from 'vue'
import App from './App.vue'
import './assets/css/style.css'

createApp(App).mount('#app')
``` 