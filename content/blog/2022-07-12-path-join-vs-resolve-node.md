---
layout: post
title: "path join vs resolve Node JS"
tags: [node]
date: 2022-07-12 20:40:00 +0700
---

Keduanya digunakan untuk membuat path dengan cara kerja yang berbeda.

## 1. path.resolve mengembalikan absolute path

Path resolve akan mengembalikan absolute path dari working directory berada, misal di `/home/user/Documents`, maka absolute path-nya dari directory tersebut.

Sedangkan path join hanya menggabungkan path sebelumnya dan seterusnya.

```js
console.log(path.join('project')) // 'project'
console.log(path.join('project', 'web')) // 'project/web'
console.log(path.resolve('project')) // '/{working_directory}/project'
console.log(path.resolve('project')) // '/{working_directory}/project/web'
```

## 2. path.resolve membuat path dari kanan ke kiri

Path resolve membuat path dimulai dari arah kanan ke kiri sampai absolute path dibangun, sedangkan path join hanya menggabungkannya. 

```js
console.log(path.join('/project', '/web', '/blog')) // /project/web/blog
console.log(path.resolve('/project', '/web', '/blog')) // /blog
```