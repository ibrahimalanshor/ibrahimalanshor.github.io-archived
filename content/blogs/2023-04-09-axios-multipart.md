---
title: Axios Multipart Body
date: 2023-04-09 13:30:00 +0700
images: ['/images/blogs/axios-multipart/thumbnail.jpg']
---

Multipart adalah salah satu *encoding_types* yang memungkinkan untuk menambah file pada body request yang akan dikirimkan ke server.

Untuk mengirimkan request dengan multipart pada axios, ada dua cara yang dapat digunakan.

## FormData Object

Cara pertama adalah dengan membuat `FormData` objek melalui `FormData` constructor, kemudian tambahkan key/field beserta file yang akan dikirim menggunakan method `apppend`.

Contoh.

```js
const fileInput = document.querySelector('[type=file]')
const formData = new FormData()

formData.append('file', fileInput.files[0])

axios.post('https://example.com', formData)
```

Hasilnya

![FormData Object](/images/blogs/axios-multipart/form-data-object.png)

## postForm Method

Cara kedua adalah dengan menggunakan `postForm` method pada axios, dengan cara ini anda tidak perlu membuat `FormData` objek karena karena body yang akan dikirimkan akan secara otomatis di-*serialize* oleh internal axios serializer

Contoh.

```js
const fileInput = document.querySelector('[type=file]')

axios.postForm('https://example.com', {
  file: fileInput.files[0]
})
```

Hasilnya.

![Post Form Method](/images/blogs/axios-multipart/post-form-method.png)

Request body yang dihasilkan sama seperti menggunakan `FormData` objek pada cara pertama.
