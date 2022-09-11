---
title: 'Cek Apakah User Menggunakan Dark Mode Javascript'
date: 2022-09-11 20:30:00 +0700
---

```js
const isDarkMode = window.matchMedia('(prefers-color-scheme: dark)').matches

console.log(isDarkMode ? 'using dark mode' : 'using light mode')
```