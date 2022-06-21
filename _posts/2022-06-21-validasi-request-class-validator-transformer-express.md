---
layout: post
title: "Validasi Request Dengan Class Validator dan Class Transformer Express Typescript"
tags: [typescript, express]
data: 2022-06-21 10:10:00 +0700
---

Class Validator dan Class Transformer adalah library yang dapat anda gunakan untuk melakukan validasi pada request express.

Class Transformer digunakan untuk mentransformasi object ke dalam class tertentu.

Class Validator digunakan untuk memvalidasi property pada class sesuai dengan aturan yang sudah ditentukan.

Langkah-Langkah:

1. Tangkap Request Body dengan middleware
2. Transform request body objek ke class request dengan class-tranformer.
3. Validasi hasil class dengan class-validator.

## Buat Target Class Validator

Buat class yang berisi property yang akan divalidasi beserta aturannya menggunakan class-validator.

```ts
import { IsDefined, IsEmail, IsString, Length } from 'class-validator'
import { Expose } from 'class-tranformer'

export default class RegisterRequest {
  @Expose()
  @IsDefined()
  @IsEmail()
  public email: string;

  @Expose()
  @IsDefined()
  @IsString()
  @Length(4, 8)
  public username: string;

  @Expose()
  @IsDefined()
  @IsString()
  @Length(8, 16)
  public password: string;
}
```

> Expose digunakan untuk hanya menggunakan property yang didefinisikan saja.

## Buat Validator Middleware

Buat validator middleware yang akan mentransformasi request objek ke class kemudian divalidasi hasil class-nya.

- Gunakan `plainToClass` modul dari class-transformer proses transformasinya.
- Gunakan `validateOrReject` untuk proses validasi class-nya.

```ts
import { RequestHandler, Request, Response, NextFunction } from 'express'
import { plainToClass } from 'class-tranformer'
import { validateOrReject } from 'class-validator'

export default (schema: any): RequestHandler => {
  return async (req: Request, res: Response, next: NextFunction) => {
    try {
      const body: any = plainToClass(schema, req.body, {
        excludeExtraneousValues: true
      })

      await validateOrReject(body, , {
        stopAtFirstError: true,
        validationError: {
          target: false,
          value: false,
        },
      })

      req.body = body

      next()
    } catch (err) {
      next(err)
    }
  }
}
```

## Gunakan Pada Router

```ts
import { Router, Request, Response } from 'express'
import RegisterRequest from './register.request'
import validate from './validate'

const router: Router = Router()

router.post('/register', validate(RegisterRequest), (req: Request, res: Response) => res.json(req.body))
```