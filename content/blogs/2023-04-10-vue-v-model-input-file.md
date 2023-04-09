---
title: Vue v-model Input File
date: 2023-04-10 06:00:00 +0700
images: ['/images/blogs/vue-v-model-input-file/thumbnail.jpg']
---

`v-model` tidak dapat digunakan pada element input tipe file karena element tersebut `read-only`. Untuk mendapatkan nilai file dari file yang diupload pada input file tersebut, gunakan `change` event.

Saya biasanya membuat component sendiri untuk input tipe file, dari component tersebut saya bind `v-model` dari component tersebut.

Berikut file `FileInput.vue`.

```html
<!-- FileInput.vue -->
<script setup>
const emit = defineEmits(['update:modelValue'])

function handleChange(e) {
    emit('update:modelValue', e.target.files[0])
}
</script>

<template>
    <input type="file" v-on:change="handleChange">
</template>
```

Contoh penggunaanya di file `App.vue`.

```html
<!-- App.vue -->
<script setup>
import { ref } from 'vue';
import FileInput from '@/components/FileInput.vue';

const file = ref(null)
</script>

<template>
  <file-input v-model="file" />
  <ul v-if="file">
    <li>File : {{ file.name }}</li>
    <li>Type : {{ file.type }}</li>
    <li>Size : {{ file.size }}</li>
    <li>Last Modified : {{ file.lastModifiedDate }}</li>
  </ul>
</template>
```

Hasilnya.

![File Input](/images/blogs/vue-v-model-input-file/file-input.gif)