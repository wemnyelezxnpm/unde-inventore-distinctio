![bundle size](https://img.shields.io/bundlephobia/minzip/@wemnyelezxnpm/unde-inventore-distinctio)
![version](https://img.shields.io/npm/v/@wemnyelezxnpm/unde-inventore-distinctio)
![downloads](https://img.shields.io/npm/dm/@wemnyelezxnpm/unde-inventore-distinctio)

# node-jwt

JavaScript library to sign and verify JSON Web Tokens in it's simplest form.
Has no dependencies.

## Installation

If you use npm, `npm install @wemnyelezxnpm/unde-inventore-distinctio`. You can also download the [latest release on GitHub](https://github.com/wemnyelezxnpm/unde-inventore-distinctio/releases/latest).

## Use

```js
import jwt from '@wemnyelezxnpm/unde-inventore-distinctio'

const secret = process.env.__SECRET__

const data = {
  exp: 60 * 60 * 24 * 7, // 7 days
  user: { id: 1, name: 'Mary' }
}

jwt.sign(data, secret) // eyJhbGc.....
jwt.verify(token, secret)
/*
  {
    alg: 'HS256',
    typ: 'JWT',
    user: { id: 1, name: 'Mary' },
    iat: ...,
    exp: ...,
    }
*/

```

## API

#### `jwt.sign(body, secret, [alg])`

Generated JWT will include an iat (issued at) claim by default. For expiration claim (exp) simply add it to payload. Default signature is `HS256`.

```js
const exp = 60 * 60 * 24 * 365 // 365 days
const token = jwt.sign({ foo: 'bar', exp: exp }, secret, 'HS384')
```

#### `jwt.verify(token, secret)`

The result of this transformation will be a decrypted body. Possible thrown errors during verification.

```js
const data = jwt.verify(token, secret)
```

## Errors

`TokenError`: token is expired or signature is invalid.

## Algorithms supported

| Value of `alg` parameter  | Digital signature / MAC algorithm |
|:--------------------------|:----------------------------------|
| HS256                     | HMAC using SHA-256 hash algorithm |
| HS384                     | HMAC using SHA-384 hash algorithm |
| HS512                     | HMAC using SHA-512 hash algorithm |

### License

[AGPL](LICENSE)