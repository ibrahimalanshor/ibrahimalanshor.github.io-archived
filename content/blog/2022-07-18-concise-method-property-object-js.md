---
layout: post
title: "Concise Method Object Javascript"
tags: [javascript]
date: 2022-07-18 20:30:00 +0700
---

Dalam mendefinisikan properti berupa fungsi di objek javascript anda dapat menggunakan syntax `concise method` untuk memperpendek penulisan.

Concise method dimulai dengan nama properti diikuti kurung buka, kemudian parameter jika ada, kemudian kurung tutup, kemudian kurung kurawal buka dan diakhiri dengan kurung kurawal tutup.

```js
const obj1 = {
  test() {
    console.log('test')
  }
}

obj1.test() // test
```

Berikut tidak dengan concise method.

```js
const obj1 = {
  test: function () {
    console.log('test')
  }
}

obj1.test() // test
```