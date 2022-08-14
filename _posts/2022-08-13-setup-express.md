---
layout: post
title: "Setup Express"
tags: [nodejs, server]
date: 2022-08-13 20:00:00 +0700
---

Install Paket.

```bash
npm init -y
npm install --save express cors morgan
```

Buat file `app.js`.

```js
const express = require('express')
const cors = require('cors')
const morgan = require('morgan')

module.exports = class App {
  constructor(config = {}) {
    this.#setApp()
    this.#setConfig(config)
    this.#setMiddlewares(config.middlewares)
    this.#setRoutes(config.routes)
  }

  #setApp() {
    this.app = express()
  }

  #setConfig(config = {}) {
    this.app.set('port', config.port || 4000)
    this.app.set('env', config.env || 'development')
  }

  #setMiddlewares(middlewares = []) {
    this.app.use(cors())
    this.app.use(morgan(this.app.get('env') === 'development' ? 'dev' : 'combined'))

    for (const middleware of middlewares) {
      this.app.use(middleware)
    }
  }

  #setRoutes(routes = []) {
    for (const { path, router } of routes) {
      this.app.use(path, router)
    }
  }

  run(cb) {
    const port = this.app.get('port')

    this.app.listen(port, () => {
      if (cb) {
        cb(port)
      } else {
        console.log(`server running at ${port}`)
      }
    })
  }
}
```

Buat file `server.js`.

```js
const App = require('./app.js')

const config = {
  port: process.env.PORT || 4000,
  env: process.env.NODE_ENV || 'development',
}

const helloRoute = {
  path: '/',
  router: (req, res) => res.json('hello world')
}

const middlewares = []

const app = new App({
  port: config.port,
  env: config.env,
  routes: [helloRoute],
  middlewares
})

app.run()
```

Jalankan server.

```bash
NODE_ENV=development node server.js
# server running at 4000
```

Test

```bash
curl http://localhost:4000
# "hello world"
```

[Github Repo](https://github.com/ibrahimalanshor/simple-express/tree/v0.0.1)