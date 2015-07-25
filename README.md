# node-info [![version][npm-version]][npm-url] [![License][npm-license]][license-url]

> Beautiful console logs for your console applications

[![Build Status][travis-image]][travis-url]
[![Downloads][npm-downloads]][npm-url]
[![Code Climate][codeclimate-quality]][codeclimate-url]
[![Coverage Status][codeclimate-coverage]][codeclimate-url]
[![Dependencies][david-image]][david-url]

## Install

```sh
npm install --save info
```

## Usage

### info(name, [options])

- **name** (`String`, *Required*): The name/label to use
- **options** (`Object`, *Optional*): An optional [`options`](#options) object may be passed that alters certain behaviours

Returns: `Function` The logging function


```js
var info = require('info')

var log = info('😄', {
  colors: {
    name: 'blue',
    date: 'green'
  }
})


log('foo')
```

The above example will output:

![example](example.png)

### Options

| Name      | Type       | Required | Description                            | Default       |
| --------- | ---------- | -------- | -------------------------------------- | ------------- |
| `date`    | `Object`   | no       | [date options](#date-options) object   |               |
| `colors`  | `Object`   | no       | [color options](#color-options) object |               |
| `func`    | `Function` | no       | The logging function                   | `console.log` |

#### Date Options

| Name      | Type     | Required | Description                                                                   | Default       |
| --------- | -------- | --------- | ----------------------------------------------------------------------------- | ------------- |
| `format`  | `String` | no       | any [`dateformat`](https://www.npmjs.com/package/dateformat) compatible value | `hh:MM:ss TT` |

#### Color Options

| Name   | Type           | Required | Description                                                                                 | Default            |
| ------ | -------------- | -------- | ------------------------------------------------------------------------------------------- | ------------------ |
| `name` | `String|Array` | no       | any [`chalk`](https://www.npmjs.com/package/chalk#styles) *style* value, or array of values | `['blue', 'bold']` |
| `date` | `String|Array` | no       | any [`chalk`](https://www.npmjs.com/package/chalk#styles) *style* value, or array of values | `['green']`        |

`info` will also look for `options` object in your `package.json` file. *This is accomplished using [`pkg-config`](https://www.npmjs.com/package/pkg-config), refer to `pkg-config`'s [README](https://github.com/ahmadnassri/pkg-config/blob/master/README.md) for more info*

## License

[ISC License](LICENSE) &copy; [Ahmad Nassri](https://www.ahmadnassri.com/)

[license-url]: https://github.com/ahmadnassri/node-info/blob/master/LICENSE

[travis-url]: https://travis-ci.org/ahmadnassri/node-info
[travis-image]: https://img.shields.io/travis/ahmadnassri/node-info.svg?style=flat-square

[npm-url]: https://www.npmjs.com/package/info
[npm-license]: https://img.shields.io/npm/l/info.svg?style=flat-square
[npm-version]: https://img.shields.io/npm/v/info.svg?style=flat-square
[npm-downloads]: https://img.shields.io/npm/dm/info.svg?style=flat-square

[codeclimate-url]: https://codeclimate.com/github/ahmadnassri/node-info
[codeclimate-quality]: https://img.shields.io/codeclimate/github/ahmadnassri/node-info.svg?style=flat-square
[codeclimate-coverage]: https://img.shields.io/codeclimate/coverage/github/ahmadnassri/node-info.svg?style=flat-square

[david-url]: https://david-dm.org/ahmadnassri/node-info
[david-image]: https://img.shields.io/david/ahmadnassri/node-info.svg?style=flat-square
