---
title: Setting Up Knex Js
date: 2023-05-07 16:30:00 +0700
images: ['/images/blogs/setup-knex/thumbnail.jpg']
---

Knex is a SQL query builder that supports relational databases like PostgreSQL, MySQL, MariaDB, and others.

Knex supports query and schema builders, transactions, connection pooling, and other features with easy and simple usage.

In this post, I am going to explain how to use Knex to connect to the database and do some simple queries.

First, install Knex and the database driver library. Here, I am using `mysql` as the database and `mysql2` as the database driver library.

```bash
npm install --save knex mysql2
```

The knex module has a default export; it is a function to create a knex object. The function accepts the database configuration object at the first argument.

```js
const knex = require('knex')({
    client: 'mysql2',
    connection: {
        host: 'localhost',
        port: 3306,
        user: 'root',
        password: '',
        database: 'my_db'
    }
})
```

You can use the created knex object to do some database processes, like select, insert, update, and others, by calling the query builder method from the knex object.

Example.

## Select

```js
knex('users')
    .select()
    .then(console.log('users :', res))
```

## Insert

```js
knex('users')
    .insert({
        name: 'test',
        username: 'test',
        email: 'test@gmail.com',
        password: 'password'
    })
    .then(console.log('inserted id :', res))
```

## Update

```js
knex('users')
    .where('id', 1)
    .update({
        name: 'new name',
    })
    .then(console.log('updated id :', res))
```

## Delete

```js
knex('users')
    .where('id', 1)
    .del()
    .then(console.log('affected rows :', res))
```

For more detail, you can check out the full documentation here: [https://knexjs.org/guide/](https://knexjs.org/guide/).

> This is my first time writing a blog post in English, and I am sorry for my bad English. I helped so much with this grammar checker, [https://quillbot.com/grammar-check](https://quillbot.com/grammar-check).