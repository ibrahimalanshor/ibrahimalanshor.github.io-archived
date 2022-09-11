---
title: 'Memantau Perubahan Ukuran Layar Javascript'
date: 2022-09-11 20:45:00 +0700
---

```js
const isMobileScreen = window.matchMedia('(max-width: 576px)')

isMobileScreen.addEventListener('change', e => {
  console.log(e.matches ? 'mobile screen' : 'desktop screen')
})
```