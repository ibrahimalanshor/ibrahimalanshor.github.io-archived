---
title: 'Paginate'
date: 2022-08-29 00:00:00 +0700
---

```js
const paginate = (pageNumber, pageSize = 10) => ({
  offset: (pageNumber - 1) * pageSize,
  limit: pageSize
})

paginate(1) // { offset: 0, limit: 10 }
paginate(3, 20) // { offset: 40, limit: 20 }
```