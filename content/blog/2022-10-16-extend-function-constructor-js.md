---
layout: post
title: "Extend Function Constructor Javascript"
tags: [js]
date: 2022-10-16 18:30:00 +0700
---

Function Constructor adalah fungsi untuk mengkonstruksi sebuah objek pada javascript.

```js
function User(name) {
  this.name = name
}

User.prototype.greet = function () {
  console.log(`Hello, i am ${this.name}`)
}

const adam = new User('adam')

console.log(adam) // User {name: 'adam'}
adam.greet() // Hello i am adam
```

Untuk melakukan extend pada function constructor anda dapat melakuan beberapa langkah berikut.

Misalnya disini saya membuat sebuah function constructor baru `Admin`.

```js
function Admin(name) {}
```

`Admin` adalah sub-class dari `User`, untuk itu `Admin` perlu extend pada `User`, langkah pertama panggil `User` di dalam `Admin` menggunakan method `call`.

```js
function Admin(name) {
  User.call(this, name)
}
```

Mari coba membuat sebuah admin.

```js
const henri = new Admin('henri')

console.log(henri) // Admin {name: 'henri'}
```

Dapat diperhatikan objek `henri` yang dibuat dari function `Admin` sudah memiliki properti `name` seperti pada `User`.

Mari coba panggil method `greet` pada objek `henri`.

```js
const henri = new Admin('henri')

console.log(henri) // Admin {name: 'henri'}
henri.greet() // Uncaught TypeError: henri.greet is not a function
```

Error karena pada objek `henri` maupun pada `Admin` belum terdapat method `greet`, untuk mengatasinya, atur prototype `Admin` menjadi mewarisi protoype user `User`.

```js
function User(name) {
  this.name = name
}

User.prototype.greet = function () {
  console.log(`Hello, i am ${this.name}`)
}

function Admin(name) {
  User.call(this, name)
}

Admin.prototype = Object.create(User.prototype, {
  constructor: {
    value: Admin
  }
})
```

Mari kita coba panggil method `greet` pada objek `henri`.

```js
const henri = new Admin('henri')

console.log(henri) // Admin {name: 'henri'}
henri.greet() // Hello, i am henri
```

## Kode Akhir.

```js
function User(name) {
  this.name = name
}

User.prototype.greet = function () {
  console.log(`Hello, i am ${this.name}`)
}

function Admin(name) {
  User.call(this, name)
}

Admin.prototype = Object.create(User.prototype, {
  constructor: {
    value: Admin
  }
})
```