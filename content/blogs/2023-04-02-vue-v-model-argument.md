---
title: Vue v-model Arguments
date: 2023-04-02 10:00:00 +0700
images: ['/images/blogs/v-model-arguments/thumbnail.jpg']
---

`v-model` arguments dapat digunakan untuk membuat multi v-model binding pada component.

Misal disini ada component `UserNameInput.vue` yang terdiri dari dua input, yaitu `first name` dan `last name`.

Component tersebut akan melakukan two way binding pada dua props, `firstname` dan `lastname`.

```html
<!-- UserNameInput.vue -->
<script setup>
import { computed } from 'vue';

const props = defineProps({
    firstname: String,
    lastname: String
})
const emit = defineEmits([
    'update:firstname',
    'update:lastname'
])

const firstNameValue = computed({
    get: function () {
        return props.firstname
    },
    set: function (value) {
        emit('update:firstname', value)
    }
})
const lastNameValue = computed({
    get: function () {
        return props.lastname
    },
    set: function (value) {
        emit('update:lastname', value)
    }
})
</script>

<template>
  <input
    type="text"
    placeholder="First Name"
    v-model="firstNameValue"
  />
  <input
    type="text"
    placeholder="Name Name"
    v-model="lastNameValue"
  />
</template>
```

Untuk menggunakan component tersebut, tambahkan `v-model` dengan arguments `firstname` dan `lastname`.

```html
<!-- App.vue -->
<script setup>
import { ref } from 'vue';
import UserNameInput from '@/components/UserNameInput.vue';

const firstname = ref(null)
const lastname = ref(null)
</script>

<template>
  <user-name-input
    v-model:firstname="firstname"
    v-model:lastname="lastname"
  />
  <p>First Name : {{ firstname }}</p>
  <p>Last Name : {{ lastname }}</p>
</template>
```

Hasilnya.

![v-model arguments](/images/blogs/v-model-arguments/v-model-argument.gif)