---
layout: post
title: "Pagination Pada Sequelize"
tags: [sequelize]
date: 2022-08-28 18:00:00 +0700
---

Pagination adalah proses membagi data menjadi beberapa halaman yang lebih kecil.

Pagination pada MySQL menggunakan dua klause, `OFFSET` dan `LIMIT`.

`OFFSET` sebagai titik awal data, dan `LIMIT` sebagai jumlah data atau titik akhirnya.

Penentuan `OFFSET` dan `LIMIT` akan dihitung berdasarkan nomor halaman dan jumlah data per halaman yang diinginkan, dengan rumus berikut.

```
limit = pageSize
offset = (pageNumber - 1) * limit
```

Implementasi pada sequelize

```js
const pageNumber = 2
const pageSize = 10

await UserModel.findAll({
  offset: (pageNumber - 1) * pageSize,
  limit: pageSize
})
```

Untuk menghindari boilerplate buat fungsi helper untuk membuat pagination.

```js
const paginate = (pageNumber, pageSize = 10) => ({
  offset: (pageNumber - 1) * pageSize,
  limit: pageSize
})
```

Fungsi tersebut akan mengembalikan objek dengan properti `offset` dan `limit`.

Gunakan fungsi helper tersebut pada objek query model sequelize.

```js
const users = await UserModel.findAll({
  where: {
    name: 'Jordan'
  },
  ...paginate(2, 20)
})

const posts = await PostModel.findAll(paginate(1))