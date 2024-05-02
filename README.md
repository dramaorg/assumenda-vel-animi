# @dramaorg/assumenda-vel-animi <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2019 spec-compliant `Array.prototype.flatMap` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-@dramaorg/assumenda-vel-animi).

Because `Array.prototype.flatMap` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save @dramaorg/assumenda-vel-animi
```

## Usage/Examples

```js
var flatMap = require('@dramaorg/assumenda-vel-animi');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = flatMap(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var flatMap = require('@dramaorg/assumenda-vel-animi');
var assert = require('assert');
/* when Array#flatMap is not present */
delete Array.prototype.flatMap;
var shimmedFlatMap = flatMap.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, flatMap.getPolyfill());
assert.deepEqual(arr.flatMap(mapper), flatMap(arr, mapper));
```

```js
var flatMap = require('@dramaorg/assumenda-vel-animi');
var assert = require('assert');
/* when Array#flatMap is present */
var shimmedIncludes = flatMap.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, Array.prototype.flatMap);
assert.deepEqual(arr.flatMap(mapper), flatMap(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@dramaorg/assumenda-vel-animi
[npm-version-svg]: https://versionbadg.es/dramaorg/assumenda-vel-animi.svg
[deps-svg]: https://david-dm.org/dramaorg/assumenda-vel-animi.svg
[deps-url]: https://david-dm.org/dramaorg/assumenda-vel-animi
[dev-deps-svg]: https://david-dm.org/dramaorg/assumenda-vel-animi/dev-status.svg
[dev-deps-url]: https://david-dm.org/dramaorg/assumenda-vel-animi#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@dramaorg/assumenda-vel-animi.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@dramaorg/assumenda-vel-animi.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@dramaorg/assumenda-vel-animi.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@dramaorg/assumenda-vel-animi
[codecov-image]: https://codecov.io/gh/dramaorg/assumenda-vel-animi/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/dramaorg/assumenda-vel-animi/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/dramaorg/assumenda-vel-animi
[actions-url]: https://github.com/dramaorg/assumenda-vel-animi/actions
