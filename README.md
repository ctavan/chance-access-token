# chance-access-token

[![Travis](https://img.shields.io/travis/jonathansamines/chance-access-token.svg?style=flat-square)](https://travis-ci.org/jonathansamines/chance-access-token) [![npm](https://img.shields.io/npm/v/chance-access-token.svg?style=flat-square)](https://www.npmjs.com/package/chance-access-token)


A simple chance mixin which generates a random access token

## Installation

```bash
npm install --save chance-access-token
```

## Usage

```js
const Chance = require('chance');
const accessToken = require('chance-access-token');

const chance = new Chance();

chance.mixin({ accessToken });

const expiredAccessToken = chance.accessToken({
  expireMode: 'expires_at',
  expired: true,
});

// =>
// {
//   token_type: 'bearer',
//   access_token: '89D690FF-C19D-4F0E-B8E2-B1EBB3F26B0B',
//   refresh_token: '8B4361C2-4E90-4E00-B825-48C0D82F7B93',
//   expires_at: '',
// }
```

## API

### chance.accessToken(options)

+ `options`
  + `expireMode` -  Can be either **expires_at** or **expires_in**. When set to **expires_at** it generates a token which expires at a random date. When set to **expires_in** it generates a token which expires in a random number of seconds.
  + `parseDate` - When is true and **expireMode** is **expires_at** it generates a date object, otherwise it generates a ISO string
  + `expired` - When is true and **expireMode** is **expires_at** it generates a date in the past
