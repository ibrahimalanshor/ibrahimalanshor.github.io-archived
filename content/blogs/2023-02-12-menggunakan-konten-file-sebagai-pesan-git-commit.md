---
title: Cara Menggunakan Konten File Sebagai Pesan Git Commit
date: 2023-02-12 09:30:00 +0700
---

Konten dari file dapat digunakan sebagai pesan commit, dengan menambahkan option `-F <file>` atau `--file=<file>` pada perintah `git commit`.

Contoh, saya membuat file `message.txt` berisi teks yang akan digunakan sebagai pesan commit.

```bash
echo "Pesan Commit Dari File" > message.txt
```

Kemudian file tersebut digunakan sebagai pesan commit.

```bash
git commit -aF message.txt
# [master c16e87e] Pesan Commit Dari File
# 1 file changed, 1 insertion(+), 1 deletion(-)
```

Cek log.

```bash
git log --oneline
# c16e87e (HEAD -> master) Pesan Commit Dari File
# 6b39437 Setup project
# 02f0dae init
```

Dapat dilihat, pesan commit terbaru sesuai dengan konten file `message.txt` yang sebelumnya dibuat.