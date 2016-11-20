# Free Mobile for JS
![Release](https://img.shields.io/npm/v/@cedx/free-mobile.svg) ![License](https://img.shields.io/npm/l/@cedx/free-mobile.svg) ![Downloads](https://img.shields.io/npm/dt/@cedx/free-mobile.svg) ![Dependencies](https://img.shields.io/david/cedx/free-mobile.js.svg) ![Code quality](https://img.shields.io/codacy/grade/e5a0027047554e298db354bcf3defefc.svg) ![Build](https://img.shields.io/travis/cedx/free-mobile.js.svg)

Send SMS messages to your [Free Mobile](http://mobile.free.fr) account, in [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript).

To use this library, you must have enabled SMS Notifications in the Options of your [Subscriber Area](https://mobile.free.fr/moncompte).

## Requirements
The latest [Node.js](https://nodejs.org) and [NPM](https://www.npmjs.com) versions.
If you plan to play with the sources, you will also need the [Gulp.js](http://gulpjs.com/) latest version.

## Installing via [npm](https://www.npmjs.com)
From a command prompt, run:

```shell
$ npm install --save @cedx/free-mobile
```

## Usage
This package has an API based on [Observables](http://reactivex.io/intro.html).

It provides a single class, `Client`, which allow to send messages to your mobile phone by using the `sendMessage` method:

```javascript
const {Client} = require('free-mobile');

let client = new Client({
  username: 'your Free Mobile user name',
  password: 'your Free Mobile identification key'
});

client.sendMessage('Hello World!').subscribe(
  () => console.log('The message was sent successfully.'),
  err => console.log(`An error occurred: ${err}`)
);
```

The text of the messages will be automatically truncated to 160 characters: you can't send multipart messages using this library.

## Promise Support
If you require it, an `Observable` can be converted to a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) by using the `toPromise()` method:

```javascript
let promise = client.sendMessage('Hello World!').toPromise();
promise.then(() => console.log('The message was sent successfully.'));
```

## Unit Tests
In order to run the tests, you must set two environment variables:

```shell
$ export FREEMOBILE_USERNAME="<your Free Mobile user name>"
$ export FREEMOBILE_PASSWORD="<your Free Mobile identification key>"
```

Then, you can run the `test` script from the command prompt:

```shell
$ npm test
```

## See Also
- [API Reference](http://dev.belin.io/free-mobile.js)
- [Code Quality](https://www.codacy.com/app/cedx/free-mobile-js)
- [Continuous Integration](https://travis-ci.org/cedx/free-mobile.js)

## License
[Free Mobile for JS](https://github.com/cedx/free-mobile.js) is distributed under the Apache License, version 2.0.
