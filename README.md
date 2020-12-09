<p align="center">
<img src="./.assets/nuxt_LogRocket.png" width="300px" alt="nuxt-logrocket">
</p>

# nuxt-logrocket

[![npm (scoped with tag)](https://img.shields.io/npm/v/nuxt-logrocket/latest.svg?style=flat-square)](https://npmjs.com/package/nuxt-logrocket)
[![npm](https://img.shields.io/npm/dt/nuxt-logrocket.svg?style=flat-square)](https://npmjs.com/package/nuxt-logrocket)
[![CircleCI](https://img.shields.io/circleci/project/github/nuxt-community/nuxt-logrocket.svg?style=flat-square)](https://circleci.com/gh/nuxt-community/nuxt-logrocket)
[![Codecov](https://img.shields.io/codecov/c/github/nuxt-community/nuxt-logrocket.svg?style=flat-square)](https://codecov.io/gh/nuxt-community/nuxt-logrocket)
[![Dependencies](https://david-dm.org/nuxt-community/nuxt-logrocket/status.svg?style=flat-square)](https://david-dm.org/nuxt-community/nuxt-logrocket)
[![js-standard-style](https://img.shields.io/badge/code_style-standard-brightgreen.svg?style=flat-square)](http://standardjs.com)

> LogRocket module for Nuxt.js

[📖 **Release Notes**](./CHANGELOG.md)

## Features

- Supports `logrocket-vuex` plugin integration by default
- Ability to run in development mode

## Setup

- Add `nuxt-logrocket` dependency using yarn or npm to your project

```sh
yarn add nuxt-logrocket
```

OR

```sh
npm install nuxt-logrocket --save
```

- Add `nuxt-logrocket` to the `modules` section of your `nuxt.config.js` file

```js
{
  modules: [
    'nuxt-logrocket',
  ],

  logRocket: {
    // configure LogRocket
    logRocketId: '',
    devModeAllowed: false,
    config: {
      //
    }
  }
}
```

## For Typescript Users

Add the types to your `"types"` array in `tsconfig.json` after the `@nuxt/types` entry.

### tsconfig.json

```json
{
  "compilerOptions": {
    "types": [
      "@nuxt/types",
      "nuxt-logrocket"
    ]
  }
}
```

## Integration with Official Sentry Module

If you're using the [`@nuxtjs/sentry`](https://github.com/nuxt-community/sentry-module) module, this module will automatically add a LogRocket session recording URL to every Sentry exception report.

Note that in order to have this work correctly, you must add `@nuxtjs/sentry` with a higher priority in your `nuxt.config.js` file. For example:

```js
{
  modules: [
    ...
    '@nuxtjs/sentry',
    ...
    'nuxt-logrocket'
    ...
  ]
}
```

You can read more about this integration [here](https://docs.logrocket.com/docs/sentry).

## Options

Options can be passed using either environment variables or `logRocket` section in `nuxt.config.js`.
Setting a value for the required `logRocketId` option is enough in most cases.

Below is the complete list of options:

| Option | Type | Default | Required | Environment Variable |
| :-- | :-- | :-- | :-- | :-- |
| logRocketId | `String` | `''` | True | `process.env.LOGROCKET_ID` |
| devModeAllowed | `Boolean` | `false` | False | `process.env.LOGROCKET_DEV_MODE_ALLOWED` |
| release | `String` | `null` | False | `process.env.LOGROCKET_RELEASE` |
| consoleEnabled | `Boolean` | `true` | False | `process.env.LOGROCKET_CONSOLE` |
| networkEnabled | `Boolean` | `true` | False | `process.env.LOGROCKET_NETWORK` |
| networkRequestSanitizer | `Function` | - | False | - |
| networkResponseSanitizer | `Function` | - | False | - |
| domEnabled | `Boolean` | `true` | False | `process.env.LOGROCKET_DOM_ENABLED` |
| inputSanitizer | `Boolean` | `false` | False | `process.env.LOGROCKET_INPUT_SANITIZER` |
| textSanitizer | `Boolean` | `false` | False | `process.env.LOGROCKET_TEXT_SANITIZER` |
| baseHref | `String` | `null` | False | `process.env.LOGROCKET_BASE_HREF` |
| shouldCaptureIP | `Boolean` | `true` | False | `process.env.LOGROCKET_SHOULD_CAPTURE_IP` |
| rootHostname | `String` | `null` | False | `process.env.LOGROCKET_ROOT_HOSTNAME` |
| shouldDebugLog | `Boolean` | `true` | False | `process.env.LOGROCKET_SHOULD_DEBUG_LOG` |
| mergeIframes | `Boolean` | `false` | False | `process.env.LOGROCKET_MERGE_IFRAMES` |

This is an example containing the default values for the options:

```js
{
  logRocketId: '',
  devModeAllowed: false,
  config: {
    release: null,
    console: {
      isEnabled: true
    },
    network: {
      isEnabled: true,
      networkRequestSanitizer: () => {},
      networkResponseSanitizer: () => {}
    },
    dom: {
      isEnabled: true,
      inputSanitizer: false,
      textSanitizer: false,
      baseHref: null
    },
    shouldCaptureIP: true,
    rootHostname: null,
    shouldDebugLog: true,
    mergeIframes: false
  }
}
```

## Usage

LogRocket gets automatically injected into your application when it is setup correctly. By default this module works only in `production` and on client-side events.

In order to use LogRocket's injected functionality in your application, you can use :

```js
this.$logRocket
```

in your components or :

```js
app.$logRocket
```

in plugins.

If Vuex store is initialized, LogRocket Vuex plugin will be automatically registered.

Visit LogRocket's website for a full list of features : [Docs](https://docs.logrocket.com/docs)

## Development

- Clone this repository
- Install dependencies using `yarn install` or `npm install`
- Start development server using `yarn run dev` or `npm run dev`
- Point your browser to `http://localhost:3000`

## License

[MIT License](./LICENSE) - Alibaba Travels Co
