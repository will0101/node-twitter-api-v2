# Twitter API v2

[![Twitter API v2 badge](https://img.shields.io/endpoint?url=https%3A%2F%2Ftwbadges.glitch.me%2Fbadges%2Fv2)](https://developer.twitter.com/en/docs/twitter-api/early-access)
[![Twitter API v1.1 badge](https://img.shields.io/endpoint?url=https%3A%2F%2Ftwbadges.glitch.me%2Fbadges%2Fstandard)](https://developer.twitter.com/en/docs/twitter-api/v1)
[![Version badge](https://badgen.net/github/release/PLhery/node-twitter-api-v2)](https://github.com/PLhery/node-twitter-api-v2)
[![Checks badge](https://github.com/PLhery/node-twitter-api-v2/actions/workflows/CI.yml/badge.svg)](https://github.com/PLhery/node-twitter-api-v2/actions/workflows/CI.yml)
[![Package size badge](https://badgen.net/bundlephobia/minzip/twitter-api-v2)](https://bundlephobia.com/package/twitter-api-v2)

Strongly typed, full-featured, light, versatile yet powerful Twitter API v1.1 and v2 client for Node.js.

Main maintainer: [@alkihis](https://github.com/alkihis) - <a href="https://www.buymeacoffee.com/alkihis" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" height="20px" marginTop="10px"></a>


## Highlights

✅ **Ready for v2 and good ol' v1.1 Twitter API**

✅ **Light: No dependencies, 17kb minified+gzipped**

✅ **Bundled types for request parameters and responses**

✅ **Streaming support**

✅ **Pagination utils**

✅ **Media upload helpers**

## How to use

Install it through your favorite package manager:
```bash
yarn add twitter-api-v2
# or
npm i twitter-api-v2
```

Here's is a quick example of usage:

```ts
import TwitterApi from 'twitter-api-v2';

// Instanciate with desired auth type (here's Bearer v2 auth)
const twitterClient = new TwitterApi('<YOUR_APP_USER_TOKEN>');

// Tell typescript it's a readonly app
const roClient = twitterClient.readOnly;

// Play with the built in methods
const user = await roClient.v2.userByUsername('plhery');
await twitterClient.v1.tweet('Hello, this is a test.');
// You can upload media easily!
await twitterClient.v1.uploadMedia('./big-buck-bunny.mp4');
```

## Why?

Sometimes, you just want to quickly bootstrap an application using the Twitter API.
Even if they're a lot of available libraries on the JavaScript ecosystem, they usually just
provide wrappers around HTTP methods, and some of them are bloated with many dependencies.

`twitter-api-v2` meant to provide full endpoint wrapping, from method name to response data,
using descriptive typings for read/write/DMs rights, request parameters and response payload.

A small feature comparaison with other libs:

| Package        | API version(s) | Response typings | Media helpers | Pagination | Subdeps |  Size (gzip)  | Install size  |
| -------------- | -------------- | ---------------- | ------------- | ---------- | --------------- | -------------:|  -------------:|
| twitter-api-v2 | v1.1, v2, labs | ✅               | ✅             | ✅         | 0               | ~17 kB      | [![twitter-api-v2 install size badge](https://badgen.net/packagephobia/install/twitter-api-v2)](https://packagephobia.com/result?p=twitter-api-v2) |
| twit           | v1.1           | ❌               | ✅             | ❌         | 51              | ~214.5 kB     | [![twit install size badge](https://badgen.net/packagephobia/install/twit)](https://packagephobia.com/result?p=twit) |
| twitter        | v1.1           | ❌               | ❌             | ❌         | 50              | ~182.1 kB     | [![twitter install size badge](https://badgen.net/packagephobia/install/twitter)](https://packagephobia.com/result?p=twitter) |
| twitter-lite   | v1.1, v2       | ❌               | ❌*            | ❌         | 4               | ~5.3 kB       | [![twitter-lite install size badge](https://badgen.net/packagephobia/install/twitter-lite)](https://packagephobia.com/result?p=twitter-lite) |
| twitter-v2     | v2             | ❌               | ❌             | ❌         | 7               | ~4.5 kB       | [![twitter-v2 install size badge](https://badgen.net/packagephobia/install/twitter-v2)](https://packagephobia.com/result?p=twitter-v2) |

\**No support for `media/upload`, cannot send a `multipart/form-data` encoded-body without tricks*

## Features

Here's the detailed feature list of `twitter-api-v2`:

### Basics:
- Support for v1.1 and **v2 of Twitter API**
- Make signed HTTP requests to Twitter with every auth type: **OAuth 1.0a**, **OAuth2** (even brand new user context OAuth2!) and **Basic** HTTP Authorization
- Helpers for numerous HTTP request methods (`GET`, `POST`, `PUT`, `DELETE` and `PATCH`),
  that handle query string parse & format, automatic body formatting and more
- High-class support for stream endpoints, with easy data consumption and auto-reconnect on stream errors

### Request helpers:
- Automatic paginator for endpoints like user and tweet timelines,
  allowing payload consumption with modern asynchronous iterators until your rate-limit is hit
- Convenient methods for authentication - generate auth links and ask for tokens to your users will be a breeze
- Media upload with API v1.1, including **long video & subtitles support**, automatic media type detection,
  **chunked upload** and support for **concurrent uploads**
- Dedicated methods that wraps API v1.1 & v2 endpoints, with **typed arguments** and fully **typed responses**
- Bundled parsing of rate limit headers
- Typed errors, meaningful error messages, error enumerations for both v1.1 and v2

### Type-safe first:
- **Typings for tweet, user, media entities (and more) are bundled!**
- Type-safe wrapping of dedicated methods in 3 right level: *DM*/*Read-write*/*Read-only* (just like Twitter API do!) -
  you can declare a read-only client - you will only see the methods associated with read-only endpoints

And last but not least, fully powered by native `Promise`s.

## Documentation

Learn how to use the full potential of `twitter-api-v2`.

- Get started
  - [Create a client and make your first request](./doc/basics.md)
  - [Handle Twitter authentication flows](./doc/auth.md)
  - [Explore some examples](./doc/examples.md)
- Use endpoints wrappers — ensure typings of request & response
  - [Available endpoint wrappers for v1.1 API](./doc/v1.md)
  - [Available endpoint wrappers for v2 API](./doc/v2.md)
  - [Use Twitter streaming endpoints (v1.1 & v2)](./doc/streaming.md)
- Deep diving into requests
  - [Use direct HTTP-method wrappers](./doc/http-wrappers.md)
  - [Use rate limit helpers](./doc/rate-limiting.md)
  - [Handle errors](./doc/errors.md)
  - [Master `twitter-api-v2` paginators](./doc/paginators.md)
  - [Discover available helpers](./doc/helpers.md)
