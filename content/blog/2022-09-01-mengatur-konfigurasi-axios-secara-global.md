---
layout: post
title: "Mengatur Konfigurasi Axios Secara Global"
tags: [javascript]
date: 2022-09-01 20:00:00 +0700
---

Ada beberapa konfigurasi axios yang mungkin akan diaplikasikan di setiap request axios, contohnya header `Content-Type` yang selalu `application/vnd.api+json` atau `Accept-Language` berdasarkan bahasa browser pengguna.

Agar tidak mengaturnya di setiap request, anda dapat mengatur properti konfigurasi tersebut secara global, yaitu di objek `axios.defaults`.

Contoh mengatur `baseURL` request secara global.

```js
import axios from 'axios'

axios.defaults.baseURL = 'http://api.myserver.com'

axios.get('/posts') // http://api.myserver.com/posts
axios.get('/posts') // http://api.myserver.com/users
```

Contoh mengatur `Content-Type` header secara global.

```js
import axios from 'axios'

axios.defaults.headers.common['Content-Type'] = 'application/vnd.api+json'

axios.get('/posts') // Content-Type: application/vnd.api+json
axios.get('/posts') // Content-Type: application/vnd.api+json
```

Referensi [https://axios-http.com/docs/config_defaults](https://axios-http.com/docs/config_defaults)