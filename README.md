# oh-my-log [![version][npm-version]][npm-url] [![License][npm-license]][license-url]

> Beautiful console logs for your console applications with string substitution using [`fürmat`][furmat] & styling with [Chalk][chalk].

[![Build Status][travis-image]][travis-url]
[![Downloads][npm-downloads]][npm-url]
[![Code Climate][codeclimate-quality]][codeclimate-url]
[![Coverage Status][codeclimate-coverage]][codeclimate-url]
[![Dependency Status][dependencyci-image]][dependencyci-url]
[![Dependencies][david-image]][david-url]

## Install

```bash
npm install --only=production --save oh-my-log
```

## Usage

I recommend using an optimized build matching your Node.js environment version, otherwise, the standard `require` would work just fine with any version of Node `>= v4.0` .

```js
/*
 * Node 7
 */
const logger = require('oh-my-log/lib/node7')

/*
 * Node 6
 */
const logger = require('oh-my-log/lib/node6')

/*
 * Node 4 (Default)
 * Note: additional ES2015 polyfills may be required
 */
var logger = require('oh-my-log')
```

## API

### myLog(name, [options])

- **name** (`String`, *Required*): The name/label to use
- **options** (`Object`, *Optional*): An optional [`options`](#options) object may be passed that alters certain behaviours

Returns: `Function` The logging function


```javascript
const logger = require('oh-my-log')
const log = logger('😄')

log('foo')
```

The above example will output:

![example](example.png)

- Create custom local variables:

  ```javascript
  const log = logger('😄', {
    locals: {
      me: 'ahmad'
    }
  })

  log('Hi, I\'m %me. repeat, my name is %me') // outputs: `Hi, my name is ahmad. repeat, my name is ahmad`
  ```

- Supports creating custom modifiers:

  ```javascript
  const log = logger('😄', {
    modifiers: {
      upper: (string) => string.toUpperCase()
    }
  })

  log('%s:upper', 'foo') // outputs `FOO`
  ```

- Use chained Chalk styles as modifiers:

  ```javascript
  const log = logger('😄')

  log('%s:red:bold', 'foo')
  ```

- Combine for extra magic:

  ```javascript
  const log = logger('😄', {
    locals: {
      me: 'ahmad'
    },
    modifiers: {
      upper: (string) => string.toUpperCase()
    }
  })


  log('Hi, I\'m %me:upper. repeat, my name is %me:upper:red:bold') // outputs a colored version of: `Hi, my name is ahmad. repeat, my name is ahmad`
  ```

### Options

| Name        | Type       | Required | Description                                                                         | Default          |
| ----------- | ---------- | -------- | ----------------------------------------------------------------------------------- | ---------------- |
| `prefix`    | `String`   | no       | prefix this string after substitution with `locals` values using [`fürmat`][furmat] | `[%name] %date:` |
| `locals`    | `Object`   | no       | `locals` object, *see [`fürmat`][furmat] for details*                               | `false`          |
| `modifiers` | `Object`   | no       | custom modifiers, *see [`fürmat`][furmat] for details*                              | `{}`             |
| `chalk`     | `Boolean`  | no       | enable/disable chalk modifiers support *see [`fürmat`][furmat] for details*         | `true`           |
| `date`      | `String`   | no       | any [`dateformat`](https://www.npmjs.com/package/dateformat) compatible value       | `hh:MM:ss TT`    |
| `func`      | `Function` | no       | The logging function                                                                | `console.log`    |

## [fürmat][furmat] & [Chalk](chalk)

`oh-my-log` relies heavily on `fürmat` for styling text *(using `chalk`)* and adding modifiers functions for extended formating, please review [`fürmat`][furmat] and [`chalk`][chalk] documentation for more details on how to use those modules.


`oh-my-log` will also look for `options` object in your `package.json` file. *This is accomplished using [`pkg-config`](https://www.npmjs.com/package/pkg-config), refer to `pkg-config`'s [README](https://github.com/ahmadnassri/pkg-config/blob/master/README.md) for more info*

----
> :copyright: [ahmadnassri.com](https://www.ahmadnassri.com/) &nbsp;&middot;&nbsp;
> License: [ISC][license-url] &nbsp;&middot;&nbsp;
> Github: [@ahmadnassri](https://github.com/ahmadnassri) &nbsp;&middot;&nbsp;
> Twitter: [@ahmadnassri](https://twitter.com/ahmadnassri)

[license-url]: http://choosealicense.com/licenses/isc/

[travis-url]: https://travis-ci.org/ahmadnassri/oh-my-log
[travis-image]: https://img.shields.io/travis/ahmadnassri/oh-my-log.svg?style=flat-square

[npm-url]: https://www.npmjs.com/package/oh-my-log
[npm-license]: https://img.shields.io/npm/l/oh-my-log.svg?style=flat-square
[npm-version]: https://img.shields.io/npm/v/oh-my-log.svg?style=flat-square
[npm-downloads]: https://img.shields.io/npm/dm/oh-my-log.svg?style=flat-square

[codeclimate-url]: https://codeclimate.com/github/ahmadnassri/oh-my-log
[codeclimate-quality]: https://img.shields.io/codeclimate/github/ahmadnassri/oh-my-log.svg?style=flat-square
[codeclimate-coverage]: https://img.shields.io/codeclimate/coverage/github/ahmadnassri/oh-my-log.svg?style=flat-square

[david-url]: https://david-dm.org/ahmadnassri/oh-my-log
[david-image]: https://img.shields.io/david/ahmadnassri/oh-my-log.svg?style=flat-square

[dependencyci-url]: https://dependencyci.com/github/ahmadnassri/oh-my-log
[dependencyci-image]: https://dependencyci.com/github/ahmadnassri/oh-my-log/badge?style=flat-square
