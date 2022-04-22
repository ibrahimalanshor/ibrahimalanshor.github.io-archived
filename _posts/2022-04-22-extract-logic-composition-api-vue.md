---
layout: 'post'
title: 'Memisahkan Logika Aplikasi Dengan Composition Api Vue'
date: 2022-04-22 09:30:00 +0700
---

Memisahkan logika aplikasi berguna agar kode menjadi independen sehingga lebih mudah untuk dikembangkan, dan membuat proses pengembangan menjadi lebih sederhana.

```js
export default function useTodo() {
  const todos = ref([]);

  const read = () => {
    // Read Todo
  };

  const store = (name) => {
    // Store Todo
  };

  const update = (todo) => {
    // Update Todo
  };

  const remove = (id) => {
    // Remove Todo
  };

  return {
    todos,
    read,
    store,
    update,
    remove,
  };
}
```

Gunakan pada komponen.

```html
<script setup>
import { onMounted } from 'vue'
import { useTodo } from './logic'

const { todos, read, store, update, remove } = useTodo()

onMounted(() => {
  read()
})

const handleSave = name => {
  store(name)
}
const handleUpdate = todo => {
  update(todo)
}
const handleDelete = id => {
  remove(id)
}
</script>
```