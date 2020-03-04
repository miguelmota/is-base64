# is-base64

> Predicate that returns true if [base64](https://en.wikipedia.org/wiki/Base64) string.

## Install

```bash
npm install is-base64
```

## Usage

```javascript
var isBase64 = require('is-base64');

var string = 'iVBORw0KGgoAAAAN ... kSuQmCC';
var stringWithMime = 'data:image/png;base64,iVBORw0KGgoAAAA ... AAElFTkSuQmCC';

console.log(isBase64(string)); // true
console.log(isBase64(stringWithMime)); // false
console.log(isBase64(stringWithMime, {allowMime: true})); // true
console.log(isBase64(string, {mimeRequired: true})); // false
console.log(isBase64(stringWithMime, {mimeRequired: true})); // true
console.log(isBase64('1342234')); // false
console.log(isBase64('afQ$%rfew')); // false
console.log(isBase64('dfasdfr342')); // false
console.log(isBase64('uuLMhh==')); // true
console.log(isBase64('uuLMhh')); // false
console.log(isBase64('uuLMhh', {paddingRequired: false})); // true
console.log(isBase64('')); // true
console.log(isBase64('', {allowEmpty: false})); // false
```

## API

## isBase64(string, options)

- {string} string - string to check if is valid base64 string

- {object} [options]
    - [options.allowEmpty=true] {boolean} - returns true for empty string
    - [options.allowMime=false] {boolean} - returns true for valid strings with optional mime
    - [options.mimeRequired=false] {boolean} - returns true for valid strings with mime
    - [options.paddingRequired=true] {boolean} - returns true for valid strings with valid padding

## CLI

Install CLI:

```bash
npm install -g is-base64
```

CLI example:

```bash
$ is-base64 aGVsbG8gd29ybGQ=
true
```

Piping example:

```bash
$ echo aGVsbG8gd29ybGQ= | is-base64
true
```

## FAQ

- Q: Why is empty string `""` a valid base64 string by default?

  - A: According to [RFC 4648 Section 10](https://tools.ietf.org/html/rfc4648#section-10), the following is valid test vector:

      ```
      BASE64("") = ""
      ```

# License

MIT
