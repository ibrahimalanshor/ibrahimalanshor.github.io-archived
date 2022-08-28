---
layout: post
title: "Function vs Method pada Javascript"
tags: [javascript]
date: 2022-07-18 20:50:00 +0700
---

Function atau fungsi adalah blok kode yang digunakan untuk melakukan sebuah aksi tertentu, method adalah fungsi yang didefinisikan sebagai properti dari sebuah objek.

```js
// fungsi
function test() {
  console.log('test')
}

// method
const obj = {
  test() {
    console.log('test')
  }
}

test() // test
obj.test() // test
```