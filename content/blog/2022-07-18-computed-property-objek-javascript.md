---
layout: post
title: "Computed Property Object Javascript"
tags: [javascript]
date: 2022-07-18 19:00:00 +0700
---

Computed properti adalah properti pada objek yang nama propertinya dihasilkan dari sebuah ekspresi di dalam kurung siku `[]`.

```js
const prop1 = 'name'
const prop2 = 'age' + 4
const prop3 = 10 + 15

const user = {
  lang: 'id',
  [prop1]: 'gens',
  [prop2]: 15,
  [prop3]: 25
}

console.log(user)
// {25: 25, lang: 'id', name: 'gens', age4: 15}
```

Hal ini berlaku juga untuk method properti.

```js
const user = {
  name: 'nems',
  ['haha' + 'hihi']: () => { console.log('hahahihi') },
  'hehehoho'() { console.log('hehehoho') }
}

user.hahahihi() // hahahihi
user.hehehoho() // hehehoho
```