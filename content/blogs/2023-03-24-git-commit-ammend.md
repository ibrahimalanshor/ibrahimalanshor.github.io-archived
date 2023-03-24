---
title: Cara Modifikasi Commit Git Terakhir
date: 2023-03-24 17:00:00 +0700
images: ['/images/blogs/git-commit-amend/thumbnail.jpg']
---

Misalnya disini saya membuat dua file baru, `index.ts` dan `README.md`.

```bash
touch index.ts README.md
```

Kemudian saya membuat commit untuk menambahkan file `index.ts`.

```bash
git add index.ts
git commit -m "add index.ts"
# [master (root-commit) ba354a7] add index.ts
# 1 file changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 index.ts
```

Cek detil commit terbaru.

```bash
git show --name-only
# commit ba354a7a0ba048d09dbff3628ed129ab6b0932f2 (HEAD -> master)
# Author: ibra <ibrahimalanshor6@gmail.com>
# Date:   Fri Mar 24 10:55:14 2023 +0800

#     add index.ts

# index.ts
```

Ternyata saya ingin menambahkan file `README.md` di commit sebelumnya, untuk melakukannya, saya membuat commit yang mengubah commit sebelumnya dengan bantuan opsi `--amend`.

```bash
git add README.md
git commit --amend -m "add index.ts and README.md"
# [master efcfb2a] add index.ts and README.md
# Date: Fri Mar 24 10:55:14 2023 +0800
# 2 files changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 README.md
# create mode 100644 index.ts
```

Ketika dicek detil commit terbaru, pesan commit dan file yang ditambahkan berubah.

```bash
git show --name-only
# commit efcfb2a62addba3d52891dba89ba27f97349232a (HEAD -> master)
# Author: ibra <ibrahimalanshor6@gmail.com>
# Date:   Fri Mar 24 10:55:14 2023 +0800
# 
#     add index.ts and README.md
# 
# README.md
# index.ts
```

Ternyata saya ingin mengubah pesan commit sebelumnya.

Untuk melakukannya, saya membuat commit yang mengubah pesan commit sebelumnya dengan bantuan opsi `--amend`.

```bash
git commit --amend -m "initial commit"
# [master f1b17ba] initial commit
# Date: Fri Mar 24 10:55:14 2023 +0800
# 2 files changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 README.md
# create mode 100644 index.ts
```

Ketika dicek history commit, pesan commit terbaru berubah.

```bash
git log --oneline
# f1b17ba (HEAD -> master) initial commit
```

Kemudian saya menambahkan file baru `.gitignore`, dan saya ingin menambahkan file tersebut ke commit sebelumnya tanpa mengubah pesan commit sebelumnya.

Untuk melakukanya, saya membuat commit yang mengubah commit sebelumnya dengan bantuan opsi `--amend`, dengan tambahan opsi `--no-edit` untuk tidak mengubah pesan commit sebelumnya.

```bash
touch .gitignore
git add .
git commit --amend --no-edit
# [master 0c1d550] initial commit
# Date: Fri Mar 24 10:55:14 2023 +0800
# 3 files changed, 0 insertions(+), 0 deletions(-)
# create mode 100644 .gitignore
# create mode 100644 README.md
# create mode 100644 index.ts
```

Ketika dicek detil commit terbaru, tidak ada commit baru, commit sebelumnya masih sama pesannya dan file `.gitignore` berhasil ditambahkan.

```bash
git show --name-only
# commit 0c1d5508ea3c06c8d2f0f67cd3757399f0c0c1bc (HEAD -> master)
# Author: ibra <ibrahimalanshor6@gmail.com>
# Date:   Fri Mar 24 10:55:14 2023 +0800
# 
#     initial commit
# 
# .gitignore
# README.md
# index.ts
```