# tail-follow

Stream a file as it is appended

## Synopsis

If you are familiar with UNIX's `tail -f`, you have a good idea what this module does. It provides a `Readable` stream interface to a file that emits new data appended to the file in real time.

## API

```javascript
var TailFollow = require("tail-follow")
```

### new TailFollow(path, [options])

Create new TailFollow instance, for the file at the given path. This is a [Readable stream](https://nodejs.org/api/stream.html#stream_class_stream_readable), so you should listen for the `error` event and `data` event. Or `pipe()` it to another stream.

The optional arguments object takes the same parameters as a Readable stream (`encoding` and `highWaterMark`), plus the following:

  - `tailChunkSize`: Sets the size in bytes of `Buffer` objects created when reading from the file. Too small of a value, you will spend too much CPU handling new chunks; too big of a value, and you will waste memory. The default is `16384`.

#### .setTailChunkSize(size)

See the documentation for the `tailChunkSize` constructor option above.

## Contributing

This module uses ES2015. To compile the source to ES5 (compatible with Node.js, io.js), run `npm run compile`.

Any changes in behavior need test coverage. To run the tests, run `npm test`.
