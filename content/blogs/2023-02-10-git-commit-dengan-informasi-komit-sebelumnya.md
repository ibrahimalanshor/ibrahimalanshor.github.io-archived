---
title: Cara Membuat Git Commit Dengan Informasi Dari Commit Sebelumnya
date: 2023-02-10 18:30:00 +0700
---

Informasi commit sebelumnya dapat digunakan kembali ketika ingin membuat commit, dengan menambahkan option `-C <commit>` atau `--reuse-messsage=<commit>` pada perintah `git commit`.

Berikut contoh log git yang sudah ada:

```bash
git log --pretty=format:"%h %ah | %s [%an]"
```

```bash
# 7b0cb4c 25 minutes ago | Install pkg [ibra]
# 94358ab 26 minutes ago | Setup project [ibra]
# 55153d5 26 minutes ago | Add License [ibra]
# 85fb35c 27 minutes ago | Add readme [ibra]
```

Kemudian saya melakukan perubahan, dan ingin melakukan commit dengan informasi yang sama dengan commit `94358ab`.

```bash
git commit -aC 94358ab
```

Kemudian cek log.

```bash
git log --pretty=format:"%h %ah | %s [%an]"
```

```bash
# 4f9b5e0 26 minutes ago | Setup project [ibra]
# 7b0cb4c 26 minutes ago | Install pkg [ibra]
# 94358ab 26 minutes ago | Setup project [ibra]
# 55153d5 27 minutes ago | Add License [ibra]
# 85fb35c 27 minutes ago | Add readme [ibra]
```

Dapat dilihat commit terbaru `4f9b5e0` memiliki informasi commit yang sama dengan commit `94358ab`.

Jika anda ingin menggunakan informasi sebelumnya tapi ingin mengubah pesan commitnya, anda bisa gunakan option `-c <commit>` atau `--reedit-message=<commit>`.

```bash
git commit -ac 94358ab
```

Akan muncul editor untuk mengubah pesan commit sebelumnya.

![Git Commit -c](/images/blogs/git-commit-c.png)

Cek log.

```bash
git log --pretty=format:"%h %ah | %s [%an]"
```

```bash
# 6b39437 26 minutes ago | Setup project again [ibra]
# 4f9b5e0 26 minutes ago | Setup project [ibra]
# 7b0cb4c 26 minutes ago | Install pkg [ibra]
# 94358ab 26 minutes ago | Setup project [ibra]
# 55153d5 27 minutes ago | Add License [ibra]
# 85fb35c 27 minutes ago | Add readme [ibra]
```