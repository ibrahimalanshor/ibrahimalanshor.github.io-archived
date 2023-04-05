---
title: Vue Dynamically Binding Multiple Attributes
date: 2023-04-05 19:00:00 +0700
images: ['/images/blogs/bind-multiple-attributes/thumbnail.jpg']
---

Jika anda memiliki banyak atribut yang akan di-binding pada suatu element/component, anda dapat menyimpan atribut-atribut tersebut ke dalam objek, kemudian di-bind sekaligus menggunakan `v-bind` tanpa argument.

Contoh.

```html
<!-- App.vue -->
<script setup>
const attributes = {
  disabled: true,
  name: 'submit',
  type: 'submit',
  value: 'ok',
  formtarget: '_blank'
}
</script>

<template>
  <button v-bind="attributes">Button</button>
</template>
```

Hasilnya.

![Button v-bind](/images/blogs/bind-multiple-attributes/button-v-bind.png)