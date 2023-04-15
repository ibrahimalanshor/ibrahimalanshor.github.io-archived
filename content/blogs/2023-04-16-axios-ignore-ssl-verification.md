---
title: Cara Ignore SSL Verification di Axios Request
date: 2023-04-16 06:30:00 +0700
images: ['/images/blogs/axios-ignore-ssl/thumbnail.jpg']
---

```bash
Error: certificate has expired
```

Untuk mengatasi ssl yang error pada request axios karena ssl expired atau yang lainnya, anda dapat menonaktifkan verifikasi ssl dengan menggunaan custom `Https Agent`.

Pertama buat custom `Https Agent` melalui module `https` dengan opsi properti `rejectUnauthorized: false` untuk menonaktifkan verifikasi ssl.

```js
const { Agent } = require('https')

const agent = new Agent({
    rejectUnauthorized: false
})
```

Setelah itu, gunakan `agent` yang sudah dibuat pada konfigurasi `httpsAgent` request axios.

```js
const axios = require('axios')
const { Agent } = require('https')

const agent = new Agent({
    rejectUnauthorized: false
})

axios
    .get('https://example.com', {
        httpsAgent: agent
    })
    .then(res => console.log(res.data))
    .catch(console.log)
```

Atau gunakan `agent` pada axios instance.

```js
const axios = require('axios')
const { Agent } = require('https')

const agent = new Agent({
    rejectUnauthorized: false
})
const instance = axios.create({
    httpsAgent: agent
})

instance
    .get('https://example.com')
    .then(res => console.log(res.data))
    .catch(console.log)
```