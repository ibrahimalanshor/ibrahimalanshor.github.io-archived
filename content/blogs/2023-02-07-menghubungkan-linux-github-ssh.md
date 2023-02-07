---
title: Menghubungkan Linux Ke Akun Github Dengan SSH Key
date: 2023-02-07 18:30:00 +0700
---

Dengan SSH Key, menghubungkan komputer linuk ke akun github menjadi lebih mudah karena tidak perlu memasukkan username dan password setiap kali melakukan push, pull, clone dll.

SSH Key adalah kunci yang digunakan komputer untuk berkomunikasi ke komputer lain dalam hal ini server github melalui protokol SSH. SSH Key terdiri dari __public key__ dan __private key__

Public key disimpan di server Github, Private key disimpan di komputer lokal

## Cek Apakah Sudah Ada SSH Key

Sebelum membuat SSH Key baru, cek terlebih dahulu di komputer lokal apakah sudah ada key yang sudah dibuat sebelumnya.

SSH Key yang sudah dibuat secara default disimpan di direktori `~.ssh`.

```bash
ls -al ~/.ssh
```

Jika ada file `id_xxx.pub` di direktori tersebut maka sudah ada SSH Key yang sudah dibuat sebelumnya, anda bisa menggunakanya untuk menghubungkan ke github akun anda.

Jika belum ada, ikuti langkah selanjutnya untuk membuatnya.

## Membuat SSH Key

Untuk membuat SSH Key baru, gunakan perintah `ssh-keygen`

```bash
ssh-keygen -t ed25519 -C "email@email.com"
```

Ikuti *prompt*-nya, pada saat pengisian `passphare` anda bebas boleh mengisi atau tidak.

Cek di direktori `~/.ssh` untuk melihat SSH Key yang dibuat.

Tambahkan SSH Key yang sudah dibuat ke `ssh-agent` dengan perintah `ssh-add`.

```bash
ssh-add ~/.ssh/id_ed25519
```

Ubah `id_ed25519` sesuai dengan file SSH Key yang dibuat.

## Menambahkan SSH Key ke Akun Github

Salin isi file SSH Key yang sudah dibuat, bisa dengan perintah `cat` untuk menampilkan isinya.

```bash
cat ~/.ssh/id_ed25519
```

Buka akun github anda > Settings > SSH and GPG keys > [New SSH Key](https://github.com/settings/ssh/new).

![Github New SSH Key](/images/blogs/github-new-ssh-key.png)

Kolom `Title` bebas diisi apa saja, misal nama komputer.

Tempelkan isi file SSH Key yang sudah disalin sebelumnya di kolom `Key`.

Kemudian klik tombol __Add SSH Key__.

## Uji Coba SSH Key

Cek apakah ssh key sudah terhubung ke akun github dengan perintah berikut.

```bash
ssh -T git@github.com
# Hi ibrahimalanshor! You've successfully authenticated, but GitHub does not provide shell access.
```

Jika muncul pesan tersebut, komputer anda sudah terhubung dengan akun github.