---
layout: post
title: "Cara Menambahkan Waktu Kadaluarsa Pada Document Mongoose"
tags: [mongoose]
date: 2022-07-12 21:20:00 +0700
---

`expires` options pada schema date mongoose dapat anda gunakan untuk menambahkan waktu kadaluarsa pada document.

```js
const { Schema } = require('mongoose')

const schema = new Schema({
  expireAt: {
    type: Date,
    default: Date.now,
    expires: 60
  }
});
```

Setelah 60 detik dibuat, document akan kadaluarsa.

[https://mongoosejs.com/docs/api.html#schemadateoptions_SchemaDateOptions-expires](https://mongoosejs.com/docs/api.html#schemadateoptions_SchemaDateOptions-expires)