---
title: 'Debounce'
date: 2022-08-29 01:00:00 +0700
---

```js
const debounce = (func, wait = 500) => {
  let timeout;

  return (...args) => {
    clearTimeout(timeout);

    timeout = setTimeout(() => func.apply(this, args), wait);
  };
};

const greetDebounce = debounce(() => console.log('hello'))

greetDebounce() // hello after wait 500 millisecond
```