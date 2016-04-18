# frau-local-appresolver

[![NPM version][npm-image]][npm-url]
[![Build status][ci-image]][ci-url]
[![Coverage Status][coverage-image]][coverage-url]
[![Dependency Status][dependencies-image]][dependencies-url]

A free-range-app utility for resolving locally hosted apps.

## Installation

Install from NPM:
```shell
npm install frau-local-appresolver
```

## Usage

### From CLI

The FRAU app resolver can be run either directly on the console CLI (assuming dependencies are installed), or specified as a script in `package.json`.

Launching the local app resolver can be as simple as:

```javascript
frau-local-appresolver --appclass|-c urn:d2l:fra:class:some-app
```

However additional options (described below) can be configured:

```javascript
frau-local-appresolver --appclass|-c urn:d2l:fra:class:some-app 
                       --configfile|-f appconfig.json 
                       --hostname|-h acme.com 
                       --port|-p 3000 
                       --dist|-d dist
```

```javascript
"scripts": {
  "resolver": "frau-local-appresolver"
},
"config": { 
  "frauLocalAppResolver": {
    "appClass": "urn:d2l:fra:class:some-app",
    "configFile": "appconfig.json",
    "hostname": "acme.com",
    "port": "3000",
    "dist": "dist"
   }
}
```

### From JavaScript

```javascript
var appResolver = require('frau-local-appresolver').resolver;

// simply provide required appClass
appResolver = appResolver(appClass);

// alternatively override default options
appResolver = appResolver(appClass, options);

// host the app resolver
appResolver.host();

// get where the app content is hosted
var target = appResolver.getUrl();
```

**Parameters**:

- `appClass` (required) - The app class to resolve.
- `options` (optional) - An object containing:
  - `dist` - The directory containing the app files to serve.  By default, the `dist` directory is used.
  - `port` - The port to listen on.  By default, port `3000` is used, which is the port that the LMS expects it on.
  - `hostname` - The hostname (or IP) to listen on. By default, `localhost` is used.  You should not need to change this.
  - `configFile` - The name of the app config file.  By default, `appconfig.json` is used.  You should not need to change this.

## Contributing
Contributions are welcome, please submit a pull request!

### Code Style

This repository is configured with [EditorConfig](http://editorconfig.org) rules and
contributions should make use of them.

[npm-url]: https://www.npmjs.org/package/frau-local-appresolver
[npm-image]: https://img.shields.io/npm/v/frau-local-appresolver.svg
[ci-url]: https://travis-ci.org/Brightspace/frau-local-appresolver
[ci-image]: https://img.shields.io/travis-ci/Brightspace/frau-local-appresolver.svg
[coverage-url]: https://coveralls.io/r/Brightspace/frau-local-appresolver?branch=master
[coverage-image]: https://img.shields.io/coveralls/Brightspace/frau-local-appresolver.svg
[dependencies-url]: https://david-dm.org/brightspace/frau-local-appresolver
[dependencies-image]: https://img.shields.io/david/Brightspace/frau-local-appresolver.svg
