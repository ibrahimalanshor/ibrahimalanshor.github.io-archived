---
layout: post
title: "xdg-open Linux"
tags: [linux]
date: 2022-05-22 19:00:00 +0700
---

xdg-open merupakan salah satu tool yang didapatkan dari xdg-utils.

xdg-open digunakan untuk membuka url atau file dengan aplikasi default sistem.

Jika argumen yang dikirimkan adalah url, maka xdg-open akan membuka url tersebut browser default sistem.

Jika argumen yang dikirimkan adalah file atau folder, maka xdg-open akan membuka file atau folder tersebut di aplikasi yang sesuai.

Dibuka di browser.

```bash
xdg-open "https://google.com"
```

Dibuka di aplikasi yang sesuai contohnya sublime text.

```bash
xdg-open note.txt
```

Dibuka di file explorer.

```bash
xdg-open Documents/
```