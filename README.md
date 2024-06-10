# @diotoborg/et-maxime-hic <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Array.prototype.toReversed` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.es/proposal-change-array-by-copy/#sec-array.prototype.toReversed).

Because `Array.prototype.toReversed` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @diotoborg/et-maxime-hic
```

## Usage/Examples

```js
var toReversed = require('@diotoborg/et-maxime-hic');
var assert = require('assert');

var arr = [0, 1, 2, 3, 4, 5];

var results = toReversed(arr);

assert.deepEqual(results, [5, 4, 3, 2, 1, 0]);
assert.deepEqual(arr, [0, 1, 2, 3, 4, 5]);
```

```js
var toReversed = require('@diotoborg/et-maxime-hic');
var assert = require('assert');
/* when Array#toReversed is not present */
delete Array.prototype.toReversed;
var shimmed = toReversed.shim();

assert.equal(shimmed, toReversed.getPolyfill());
assert.deepEqual(arr.toReversed(), toReversed(arr));
```

```js
var toReversed = require('@diotoborg/et-maxime-hic');
var assert = require('assert');
/* when Array#toReversed is present */
var shimmed = toReversed.shim();

assert.equal(shimmed, Array.prototype.toReversed);
assert.deepEqual(arr.toReversed(), toReversed(arr));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@diotoborg/et-maxime-hic
[npm-version-svg]: https://versionbadg.es/diotoborg/et-maxime-hic.svg
[deps-svg]: https://david-dm.org/diotoborg/et-maxime-hic.svg
[deps-url]: https://david-dm.org/diotoborg/et-maxime-hic
[dev-deps-svg]: https://david-dm.org/diotoborg/et-maxime-hic/dev-status.svg
[dev-deps-url]: https://david-dm.org/diotoborg/et-maxime-hic#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@diotoborg/et-maxime-hic.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@diotoborg/et-maxime-hic.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@diotoborg/et-maxime-hic.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@diotoborg/et-maxime-hic
