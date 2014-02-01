# shortify

[browserify](https://github.com/substack/browserify) transform which can
shorten require paths with defined aliases.

## Installation

Install with [npm(1)](http://npmjs.org):

    $ npm install shortify

## Preview

Call shortify with your alias hash and pass it to the `transform` method of 
your browserify instance.

```
var shortify = require('shortify');

var builder = browserify({ entries: ['app.js'] });
var transform = shortify({ foo: '../../foo' });

builder.transform(transform).bundle().pipe(yourwritestream);
```

Then require your modules will be rewritten from:

```
var bar = require('foo/bar');
var baz = require('foo/../baz');

// your module.exports source code
```

to:

```
var bar = require('../../foo/bar');
var baz = require('../../foo/../baz');

// your module.exports source code
```

Main motivation behind this is that you can keep the > 80 character per
line limit when requiring templates, configuration, ... files shared
between your server and client environment.

## License

Copyright © 2013 Bodo Kaiser <i@bodokaiser.io>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
