---
title: Setup Eslint Prettier Husky dan Lint Staged
date: 2023-03-25 16:00:00 +0700
images: ['/images/blogs/setup-linter/thumbnail.jpg']
---

## 1. Setup Eslint

Eslint adalah tool untuk membantu menganalisis, menemukan dan memperbaiki kode javascript.

```bash
npm install eslint --save-dev
npm init @eslint/config
```

## 2. Setup Prettier

Prettier adalah tool untuk memformat kode javascript menjadi menjadi lebih rapi dan konsisten.

```bash
npm install --save-dev --save-exact prettier
echo {}> .prettierrc.json
```

## 3. Setup Husky dan Lint Staged

Husky adalah tool untuk mengatur skrip yang akan dijalankan pada Git Hooks.

Lint Staged adalah tool untuk menjalankan task linters hanya pada file yang berada pada fase staged git.

```bash
git init
npx mrm@2 lint-staged
```