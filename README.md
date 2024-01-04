tweetnacl-util-js
=================

String encoding utilities extracted from early versions of <https://github.com/dchest/tweetnacl-js>

> **Nota bene**: this repository is basically a copy of the [original](https://github.com/dchest/tweetnacl-util-js) with some changes inspired by tweetnacl-js pull request [#186](https://github.com/dchest/tweetnacl-js/pull/186) which make this module ES6 compatible and allows you to `import nacl_util from 'nacl-util.esm.js'`.
>
> As a consequence, `npm run build` will now build ESM modules, while `npm run build-iife` has to be used in order to build the old version of this module.

Notice
------

Encoding/decoding functions in this package are correct,
however their performance and wide compatibility with uncommon runtimes is not
something that is considered important compared to the simplicity and size of
implementation. For example, they don't work under
React Native.

Instead of this package, I strongly recommend using my [StableLib](https://github.com/StableLib/stablelib) packages:

* [@stablelib/utf8](https://www.stablelib.com/modules/_stablelib_utf8.html) for UTF-8
  encoding/decoding (note that the names of operations are reversed compared to
  this package): `npm install @stablelib/utf8`

  Alternatively, in a modern environment, use [TextEncoder](https://developer.mozilla.org/en-US/docs/Web/API/TextEncoder) and [TextDecoder](https://developer.mozilla.org/en-US/docs/Web/API/TextDecoder).

* [@stablelib/base64](https://www.stablelib.com/modules/_stablelib_base64.html) for
  constant-time Base64 encoding/decoding: `npm install @stablelib/base64`


Installation
------------

Use a package manager:

[Bower](http://bower.io):

    $ bower install tweetnacl-util

[NPM](https://www.npmjs.org/):

    $ npm install tweetnacl-util

or [download source code](https://github.com/dchest/tweetnacl-util-js/releases).


Usage
------

To make keep backward compatibility with code that used `nacl.util` previously
included with TweetNaCl.js, just include it as usual:

```
<script src="nacl.min.js"></script>
<script src="nacl-util.min.js"></script>
<script>
  // nacl.util functions are now available, e.g.:
  // nacl.util.decodeUTF8
</script>
```

When using CommonJS:

```
var nacl = require('tweetnacl');
nacl.util = require('tweetnacl-util');
```


Documentation
-------------

#### nacl.util.decodeUTF8(string)

Decodes string and returns `Uint8Array` of bytes.

#### nacl.util.encodeUTF8(array)

Encodes `Uint8Array` or `Array` of bytes into string.

#### nacl.util.decodeBase64(string)

Decodes Base-64 encoded string and returns `Uint8Array` of bytes.

#### nacl.util.encodeBase64(array)

Encodes `Uint8Array` or `Array` of bytes into string using Base-64 encoding.
