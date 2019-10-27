# chain-fns

[![Build Status](https://travis-ci.org/saxjst/chain-fns.svg?branch=master)](https://travis-ci.org/saxjst/chain-fns)
[![Coverage Status](https://coveralls.io/repos/github/saxjst/chain-fns/badge.svg?branch=master)](https://coveralls.io/github/saxjst/chain-fns?branch=master)

> Create a chain of responsability by chaining a list of handlers

## Install

```
$ npm install chain-fns
```

## Usage

```js
const chainFns = require("chain-fns");

const divideByTwo = next => num => next(num / 2);
const addOne = next => num => next(num + 1);
const stopChainIfOdd = next => num => (num % 2 === 0 ? next(num) : num);
const thousandTimes = next => num => next(num * 1000);

const operations = chainFns([double, addOne, stopChainIfOdd, thousandTimes]);

operations(10);
//=> 6000

operations(12);
//=> 7
```

## API

### chainFns(fns)

Returns the first handler chains with the others

### fns

Type: `Function[]`

Each functions should be curried with the first parameter being the next function they are chain with.

```js
const handler1 = next => (param1, param2, param3, ...) => ...
```

## License

MIT © [saxjst]()