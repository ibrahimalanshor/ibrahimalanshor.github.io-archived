---
title: Element vs Node Dalam DOM
date: 2023-05-13 11:00:00 +0700
images: ['/images/blogs/node-vs-element/thumbnail.jpg']
---

`Node` adalah objek yang merepresentasikan sebuah bagian / sebuah titik pada Node Tree struktur HTML, misalnya tag, teks, atribut, komentar, dll.

`Element` adalah salah satu tipe dari `Node`. Yaitu `ELEMENT_NODE` yang merepresentasikan sebuah Tag HTML.

Misalnya pada kode berikut:

```html
<div class="parent">
  <!-- Comment -->
  Text
  <p>Paragraph</p>
  <a href="#">Link</a>
</div>
```

Kalau kita bicara `Node`, maka semua bagian dari kode diatas adalah node, mulai dari tag, new line, komentar, teks, dll.

Kalai kita bicara `Element`, maka hanya ada 3 objek saja, yaitu `div`, `p` dan `a`.

---

Karena `Element` adalah salah satu tipe dari `Node`, maka objek `Element` mewarisi semua properti dan method dari `Node`.

Contohnya pada objek `Node` terdapat properti `nodeName` yang mengembalikan nama dari node tertentu. Properti tersebut dapat kita panggil dari objek `Element`.

```js
const p = document.querySelector('p')

console.log(p.nodeName)
// 'P'
```

Sedangkan objek `Node` yang bukan bertipe `Element`, tentu tidak bisa memanggil properti atau method `Element`.

Contohnya objek `document` adalah `Node` yang bukan bertipe `Element`, tapi bertipe `Document`.

Jika kita panggil properti dari `Element` misalnya `id` atau `innerHTML` pada `document`, maka akan mengembalikan `undefined`.

```js
console.log(document.id)
// undefined
console.log(document.innerHTML)
// undefined
```

Sumber:

- [https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType](https://developer.mozilla.org/en-US/docs/Web/API/Node/nodeType)
- [https://developer.mozilla.org/en-US/docs/Web/API/Element](https://developer.mozilla.org/en-US/docs/Web/API/Element)
- [https://developer.mozilla.org/en-US/docs/Web/API/Document](https://developer.mozilla.org/en-US/docs/Web/API/Document)