---
layout: post
title: "Cara Extend Express Request Object Dengan Typescript"
tags: [typescript, express]
date: 2022-06-21 20:30:00 +0700
---

Terkadang kita perlu menambahkan properti baru pada request object express contohnya seperti properti `user`.

```ts
router.get('/test',
  (req: Request, res: Response, next: NextFunction) => {
    try {
      req.user = 'admin'

      next(user)
    } catch (err) {
      next(err)
    }
  },
  (req: Request, res: Response, next: NextFunction) => {
    return res.json(req.user)
  }
)
```

Kode diatas akan menimbulkan error karena property user tidak ada di interface request express.

Untuk mengatasinya, pertama buat folder `@types/express` di dalamnya buat file `index.d.ts`.

```bash
mkdir @types/express
touch @types/express/index.d.ts
```

Buka file `tsconfig.json`, tambahkan folder `@types` pada properti `typeRoots`.

```json
"typeRoots": [
  "@types"
]
```