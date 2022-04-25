---
layout: 'post'
title: 'Setup Vite Eslint Prettier Husky dan Lint Staged Untuk Project Vue'
date: 2022-04-25 10:30:00 +0700
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

## 2. Setup Eslint

Eslint adalah tool untuk membantu menganalisis, menemukan dan memperbaiki kode javascript berdasarkan aturan yang ditentukan.

```bash
npm install eslint --save-dev
npm init @eslint/config
```

## 3. Setup Prettier

Prettier adalah tool untuk memformat kode menjadi kode yang lebih konsisten berdasarkan aturan yang ditentukan.

```bash
npm install --save-dev --save-exact prettier
echo {}> .prettierrc.json
```

## 4. Setup Husky dan Lint Staged

Husky adalah tool untuk mengatur skrip yang akan dijalankan pada Git Hooks.

Lint Staged adalah tool untuk menjalankan linters hanya pada file yang berada pada fase staged git.

```bash
# Jika belum ada git pada project
git init

npx mrm@2 lint-staged
```