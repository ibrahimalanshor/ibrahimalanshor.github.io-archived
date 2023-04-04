---
title: Vue Click Outside Element Event
date: 2023-04-04 17:00:00 +0700
images: ['/images/blogs/vue-click-outside/thumbnail.jpg']
---

Click outside event adalah event pada sautu element yang ter-trigger ketika area diluar element tersebut diclick.

Event ini biasa digunakan pada modal, dropdown, dan yang lainnya. Misal pada modal, ketika area diluar box modal diclick, click outside event akan ter-trigger, kemudian event tersebut dihandle dengan menutup/menyembunyikan modal.

Pada vue, anda dapat menggunakan package [click-outside-vue3](https://www.npmjs.com/package/click-outside-vue3) untuk menghandle click outside event pada suatu element.

```bash
npm install --save click-outside-vue3
# atau
yarn add click-outside-vue3
```

Untuk menggunakanya, import package tersebut pada component yang akan digunakan.

Kemudian tambahkan direktif `v-click-outside` pada element yang ingin di handle click outside event-nya, masukkan juga fungsi handler event-nya.

Contoh pada component `MyDropdown.vue`.

```html
<!-- MyDropdown.vue -->
<script setup>
import { ref } from 'vue';
import { directive as vClickOutside } from "click-outside-vue3"

const visible = ref(false)

function handleClickOutside() {
  visible.value = false
}
</script>

<template>
  <div
    class="container"
    v-click-outside="handleClickOutside"
  >
    <button
      class="toggle"
      @click="visible = !visible"
    >
      toggle
    </button>
    <div
      v-if="visible"
      class="content"
    >
      Lorem, ipsum dolor sit amet consectetur adipisicing elit.
    </div>
  </div>
</template>

<style>
.container {
  position: relative;
  width: fit-content;
}
.content {
  position: absolute;
  top: 20px;
  left: 0;
  background-color: white;
  border: 1px solid #111;
  width: 200px;
  padding: 10px;
}
</style>
```

Hasilnya.

![MyDropdown](/images/blogs/vue-click-outside/vue-click-outside.gif)

Atau install directive `v-click-outside` secara global di `main.js`.

```js
// main.js
import { createApp } from 'vue'
import './style.css'
import App from './App.vue'
import vClickOutside from "click-outside-vue3"

const app = createApp(App)

app.use(vClickOutside)
app.mount('#app')
```

Untuk menggunakanya sama seperti kode sebelumnya, dengan menambahkan `v-click-outside` directive pada element.

```html
<!-- MyDropdown.vue -->
<script setup>
import { ref } from 'vue';

const visible = ref(false)

function handleClickOutside() {
  visible.value = false
}
</script>

<template>
  <div
    class="container"
    v-click-outside="handleClickOutside"
  >
    <button
      class="toggle"
      @click="visible = !visible"
    >
      toggle
    </button>
    <div
      v-if="visible"
      class="content"
    >
      Lorem, ipsum dolor sit amet consectetur adipisicing elit.
    </div>
  </div>
</template>

<style>
.container {
  position: relative;
  width: fit-content;
}
.content {
  position: absolute;
  top: 20px;
  left: 0;
  background-color: white;
  border: 1px solid #111;
  width: 200px;
  padding: 10px;
}
</style>
```

Hasilnya.

![MyDropdown](/images/blogs/vue-click-outside/vue-click-outside.gif)