# mocha-clean

Cleans up [mocha] test stack traces.

Ever find it hard to read this? Me too.

```
  1) Test:
     ReferenceError: someKey is not defined
      at Context.<anonymous> (/Users/rsc/Projects/mocha-clean/test/test.js:24:5)
      at callFn (/Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runnable.js:249:21)
      at Test.Runnable.run (/Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runnable.js:242:7)
      at Runner.runTest (/Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runner.js:373:10)
      at /Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runner.js:451:12
      at next (/Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runner.js:298:14)
      at /Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runner.js:308:7
      at next (/Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runner.js:246:23)
      at Object._onImmediate (/Users/rsc/Projects/mocha-clean/node_modules/mocha/lib/runner.js:275:5)
      at processImmediate [as _immediateCallback] (timers.js:330:15)
```

This is better:

```
  1) Test:
     ReferenceError: someKey is not defined
      at myFunction (test/test:7:1)
      at test/test.js:24:5
```

It strips away mocha internals, node_modules, absolute paths (based on cwd), and 
other unneccessary cruft.

## Usage

Available via npm.

```sh
$ npm i --save-dev mocha-clean
```

[![npm version](http://img.shields.io/npm/v/mocha-clean.svg?style=flat)](https://npmjs.org/package/mocha-clean "View this project on npm")

Add this to your `test/mocha.opts`:

```js
--require mocha-clean
```

## Customization

### Showing node_modules

By default, mocha-clean removes anything under `node_modules`.
To disable this behavior, use this:

```js
--require mocha-clean/show_node_modules
```

### Showing filenames first

JavaScript has its stack traces in the format `at functionName (file)`, which 
can be hard to read for filenames. You can configure mocha-clean to display the 
filenames first.

```
3) error:
   ReferenceError: xyz is not defined
    test/fail.js:12:4: myfunction
    test/fail.js:9:9: Context.<anonymous>
```

Use:

```js
--require mocha-clean/filenames_first
```

## Thanks

[mocha]: http://visionmedia.github.io/mocha

**mocha-clean** © 2014+, Rico Sta. Cruz. Released under the [MIT] License.<br>
Authored and maintained by Rico Sta. Cruz with help from contributors ([list][contributors]).

> [ricostacruz.com](http://ricostacruz.com) &nbsp;&middot;&nbsp;
> GitHub [@rstacruz](https://github.com/rstacruz) &nbsp;&middot;&nbsp;
> Twitter [@rstacruz](https://twitter.com/rstacruz)

[MIT]: http://mit-license.org/
[contributors]: http://github.com/rstacruz/mocha-clean/contributors

