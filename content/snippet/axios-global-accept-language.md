---
title: 'Mengatur Header Accept-Language Secara Global Berdasarkan Bahasa Browser User'
date: 2022-09-01 20:00:00 +0700
---

```js
import axios from 'axios'

axios.global.headers.common['Accept-Language'] = window.navigator.language
```