---
layout: post
title: "Javascript Call Apply Bind"
tags: [javascript]
date: 2022-08-20 20:30:00 +0700
---

Method pada objek dapat memanggil objeknya sendiri dengan kata kunci `this`.

```js
const user = {
  name: 'helmi',
  whoami() {
    console.log(`you are ${this.name}`)
  }
}

user.whoami() // you are helmi
```

Jika properti `name` diubah nilainya, hasil pemanggilan method pun berubah sesuai konteks `this`-nya.

```js
user.name = 'valen'
user.whoami() // you are valen
```

Saya juga dapat mengubah konteks `this` pada pemanggilan method `whoami` tanpa mengubah nilai properti `name`, dengan method `call` atau `apply`.

```js
user.whoami.call({ name: 'binder' }) // you are binder
user.whoami.apply({ name: 'justin' }) // you are justin
user.whoami() // you are valen
```

Akan muncul masalah jika saya menggunakan method `whoami` seperti ini.

```js
setTimeout(user.whoami, 1000) // you are 
```

`name` nya menjadi kosong, karena pada pemanggilan method `whoami` di `setTimeout`, konteks `this` pada method tersebut mengarah pada objek global `window` bukan pada objek `user`.

Contoh saya tambahkan properti `name` pada window dan saya ulangi kode diatas.

```js
window.name = 'sukri'

setTimeout(user.whoami, 1000) // you are sukri
```

Untuk mengatasi agar pemanggilan method `whoami` mengarah pada objek `user`, gunakan method `bind`

```js
setTimeout(user.whoami.bind(user), 1000) // you are valen
```

Bagaimana jika pada method tersebut terdapat parameter? Contoh.

```js
const club = {
  name: 'chelsea',
  play(opp) {
    console.log(`${this.name} vs ${opp}`)
  }
}

club.play('arsenal') // chelsea vs arsenal
```

Kemudian saya mengganti konteks `this` menjadi yang lain.

```js
club.play.call({ name: 'man city' }) // man city vs undefined
club.play.apply({ name: 'man united' }) // man united vs undefined
```

Menjadi `undefined` karena pada method `call` dan `apply` saya tidak mengirimkan argumen yang dibutuhkan.

Pada `call` kirim argumen setelah konteks `this` setiap argumennya.

Pada `apply` kirim argumen setelah konteks `this` setiap argumennya dalam bentuk array.

```js
club.play.call({ name: 'man city' }, 'liverpool') // man city vs liverpool
club.play.apply({ name: 'man united' }, ['totenham']) // man united vs totenham
```

Untuk `bind` cara pengiriman argumennya sama seperti `call`.

```js
setTimeout(club.play.bind(club, 'west ham'), 1000) // chelsea vs west ham
```