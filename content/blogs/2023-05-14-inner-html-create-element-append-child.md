---
title: innerHTML vs createElement appendChild Untuk Menambahkan Child Element
date: 2023-05-14 11:00:00 +0700
images: ['/images/blogs/inner-html-vs-append-child/thumbnail.jpg']
---

Untuk menambahkan child element ke element tertentu, anda dapat menggunakan properti `innerHTML` atau menggunakan method `appendChild`.

---

## Contoh Penggunaan

Jika menggunakan `innerHTML`, anda tinggal memasukkan string HTML yang akan ditambahkan, contoh:

```js
const container = document.querySelector('.container')

container.innerHTML = `<p>Hello world</p>`
```

Sedangkan untuk menggunakan `appendChild`, anda perlu membuat child element menggunakan `createElement`, contoh:

```js
const container = document.querySelector('.container')

const p = document.createElement('p')
p.textContent = 'Hello world'

container.appendChild(p)
```

---

## Perbandingan

Secara kemudahan, penggunaan `innerHTML` dinilai lebih mudah, karena child element yang ditambahkan sudah dalam bentuk string html utuh tanpa perlu melakukan manipulasi tertentu, contohnya.

```js
const container = document.querySelector('.container')

container.innerHTML = `<input
    id="email"
    type="email"
    name="email"
    placeholder="Email"
    autofocus
    required
/>`
```

Sedangkan jika menggunakan `createElement`, mungkin akan lebih sulit jika belum memahami bagaimana memanipulasi suatu element, contohnya.

```js
const container = document.querySelector('.container')

const input = document.createElement('input')
input.id = 'email'
input.type = 'email'
input.name = 'email'
input.placeholder = 'Email'
input.autofocus = true
input.required = true

container.appendChild(input)
```

Secara pefrorma, `innerHTML` dinilai lebih tidak efisien karena akan melakukan parse ulang dan membuat ulang semua DOM Node didalam element tersebut.

Sedangkan `appendChild` hanya akan menambahkan child element ke Node Tree dari element tersebut.

Referensi:

- [https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)
- [https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)
- [https://www.javascripttutorial.net/javascript-dom/javascript-innerhtml-vs-createelement/](https://www.javascripttutorial.net/javascript-dom/javascript-innerhtml-vs-createelement/)
- [https://medium.com/@kevinchi118/innerhtml-vs-createelement-appendchild-3da39275a694](https://medium.com/@kevinchi118/innerhtml-vs-createelement-appendchild-3da39275a694)
- [https://www.measurethat.net/Benchmarks/Show/10096/0/createelement-vs-clonenode-vs-innerhtml](https://www.measurethat.net/Benchmarks/Show/10096/0/createelement-vs-clonenode-vs-innerhtml)