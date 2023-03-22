---
title: Cara Membuat Commit Dengan Author Yang Berbeda
date: 2023-02-13 19:30:00 +0700
---

Secara default author dari commit adalah yang diatur pada `git config user.name` dan `git config user.email`.

Contoh berikut configurasi git config user saya.

```bash
git config user.name
# ibrahimalanshor
git config user.email
# ibrahimalanshor6@gmail.com
```

Ketika melakukan commit.

```bash
git commit -am "add files"
# [master b66428b] add files
# 1 file changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 file.txt
```

```bash
git show b66428b --pretty=format:"%an %ae"
# ibrahimalanshor ibrahimalanshor6@gmail.com
# more...
```

Author pada commit yang dibuat sesuai dengan git config user.

Untuk mengubah author pada saat melakukan commit, tambahkan option `--author` diikuti argumen authornya dengan format `name <email>`.

```bash
git commit --author="kiwi <kiwi@gmail.com>" -m "add more files"
# [master c354890] add more files
# Author: kiwi <kiwi@gmail.com>
# 1 file changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 yes.txt
```

```bash
git show c354890 --pretty=format:"%an %ae"
# kiwi kiwi@gmail.com
# more...
```