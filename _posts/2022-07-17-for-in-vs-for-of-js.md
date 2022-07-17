---
layout: post
title: "For In vs For Of Javascript"
tags: [js]
date: 2022-07-17 20:30:00 +0700
---

`for ... in` dan `for ... of` merupakan dua cara untuk melakukan perulangan objek di js.

## For In

`for in` melakukan perulangan setiap properti yang bersifat `enumerable` pada objek.

> `enumerable` adalah atribut internal pada properti objek yang menentukan apakah properti tersebut disertakan di perulangan `for in` atau di method `Object.keys()`.

```js
const user = {
  name: 'sun',
  age: 15,
}

user.lang = 'id'

for (const key in user) {
  console.log(key)
}
// name, age, lang
```

Properti yang dibuat dengan object literal atau lewat assigment secara default bersifat `enumerable`.

Jika properti objek tidak `enumerable`, key properti tersebut tidak disertakan di perulangan `for in`.

```js
const user = { name: 'sun', password: 'sunsunsun', age: 15 }

Object.defineProperty(user, 'password', {
  enumerable: false
})

for (const key in user) {
  console.log(key)
}
// name, age
```

Hal ini berlaku untuk array juga.

```js
const users = ['sun', 'gogs', 'ving']

for (const key in users) {
  console.log(key)
}
// 0, 1, 2
```

## For Of

`for of` melakukan perulangan setiap properti pada objek yang bersifat `iterable`.

> Sebuah objek yang `iterable` harus memiliki properti `[Symbol.iterator]`, seperti Array, Map, dsb.

```js
const users = ['sun', 'gogs', 'ving']

for (const user of users) {
  console.log(user)
}
// sun, gogs, ving
```

String juga `iterable`.

```js
const name = 'vingke'

for (const char of name) {
  console.log(char)
}
// v, i, n, g, k, e
```

Objek yang tidak memilik properti `[Symbol.iterator]` bukanlah `iterable` dan tidak dapat dilakukan `for in`.

```js
const user = {
  name: 'vingke',
  age: 15
}

for (const data of user) {
  console.log(data)
}
// Uncaught TypeError: user is not iterable
```