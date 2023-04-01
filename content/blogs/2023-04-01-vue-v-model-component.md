---
title: Vue Component v-model
date: 2023-04-01 11:00:00 +0700
images: ['/images/blogs/vue-component-v-model/thumbnail.jpg']
---

Dibalik vue `v-model` directive pada element native, compiler mengubah directive tersebut menjadi seperti berikut:

```html
<input v-model="name" />
<!-- Menjadi -->
<input :value="name" @input="name = $event.target.value" />
```

Ketika `v-model` directive digunakan di component, compiler mengubah directive tersebut menjadi seperti berikut:

```html
<my-component v-model="name" />
<!-- Menjadi -->
<my-component
  :modelValue="name"
  @update:modelValue="newValue => name = newValue"
/>
```

Agar `v-model` pada component dapat bekerja dengan semestinya, anda perlu mendefinisikan `modelValue` props pada component, dan melakukan emit `update:modelValue` dengan nilai baru untuk mengubah nilai `v-model`-nya.

Contoh.

```html
<!-- MyComponent.vue -->
<script setup>
defineProps({ modelValue: String })
defineEmits(['update:modelValue'])
</script>

<template>
  <input
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>
```

Atau dengan menggunakan `computed`.

```html
<!-- MyComponent.vue -->
<script setup>
import { computed } from 'vue';

const props = defineProps({ modelValue: String })
const emit = defineEmits(['update:modelValue'])

const value = computed({
  get: function () {
    return props.modelValue
  },
  set: function (value) {
    emit('update:modelValue', value)
  }
})
</script>

<template>
  <input type="text" v-model="value">
</template>
```

Kemudian, coba gunakan component tersebut dengan menambahkan `v-model` directive.

```html
<script setup>
import { ref } from 'vue';
import MyComponent from '@/components/MyComponent.vue';

const name = ref(null)
</script>

<template>
  <my-component v-model="name" />
  <p>Name : {{ name }}</p>
</template>
```

Hasilnya.

![Vue Component v-model.gif](/images/blogs/vue-component-v-model/component-v-model-vue.gif)


Sumber: [https://vuejs.org/guide/components/v-model.html](https://vuejs.org/guide/components/v-model.html)