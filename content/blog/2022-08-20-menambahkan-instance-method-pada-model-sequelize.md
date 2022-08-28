---
layout: post
title: "Menambahkan Instance Method Pada Model Sequelize"
tags: [sequelize]
date: 2022-08-20 19:30:00 +0700
---

Ada beberapa cara untuk menambahkan instance method anda pada model sequelize.

Method tersebut dapat dipanggil dari objek hasil dari query model sequelize.

## 1. Melalui Object Prototype

Cara pertama untuk menambahkan instance method adalah melalui object prototype.

Contohnya disini saya menambahkan method `myCoolMethod` pada model `User`.

```js
const User = sequelize.define('User', {
  name: DataTypes.STRING
})

User.prototype.myCoolMethod = function () {
  console.log(`${this.name} is so cool`)
}
```

Selanjutnya saya dapat memanggil method tersebut pada objek hasil query model `User`.

```js
const user = await User.findOne({ where: { name: 'Admin' } })

if (!user) throw new Error('user not found')

user.myCoolMethod() // Admin is so cool
```

## 2. Melalui ES6 Class

Model pada sequelize dapat didefinisikan menggunakan es6 class dengan meng-extend Sequelize Model.

Anda dapat menambahkan instance method pada class tersebut.

Contohnya disini saya menambahkan method `myCoolMethod` pada model `User`.

```js
class User extends Model {
  myCoolMethod() {
    console.log(`${this.name} is so cool`)
  }
}

User.init({
  name: DataTypes.STRING
})
```

Selanjutnya saya dapat memanggil method tersebut pada objek hasil query model `User`.

```js
const user = await User.findOne({ where: { name: 'Admin' } })

if (!user) throw new Error('user not found')

user.myCoolMethod() // Admin is so cool
```