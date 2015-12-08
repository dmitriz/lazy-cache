# lazy-cache [![NPM version](https://img.shields.io/npm/v/lazy-cache.svg)](https://www.npmjs.com/package/lazy-cache)

> Cache requires to be lazy-loaded when needed.

## Install

Install with [npm](https://www.npmjs.com/)

```sh
$ npm i lazy-cache --save
```

## Usage

```js
var lazy = require('lazy-cache')(require);
```

**Use as a property on `lazy`**

The module is also added as a property to the `lazy` function
so it can be called without having to call a function first.

```js
var lazy = require('lazy-cache')(require);

// `npm install glob`
lazy('glob');

// glob sync
console.log(lazy.glob.sync('*.js'));

// glob async
lazy.glob('*.js', function (err, files) {
  console.log(files);
});
```

**Use as a function**

```js
var lazy = require('lazy-cache')(require);
var glob = lazy('glob');

// `glob` is a now a function that may be called when needed
glob().sync('foo/*.js');
```

## Aliases

An alias may be passed as the second argument if you don't want to use the automatically camel-cased variable name.

**Example**

```js
var utils = require('lazy-cache')(require);

utils('ansi-yellow', 'yellow');
console.log(utils.yellow('foo'));
```

## Browserify usage

**Example**

```js
var lazy = require('lazy-cache')(require);
// temporarily re-assign `require` to trick browserify
var fn = require;
require = lazy;
// list module dependencies here (`require` is actually `lazy`)
require('glob');
require = fn; // restore the native `require` function

/**
 * Now you can use glob with the `lazy.glob` variable
 */

// sync
console.log(lazy.glob.sync('*.js'));

// async
lazy.glob('*.js', function (err, files) {
  console.log(files.join('\n'));
});
```

## Related

[lint-deps](https://www.npmjs.com/package/lint-deps): CLI tool that tells you when dependencies are missing from package.json and offers you a… [more](https://www.npmjs.com/package/lint-deps) | [homepage](https://github.com/jonschlinkert/lint-deps)

## Running tests

Install dev dependencies:

```sh
$ npm i -d && npm test
```

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/lazy-cache/issues/new).

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2015 [Jon Schlinkert](https://github.com/jonschlinkert)
Released under the MIT license.

***

_This file was generated by [verb](https://github.com/verbose/verb) on December 08, 2015._