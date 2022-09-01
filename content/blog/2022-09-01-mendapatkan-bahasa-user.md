---
layout: post
title: "Mendapatkan Bahasa Yang Digunakan Browser User Dengan Javascript"
tags: [javascript]
date: 2022-09-01 19:45:00 +0700
---

Untuk mendapatkan bahasa yang digunakan browser pengguna dengan javascript, kita dapat memanfaatkan fitur [Web Api Navigator](https://developer.mozilla.org/en-US/docs/Web/API/Navigator) yang disediakan javascript.

Tepatnya melalui properti `language` atau `languages` pada objek `window.navigator`.

```js
console.log(window.navigator.language) // en-US
console.log(window.navigator.languages) // ['en-US', 'en']
```

- Properti `language` akan mengambalikan string yang berisi bahasa yang digunakan oleh browser pengguna.
- Properti `languages` akan mengambalikan array string yang berisi bahasa-bahasa yang dapat digunakan oleh browser pengguna, dengan urutan dari yang sedang digunakan.