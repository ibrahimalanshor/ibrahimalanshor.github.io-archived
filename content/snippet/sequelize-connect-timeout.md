---
title: 'Increase Timeout Duration Sequelize'
date: 2022-10-16 20:00:00 +0700
---

```js
const sequelize = new Sequelize('database', 'username', 'password', {
  host: 'localhost',
  dialectOptions: {
    connectTimeout: 60000 // milliseconds
  }
});
```