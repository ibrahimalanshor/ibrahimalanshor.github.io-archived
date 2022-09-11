---
title: 'Cek Apakah Sebuah Objek Javascript'
date: 2022-09-01 20:00:00 +0700
---

```js
const isObject = value => typeof value === 'object' && value !== null && !Array.isArray(value)

// Alternative 

const isObject = value => Object.prototype.toString.call(value) === '[object Object]'

// Test

isObject({}) // true
isObject({ a: 'b' }) // true
isObject('string') // false
isObject(12) // false
isObject(null) // false
isObject([]) // false
```