---
layout: post
title: "Perintah mkdir Multi Direktori dengan Subdirektorinya"
tags: [bash, terminal, cli, linux]
date: 2022-07-16 20:50:00 +0700
---

Gunakan opsi `-p` untuk membuat direktori induknya jika belum ada.

Gunkaan kurung kurawal `{}` untuk membuat multi direktori.

```bash
mkdir -p src/{controllers,models,routes}/test
```

Untuk memastikannya tambahkan opsi `-v` untuk melihat setiap direktori yang dibuat.

```bash
mkdir -p -v src/{controllers,models,routes}/test

# mkdir: created directory 'src'
# mkdir: created directory 'src/controllers'
# mkdir: created directory 'src/controllers/test'
# mkdir: created directory 'src/models'
# mkdir: created directory 'src/models/test'
# mkdir: created directory 'src/routes'
# mkdir: created directory 'src/routes/test'
```