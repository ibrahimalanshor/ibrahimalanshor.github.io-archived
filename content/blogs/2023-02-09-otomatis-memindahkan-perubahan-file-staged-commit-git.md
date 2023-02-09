---
title: Cara Otomatis Memindahkan Perubahan File Ke Staged Pada Saat Commit Git
date: 2023-02-09 20:00:00 +0700
---

Git commit dapat otomatis memindahkan perubahan file ke staged tanpa perlu melakukan `git add` terlebih dahulu, dengan cara menambahkan *option* `-a` atau `--all` pada perintah `git commit`.

Misal ada perubahan di file `readme.md` dan `LICENSE`, kemudian ingin dicommit.

Tanpa perlu melakukan `git add readme.md LICENSE`, anda dapat langsung memindahkan perubahan tersebut ke staged sekaligus melakukan commit dengan menambahkan option `a` pada saat `git commit`.

```bash
git commit -am "update readme and license"
```
> File yang otomatis dipindahkan ke staged adalah file yang diperbarui atau dihapus, file yang baru ditambahkan harus manual dengan perintah `git add`