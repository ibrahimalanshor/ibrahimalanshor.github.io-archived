---
layout: post
title: "Setup Eslint Prettier Husky dan Lint Staged"
tags: [setup]
date: 2022-05-07 11:00:00 +0700
---

Eslint Prettier Husky dan Lint Staged membantu programmer untuk menciptakan kode javascript yang konsisten dan sesuai aturan dengan mudah secara otomatis.

## 1. Setup Eslint

Eslint adalah tool untuk membantu menganalisis, menemukan dan memperbaiki kode javascript berdasarkan aturan yang ditentukan.

```bash
npm install eslint --save-dev
npm init @eslint/config
```

## 2. Setup Prettier

Prettier adalah tool untuk memformat kode menjadi kode yang lebih konsisten berdasarkan aturan yang ditentukan.

```bash
npm install --save-dev --save-exact prettier
echo {}> .prettierrc.json
```

## 3. Setup Husky dan Lint Staged

Husky adalah tool untuk mengatur skrip yang akan dijalankan pada Git Hooks.

Lint Staged adalah tool untuk menjalankan linters hanya pada file yang berada pada fase staged git.

```bash
# Jika belum ada git pada project
git init

npx mrm@2 lint-staged
```