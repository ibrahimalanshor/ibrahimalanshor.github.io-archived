---
title: Cara Skip Git Commit Hooks
date: 2023-03-22 17:00:00 +0700
images: ['/images/blogs/skip-commit-hooks/thumbnail.jpg']
---

Tambahkan opsi `--no-verify` pada saat melakukan commit agar tidak menjalankan `pre-commit` dan `commit-msg` hook.

```bash
git commit --no-verify -m "message"
```

Untuk lebih singkat anda juga dapat menggunakan opsi `-n` saja.

```bash
git commit -nm "message"
```

Opsi `--no-verify` juga dapat digunakan di `pre-push` hooks, `pre-merge` hooks, `pre-rebase` hooks, dsb.

```bash
git push --no-verify
```

Referensi:

- [https://git-scm.com/docs/githooks](https://git-scm.com/docs/githooks)
- [https://adamj.eu/tech/2023/02/13/git-skip-hooks/](https://adamj.eu/tech/2023/02/13/git-skip-hooks/)
- [https://bobbyhadz.com/blog/git-commit-skip-hooks](https://bobbyhadz.com/blog/git-commit-skip-hooks)