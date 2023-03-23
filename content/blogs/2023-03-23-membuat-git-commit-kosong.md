---
title: Cara Membuat Git Commit Kosong
date: 2023-03-23 20:00:00 +0700
images: ['/images/blogs/allow-empty-commit/thumbnail.jpg']
---

Misalnya disini tidak ada perubahan pada working tree.

```bash
git status
# On branch master
# nothing to commit, working tree clean
```

Kemudian saya ingin membuat commit kosong, misal untuk men-trigger build.

```bash
git commit -m "trigger build"
# On branch master
# nothing to commit, working tree clean
```

Ketika dicek di history log, karena tidak ada perubahan, commit diatas tidak masuk.

```bash
git log --oneline
# 05dc52b (HEAD -> master) add more files
# b66428b add files
# aac5ffa add files
```

Daripada saya membuat perubahan yang tidak perlu, saya bisa menambahkan opsi `--allow-empty` untuk membuat commit kosong.

```bash
git commit --allow-empty -m "trigger build"
```

Ketika dicek di history log, commit diatas akan masuk.

```bash
git log --oneline
# 42b2568 (HEAD -> master) trigger build
# 05dc52b add more files
# b66428b add files
# aac5ffa add files
```

Kemudian saya push ke remote, dan akan mentrigger build karena ada commit baru

```bash
git push origin master
```