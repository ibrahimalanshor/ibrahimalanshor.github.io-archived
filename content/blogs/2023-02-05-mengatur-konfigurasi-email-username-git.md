---
title: Mengatur Konfigurasi Email dan Username Git
date: 2023-02-05 12:00:00 +0700
---

Konfigurasi email dan username git berguna untuk mengidentifikasi author yang melakukan commit pada repository git.

Jika anda menggunakan `github` anda perlu menyesuaikan konfigurasi email git pada komputer anda agar commit yang anda lakukan dapat terhubung ke akun github anda.

Untuk melakukan konfigurasi email dan username git, jalankan perintah `git config user.email` dan `git config user.name` pada repository git.

```bash
git config user.email "jhon@email.com"
git config user.name "jhon"
```

Untuk mengetes apakah berhasil, jalankan perintah `git config user.name` dan `git config user.name`.

```bash
git config user.email
# jhon.gmail.com
git config user.name
# jhon
```

## Konfigurasi Global

Perintah konfigurasi sebelumnya hanya berlaku untuk repository saja, untuk mengatur konfigurasi email dan password global, tambahkan option `--global` pada perintah git config.

```bash
git config --global user.email "jhon@email.com"
git config --global user.name "jhon"
```

Untuk mengetes apakah berhasil, jalankan perintah `git config --global user.name` dan `git config --global user.name`.

```bash
git config --global user.email
# jhon.gmail.com
git config --global user.name
# jhon
```