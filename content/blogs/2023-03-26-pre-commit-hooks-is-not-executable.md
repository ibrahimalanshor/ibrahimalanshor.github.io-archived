---
title: Mengatasi husky pre-commit hook was ignored because it's not set as executable.
date: 2023-03-26 18:00:00 +0700
images: ['/images/blogs/husky-ignored/thumbnail.jpg']
---

Jika husky `pre-commit` hook tidak dapat dijalankan, maka skrip husky tersebut akan di-ignore dan muncul pesan warning berikut.

```bash
hint: The '.husky/pre-commit' hook was ignored because it's not set as executable.
hint: You can disable this warning with git config advice.ignoredHook false.
```

Solusinya jalankan perintah berikut, agar `husky/pre-commit` hook dapat dijalankan.

```bash
chmod ug+x .husky/*
chmod ug+x .git/hooks/*
```