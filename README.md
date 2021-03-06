# Sheetbase Module: @sheetbase/api-key

Sheetbase middleware to authorize with the API Key.

<!-- <block:header> -->

[![Build Status](https://travis-ci.com/sheetbase/api-key.svg?branch=master)](https://travis-ci.com/sheetbase/api-key) [![Coverage Status](https://coveralls.io/repos/github/sheetbase/api-key/badge.svg?branch=master)](https://coveralls.io/github/sheetbase/api-key?branch=master) [![NPM](https://img.shields.io/npm/v/@sheetbase/api-key.svg)](https://www.npmjs.com/package/@sheetbase/api-key) [![License][license_badge]][license_url] [![clasp][clasp_badge]][clasp_url] [![Support me on Patreon][patreon_badge]][patreon_url] [![PayPal][paypal_donate_badge]][paypal_donate_url] [![Ask me anything][ask_me_badge]][ask_me_url]

<!-- </block:header> -->

## Install

Using npm: `npm install --save @sheetbase/api-key`

```ts
import * as ApiKey from "@sheetbase/api-key";
```

As a library: `1NulS_tPHLm401X7Km_ONKgtRK-VHnC5ODmNZ1sMt0QgXuDgtffxJ-Zzv`

Set the _Indentifier_ to **ApiKeyModule** and select the lastest version, [view code](https://script.google.com/d/1NulS_tPHLm401X7Km_ONKgtRK-VHnC5ODmNZ1sMt0QgXuDgtffxJ-Zzv/edit?usp=sharing).

```ts
declare const ApiKeyModule: { ApiKey: any };
const ApiKey = ApiKeyModule.ApiKey;
```

## Usage

- Docs homepage: https://sheetbase.github.io/api-key

- API reference: https://sheetbase.github.io/api-key/api

<!-- <block:body> -->

## Getting started

Install: `npm install --save @sheetbase/api-key`

```ts
import { middleware as apiKeyMiddleware } from "@sheetbase/api-key";

const ApiKeyMiddleware = apiKeyMiddleware({ key: apiKey });

router.get("/", ApiKeyMiddleware, (req, res) => {
  return res.send("Aye!");
});
```

## Configs

### key

- Type: `string`

A single key.

### apiKeys

- Type: `{[key: string]: string | APIKey}`

Multiple api keys for multiple clients.

```ts
interface APIKey {
  value?: string;
  id?: string;
  title?: string;
  description?: string;
  createdAt?: string | number;
  [k: string]: any;
}
```

### failure

- Type: `(req: RouteRequest, res: RouteResponse) => any` (Sheetbase route handler)

Custom handler if not passed, default showing an unauthorized message.

```ts
{
  failure: (req, res) => res.json({ hey: "Go away!" });
}
```

### trigger

- Type: `(req: RouteRequest, apiKey: APIKey) => void`

Trigger when the middileware is call, useful for logging multiple API keys usage.

```ts
{
  trigger: (req, apiKey) => {
    return console.log("A client access using this API Key:", apiKey);
  };
}
```

<!-- </block:body> -->

## License

**@sheetbase/api-key** is released under the [MIT](https://github.com/sheetbase/api-key/blob/master/LICENSE) license.

<!-- <block:footer> -->

[license_badge]: https://img.shields.io/github/license/mashape/apistatus.svg
[license_url]: https://github.com/sheetbase/api-key/blob/master/LICENSE
[clasp_badge]: https://img.shields.io/badge/built%20with-clasp-4285f4.svg
[clasp_url]: https://github.com/google/clasp
[patreon_badge]: https://lamnhan.github.io/assets/images/badges/patreon.svg
[patreon_url]: https://www.patreon.com/lamnhan
[paypal_donate_badge]: https://lamnhan.github.io/assets/images/badges/paypal_donate.svg
[paypal_donate_url]: https://www.paypal.me/lamnhan
[ask_me_badge]: https://img.shields.io/badge/ask/me-anything-1abc9c.svg
[ask_me_url]: https://m.me/sheetbase

<!-- </block:footer> -->
