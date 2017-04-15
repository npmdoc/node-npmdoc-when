# api documentation for  [when (v3.7.8)](http://cujojs.com)  [![npm package](https://img.shields.io/npm/v/npmdoc-when.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-when) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-when.svg)](https://travis-ci.org/npmdoc/node-npmdoc-when)
#### A lightweight Promises/A+ and when() implementation, plus other async goodies.

[![NPM](https://nodei.co/npm/when.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/when)

[![apidoc](https://npmdoc.github.io/node-npmdoc-when/build/screenCapture.buildCi.browser.apidoc.html.png)](https://npmdoc.github.io/node-npmdoc-when/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-when/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-when/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "browser": {
        "when": "./dist/browser/when.js",
        "vertx": false
    },
    "bugs": {
        "url": "https://github.com/cujojs/when/issues"
    },
    "contributors": [
        {
            "name": "Brian Cavalier",
            "url": "http://hovercraftstudios.com"
        },
        {
            "name": "John Hann",
            "url": "http://unscriptable.com"
        },
        {
            "name": "Scott Andrews"
        }
    ],
    "dependencies": {},
    "description": "A lightweight Promises/A+ and when() implementation, plus other async goodies.",
    "devDependencies": {
        "benchmark": "~1",
        "browserify": "~2",
        "buster": "~0.7",
        "exorcist": "~0.4",
        "glob": "^7.1.1",
        "jshint": "~2",
        "json5": "~0.2",
        "microtime": "~2",
        "mkdirp": "^0.5.1",
        "optimist": "~0.6",
        "poly": "^0.6.1",
        "promises-aplus-tests": "~2",
        "rest": "1.1.x",
        "sauce-connect-launcher": "~0.4",
        "uglify-js": "~2",
        "wd": "~0.2"
    },
    "directories": {
        "test": "test"
    },
    "dist": {
        "shasum": "c7130b6a7ea04693e842cdc9e7a1f2aa39a39f82",
        "tarball": "https://registry.npmjs.org/when/-/when-3.7.8.tgz"
    },
    "ender": {
        "files": [
            "*.js",
            "lib/*.js",
            "node/*.js",
            "unfold/*.js",
            "monitor/*.js",
            "lib/decorators/*.js"
        ]
    },
    "gitHead": "5c0a9ebaaf9bc859e76bd9584a9c9677e1e18f08",
    "homepage": "http://cujojs.com",
    "keywords": [
        "cujo",
        "Promises/A+",
        "promises-aplus",
        "promise",
        "promises",
        "deferred",
        "deferreds",
        "when",
        "async",
        "asynchronous",
        "ender"
    ],
    "license": "MIT",
    "main": "when.js",
    "maintainers": [
        {
            "name": "cujojs"
        }
    ],
    "name": "when",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/cujojs/when.git"
    },
    "scripts": {
        "benchmark": "node benchmark/promise && node benchmark/map",
        "browser-test": "npm run build-browser-test && buster-static -e browser -p 8080",
        "browserify": "npm run browserify-es6 && npm run browserify-when && npm run browserify-debug",
        "browserify-debug": "node scripts/browserify.js debug",
        "browserify-es6": "node scripts/browserify.js es6",
        "browserify-when": "node scripts/browserify.js when",
        "build-browser-test": "browserify ./node_modules/poly/es5.js -o test/browser/es5.js && node scripts/browserify-tests",
        "ci": "npm test && node test/sauce.js",
        "prepublish": "npm run browserify && npm run uglify",
        "preversion": "npm run browserify && npm run uglify",
        "start": "buster-static -e browser",
        "test": "jshint . && buster-test -e node && promises-aplus-tests test/promises-aplus-adapter.js",
        "tunnel": "node test/sauce.js -m",
        "uglify": "npm run uglify-es6 && npm run uglify-when",
        "uglify-es6": "uglifyjs es6-shim/Promise.js --compress --mangle  --in-source-map es6-shim/Promise.js.map --source-map es6-shim/Promise.min.js.map -o es6-shim/Promise.min.js",
        "uglify-when": "uglifyjs dist/browser/when.js --compress --mangle  --in-source-map dist/browser/when.js.map --source-map dist/browser/when.min.js.map -o dist/browser/when.min.js"
    },
    "version": "3.7.8"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module when](#apidoc.module.when)
1.  [function <span class="apidocSignatureSpan"></span>when (x, onFulfilled, onRejected, onProgress)](#apidoc.element.when.when)
1.  [function <span class="apidocSignatureSpan">when.</span>Promise (resolver, handler)](#apidoc.element.when.Promise)
1.  [function <span class="apidocSignatureSpan">when.</span>TimeoutError (message)](#apidoc.element.when.TimeoutError)
1.  [function <span class="apidocSignatureSpan">when.</span>all (promises)](#apidoc.element.when.all)
1.  [function <span class="apidocSignatureSpan">when.</span>any ()](#apidoc.element.when.any)
1.  [function <span class="apidocSignatureSpan">when.</span>attempt (f)](#apidoc.element.when.attempt)
1.  [function <span class="apidocSignatureSpan">when.</span>defer ()](#apidoc.element.when.defer)
1.  [function <span class="apidocSignatureSpan">when.</span>filter (promises, predicate)](#apidoc.element.when.filter)
1.  [function <span class="apidocSignatureSpan">when.</span>isPromiseLike (x)](#apidoc.element.when.isPromiseLike)
1.  [function <span class="apidocSignatureSpan">when.</span>iterate (f, condition, handler, x)](#apidoc.element.when.iterate)
1.  [function <span class="apidocSignatureSpan">when.</span>join ()](#apidoc.element.when.join)
1.  [function <span class="apidocSignatureSpan">when.</span>lift (f)](#apidoc.element.when.lift)
1.  [function <span class="apidocSignatureSpan">when.</span>map (promises, mapFunc)](#apidoc.element.when.map)
1.  [function <span class="apidocSignatureSpan">when.</span>promise (resolver)](#apidoc.element.when.promise)
1.  [function <span class="apidocSignatureSpan">when.</span>race ()](#apidoc.element.when.race)
1.  [function <span class="apidocSignatureSpan">when.</span>reduce ()](#apidoc.element.when.reduce)
1.  [function <span class="apidocSignatureSpan">when.</span>reduceRight ()](#apidoc.element.when.reduceRight)
1.  [function <span class="apidocSignatureSpan">when.</span>reject (x)](#apidoc.element.when.reject)
1.  [function <span class="apidocSignatureSpan">when.</span>resolve (x)](#apidoc.element.when.resolve)
1.  [function <span class="apidocSignatureSpan">when.</span>settle (promises)](#apidoc.element.when.settle)
1.  [function <span class="apidocSignatureSpan">when.</span>some ()](#apidoc.element.when.some)
1.  [function <span class="apidocSignatureSpan">when.</span>toString ()](#apidoc.element.when.toString)
1.  [function <span class="apidocSignatureSpan">when.</span>try (f)](#apidoc.element.when.try)
1.  [function <span class="apidocSignatureSpan">when.</span>unfold (unspool, condition, handler, x)](#apidoc.element.when.unfold)
1.  object <span class="apidocSignatureSpan">when.</span>Promise.prototype
1.  object <span class="apidocSignatureSpan">when.</span>TimeoutError.prototype
1.  object <span class="apidocSignatureSpan">when.</span>callbacks

#### [module when.Promise](#apidoc.module.when.Promise)
1.  [function <span class="apidocSignatureSpan">when.</span>Promise (resolver, handler)](#apidoc.element.when.Promise.Promise)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_defer ()](#apidoc.element.when.Promise._defer)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_handler (x)](#apidoc.element.when.Promise._handler)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_traverse (f, promises)](#apidoc.element.when.Promise._traverse)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_visitRemaining (promises, start, handler)](#apidoc.element.when.Promise._visitRemaining)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>all (promises)](#apidoc.element.when.Promise.all)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>any (promises)](#apidoc.element.when.Promise.any)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>createContext ()](#apidoc.element.when.Promise.createContext)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>enterContext ()](#apidoc.element.when.Promise.enterContext)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>exitContext ()](#apidoc.element.when.Promise.exitContext)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>filter (promises, predicate)](#apidoc.element.when.Promise.filter)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>iterate (f, condition, handler, x)](#apidoc.element.when.Promise.iterate)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>map (promises, f)](#apidoc.element.when.Promise.map)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>never ()](#apidoc.element.when.Promise.never)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>onFatalRejection (rejection)](#apidoc.element.when.Promise.onFatalRejection)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejection (rejection)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejection)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejectionHandled (rejection)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejectionHandled)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>race (promises)](#apidoc.element.when.Promise.race)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>reduce (promises, f)](#apidoc.element.when.Promise.reduce)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>reduceRight (promises, f)](#apidoc.element.when.Promise.reduceRight)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>reject (x)](#apidoc.element.when.Promise.reject)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>resolve (x)](#apidoc.element.when.Promise.resolve)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>settle (promises)](#apidoc.element.when.Promise.settle)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>some (promises, n)](#apidoc.element.when.Promise.some)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>unfold (unspool, condition, handler, x)](#apidoc.element.when.Promise.unfold)

#### [module when.Promise.prototype](#apidoc.module.when.Promise.prototype)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>_beget ()](#apidoc.element.when.Promise.prototype._beget)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>catch (onRejected)](#apidoc.element.when.Promise.prototype.catch)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>delay (ms)](#apidoc.element.when.Promise.prototype.delay)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>done (onResult, onError)](#apidoc.element.when.Promise.prototype.done)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>else (defaultValue)](#apidoc.element.when.Promise.prototype.else)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>ensure (handler)](#apidoc.element.when.Promise.prototype.ensure)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>finally (handler)](#apidoc.element.when.Promise.prototype.finally)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>fold (f, z)](#apidoc.element.when.Promise.prototype.fold)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>inspect ()](#apidoc.element.when.Promise.prototype.inspect)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>orElse (defaultValue)](#apidoc.element.when.Promise.prototype.orElse)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>otherwise (onRejected)](#apidoc.element.when.Promise.prototype.otherwise)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>progress (onProgress)](#apidoc.element.when.Promise.prototype.progress)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>spread (onFulfilled)](#apidoc.element.when.Promise.prototype.spread)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>tap (onFulfilledSideEffect)](#apidoc.element.when.Promise.prototype.tap)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>then (onFulfilled, onRejected, onProgress)](#apidoc.element.when.Promise.prototype.then)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>timeout (ms, reason)](#apidoc.element.when.Promise.prototype.timeout)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>with (receiver)](#apidoc.element.when.Promise.prototype.with)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>withThis (receiver)](#apidoc.element.when.Promise.prototype.withThis)
1.  [function <span class="apidocSignatureSpan">when.Promise.prototype.</span>yield (value)](#apidoc.element.when.Promise.prototype.yield)

#### [module when.TimeoutError](#apidoc.module.when.TimeoutError)
1.  [function <span class="apidocSignatureSpan">when.</span>TimeoutError (message)](#apidoc.element.when.TimeoutError.TimeoutError)

#### [module when.TimeoutError.prototype](#apidoc.module.when.TimeoutError.prototype)
1.  [function <span class="apidocSignatureSpan">when.TimeoutError.prototype.</span>constructor (message)](#apidoc.element.when.TimeoutError.prototype.constructor)

#### [module when.callbacks](#apidoc.module.when.callbacks)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>apply (asyncFunction, extraAsyncArgs)](#apidoc.element.when.callbacks.apply)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>call (asyncFunction)](#apidoc.element.when.callbacks.call)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>lift (f)](#apidoc.element.when.callbacks.lift)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>liftAll (src, combine, dst)](#apidoc.element.when.callbacks.liftAll)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>promisify (asyncFunction, positions)](#apidoc.element.when.callbacks.promisify)



# <a name="apidoc.module.when"></a>[module when](#apidoc.module.when)

#### <a name="apidoc.element.when.when"></a>[function <span class="apidocSignatureSpan"></span>when (x, onFulfilled, onRejected, onProgress)](#apidoc.element.when.when)
- description and source-code
```javascript
function when(x, onFulfilled, onRejected, onProgress) {
		var p = Promise.resolve(x);
		if (arguments.length < 2) {
			return p;
		}

		return p.then(onFulfilled, onRejected, onProgress);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise"></a>[function <span class="apidocSignatureSpan">when.</span>Promise (resolver, handler)](#apidoc.element.when.Promise)
- description and source-code
```javascript
function Promise(resolver, handler) {
			this._handler = resolver === Handler ? handler : init(resolver);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.TimeoutError"></a>[function <span class="apidocSignatureSpan">when.</span>TimeoutError (message)](#apidoc.element.when.TimeoutError)
- description and source-code
```javascript
function TimeoutError(message) {
		Error.call(this);
		this.message = message;
		this.name = TimeoutError.name;
		if (typeof Error.captureStackTrace === 'function') {
			Error.captureStackTrace(this, TimeoutError);
		}
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.all"></a>[function <span class="apidocSignatureSpan">when.</span>all (promises)](#apidoc.element.when.all)
- description and source-code
```javascript
function all(promises) {
		return when(promises, Promise.all);
	}
```
- example usage
```shell
...
	 * Return a promise that will resolve only once all the supplied arguments
	 * have resolved. The resolution value of the returned promise will be an array
	 * containing the resolution values of each of the arguments.
	 * @param {...*} arguments may be a mix of promises and values
	 * @returns {Promise}
	 */
	function join(/* ...promises */) {
		return Promise.all(arguments);
	}

	/**
	 * Return a promise that will fulfill once all input promises have
	 * fulfilled, or reject when any one input promise rejects.
	 * @param {array|Promise} promises array (or promise for an array) of promises
	 * @returns {Promise}
...
```

#### <a name="apidoc.element.when.any"></a>[function <span class="apidocSignatureSpan">when.</span>any ()](#apidoc.element.when.any)
- description and source-code
```javascript
any = function () {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.attempt"></a>[function <span class="apidocSignatureSpan">when.</span>attempt (f)](#apidoc.element.when.attempt)
- description and source-code
```javascript
function attempt(f) {
		<span class="apidocCodeCommentSpan">/*jshint validthis:true */
</span>		for(var i=0, l=arguments.length-1, a=new Array(l); i<l; ++i) {
			a[i] = arguments[i+1];
		}
		return apply(f, this, a);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.defer"></a>[function <span class="apidocSignatureSpan">when.</span>defer ()](#apidoc.element.when.defer)
- description and source-code
```javascript
function defer() {
		return new Deferred();
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.filter"></a>[function <span class="apidocSignatureSpan">when.</span>filter (promises, predicate)](#apidoc.element.when.filter)
- description and source-code
```javascript
function filter(promises, predicate) {
		return when(promises, function(promises) {
			return Promise.filter(promises, predicate);
		});
	}
```
- example usage
```shell
...
	when.settle      = settle;               // Settle a list of promises

	when.any         = lift(Promise.any);    // One-winner race
	when.some        = lift(Promise.some);   // Multi-winner race
	when.race        = lift(Promise.race);   // First-to-settle race

	when.map         = map;                  // Array.map() for promises
	when.filter      = filter;               // Array.filter() for promises
	when.reduce      = lift(Promise.reduce);       // Array.reduce() for promises
	when.reduceRight = lift(Promise.reduceRight);  // Array.reduceRight() for promises

	when.isPromiseLike = isPromiseLike;      // Is something promise-like, aka thenable

	when.Promise     = Promise;              // Promise constructor
	when.defer       = defer;                // Create a {promise, resolve, reject} tuple
...
```

#### <a name="apidoc.element.when.isPromiseLike"></a>[function <span class="apidocSignatureSpan">when.</span>isPromiseLike (x)](#apidoc.element.when.isPromiseLike)
- description and source-code
```javascript
function isPromiseLike(x) {
		return x && typeof x.then === 'function';
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.iterate"></a>[function <span class="apidocSignatureSpan">when.</span>iterate (f, condition, handler, x)](#apidoc.element.when.iterate)
- description and source-code
```javascript
function iterate(f, condition, handler, x) {
			return unfold(function(x) {
				return [x, f(x)];
			}, condition, handler, x);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.join"></a>[function <span class="apidocSignatureSpan">when.</span>join ()](#apidoc.element.when.join)
- description and source-code
```javascript
function join() {
		return Promise.all(arguments);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.lift"></a>[function <span class="apidocSignatureSpan">when.</span>lift (f)](#apidoc.element.when.lift)
- description and source-code
```javascript
function lift(f) {
		return function() {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
		};
	}
```
- example usage
```shell
...
	 *
	 *		xhr.onload = callback;
	 *		xhr.onerror = errback;
	 *
	 *		xhr.send();
	 *	}
	 *
	 *    var promiseAjax = callbacks.lift(traditionalAjax);
	 *    promiseAjax("GET", "/movies.json").then(console.log, console.error);
	 *
	 *    var promiseAjaxGet = callbacks.lift(traditionalAjax, "GET");
	 *    promiseAjaxGet("/movies.json").then(console.log, console.error);
	 *
	 * @param {Function} f traditional async function to be decorated
	 * @param {...*} [args] arguments to be prepended for the new function @deprecated
...
```

#### <a name="apidoc.element.when.map"></a>[function <span class="apidocSignatureSpan">when.</span>map (promises, mapFunc)](#apidoc.element.when.map)
- description and source-code
```javascript
function map(promises, mapFunc) {
		return when(promises, function(promises) {
			return Promise.map(promises, mapFunc);
		});
	}
```
- example usage
```shell
...

The second example shows off the power that comes with when's promise logic. Here, we get an array of numbers from a remote source
 and reduce them. The example will print '150' if all went well, and if there was a problem will print a full stack trace.

'''js
var when = require('when');
var rest = require('rest');

when.reduce(when.map(getRemoteNumberList(), times10), sum)
.done(function(result) {
    console.log(result);
});

function getRemoteNumberList() {
// Get a remote array [1, 2, 3, 4, 5]
return rest('http://example.com/numbers').then(JSON.parse);
...
```

#### <a name="apidoc.element.when.promise"></a>[function <span class="apidocSignatureSpan">when.</span>promise (resolver)](#apidoc.element.when.promise)
- description and source-code
```javascript
function promise(resolver) {
		return new Promise(resolver);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.race"></a>[function <span class="apidocSignatureSpan">when.</span>race ()](#apidoc.element.when.race)
- description and source-code
```javascript
race = function () {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.reduce"></a>[function <span class="apidocSignatureSpan">when.</span>reduce ()](#apidoc.element.when.reduce)
- description and source-code
```javascript
reduce = function () {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
		}
```
- example usage
```shell
...

The second example shows off the power that comes with when's promise logic. Here, we get an array of numbers from a remote source
 and reduce them. The example will print '150' if all went well, and if there was a problem will print a full stack trace.

'''js
var when = require('when');
var rest = require('rest');

when.reduce(when.map(getRemoteNumberList(), times10), sum)
.done(function(result) {
    console.log(result);
});

function getRemoteNumberList() {
// Get a remote array [1, 2, 3, 4, 5]
return rest('http://example.com/numbers').then(JSON.parse);
...
```

#### <a name="apidoc.element.when.reduceRight"></a>[function <span class="apidocSignatureSpan">when.</span>reduceRight ()](#apidoc.element.when.reduceRight)
- description and source-code
```javascript
reduceRight = function () {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
		}
```
- example usage
```shell
...
	when.any         = lift(Promise.any);    // One-winner race
	when.some        = lift(Promise.some);   // Multi-winner race
	when.race        = lift(Promise.race);   // First-to-settle race

	when.map         = map;                  // Array.map() for promises
	when.filter      = filter;               // Array.filter() for promises
	when.reduce      = lift(Promise.reduce);       // Array.reduce() for promises
	when.reduceRight = lift(Promise.reduceRight);  // Array.reduceRight() for promises

	when.isPromiseLike = isPromiseLike;      // Is something promise-like, aka thenable

	when.Promise     = Promise;              // Promise constructor
	when.defer       = defer;                // Create a {promise, resolve, reject} tuple

	// Error types
...
```

#### <a name="apidoc.element.when.reject"></a>[function <span class="apidocSignatureSpan">when.</span>reject (x)](#apidoc.element.when.reject)
- description and source-code
```javascript
function reject(x) {
			return new Promise(Handler, new Async(new Rejected(x)));
		}
```
- example usage
```shell
...
		return new Deferred();
	}

	function Deferred() {
		var p = Promise._defer();

		function resolve(x) { p._handler.resolve(x); }
		function reject(x) { p._handler.reject(x); }
		function notify(x) { p._handler.notify(x); }

		this.promise = p;
		this.resolve = resolve;
		this.reject = reject;
		this.notify = notify;
		this.resolver = { resolve: resolve, reject: reject, notify: notify };
...
```

#### <a name="apidoc.element.when.resolve"></a>[function <span class="apidocSignatureSpan">when.</span>resolve (x)](#apidoc.element.when.resolve)
- description and source-code
```javascript
function resolve(x) {
			return isPromise(x) ? x
				: new Promise(Handler, new Async(getHandler(x)));
		}
```
- example usage
```shell
...
	 * @param {function?} onProgress callback to be called when progress updates
	 *   are issued for x. @deprecated
	 * @returns {Promise} a new promise that will fulfill with the return
	 *   value of callback or errback or the completion value of promiseOrValue if
	 *   callback and/or errback is not supplied.
	 */
	function when(x, onFulfilled, onRejected, onProgress) {
		var p = Promise.resolve(x);
		if (arguments.length < 2) {
			return p;
		}

		return p.then(onFulfilled, onRejected, onProgress);
	}
...
```

#### <a name="apidoc.element.when.settle"></a>[function <span class="apidocSignatureSpan">when.</span>settle (promises)](#apidoc.element.when.settle)
- description and source-code
```javascript
function settle(promises) {
		return when(promises, Promise.settle);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.some"></a>[function <span class="apidocSignatureSpan">when.</span>some ()](#apidoc.element.when.some)
- description and source-code
```javascript
some = function () {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.toString"></a>[function <span class="apidocSignatureSpan">when.</span>toString ()](#apidoc.element.when.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.try"></a>[function <span class="apidocSignatureSpan">when.</span>try (f)](#apidoc.element.when.try)
- description and source-code
```javascript
function attempt(f) {
		<span class="apidocCodeCommentSpan">/*jshint validthis:true */
</span>		for(var i=0, l=arguments.length-1, a=new Array(l); i<l; ++i) {
			a[i] = arguments[i+1];
		}
		return apply(f, this, a);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.unfold"></a>[function <span class="apidocSignatureSpan">when.</span>unfold (unspool, condition, handler, x)](#apidoc.element.when.unfold)
- description and source-code
```javascript
function unfold(unspool, condition, handler, x) {
			return resolve(x).then(function(seed) {
				return resolve(condition(seed)).then(function(done) {
					return done ? seed : resolve(unspool(seed)).spread(next);
				});
			});

			function next(item, newSeed) {
				return resolve(handler(item)).then(function() {
					return unfold(unspool, condition, handler, newSeed);
				});
			}
		}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.Promise"></a>[module when.Promise](#apidoc.module.when.Promise)

#### <a name="apidoc.element.when.Promise.Promise"></a>[function <span class="apidocSignatureSpan">when.</span>Promise (resolver, handler)](#apidoc.element.when.Promise.Promise)
- description and source-code
```javascript
function Promise(resolver, handler) {
			this._handler = resolver === Handler ? handler : init(resolver);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise._defer"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>_defer ()](#apidoc.element.when.Promise._defer)
- description and source-code
```javascript
function defer() {
			return new Promise(Handler, new Pending());
		}
```
- example usage
```shell
...
	 * @return {{promise: Promise, resolve: function, reject: function, notify: function}}
	 */
	function defer() {
		return new Deferred();
	}

	function Deferred() {
		var p = Promise._defer();

		function resolve(x) { p._handler.resolve(x); }
		function reject(x) { p._handler.reject(x); }
		function notify(x) { p._handler.notify(x); }

		this.promise = p;
		this.resolve = resolve;
...
```

#### <a name="apidoc.element.when.Promise._handler"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>_handler (x)](#apidoc.element.when.Promise._handler)
- description and source-code
```javascript
function getHandler(x) {
			if(isPromise(x)) {
				return x._handler.join();
			}
			return maybeThenable(x) ? getHandlerUntrusted(x) : new Fulfilled(x);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise._traverse"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>_traverse (f, promises)](#apidoc.element.when.Promise._traverse)
- description and source-code
```javascript
function traverse(f, promises) {
			return traverseWith(tryCatch2, f, promises);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise._visitRemaining"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>_visitRemaining (promises, start, handler)](#apidoc.element.when.Promise._visitRemaining)
- description and source-code
```javascript
function visitRemaining(promises, start, handler) {
			for(var i=start; i<promises.length; ++i) {
				markAsHandled(getHandler(promises[i]), handler);
			}
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.all"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>all (promises)](#apidoc.element.when.Promise.all)
- description and source-code
```javascript
function all(promises) {
			return traverseWith(snd, null, promises);
		}
```
- example usage
```shell
...
	 * Return a promise that will resolve only once all the supplied arguments
	 * have resolved. The resolution value of the returned promise will be an array
	 * containing the resolution values of each of the arguments.
	 * @param {...*} arguments may be a mix of promises and values
	 * @returns {Promise}
	 */
	function join(/* ...promises */) {
		return Promise.all(arguments);
	}

	/**
	 * Return a promise that will fulfill once all input promises have
	 * fulfilled, or reject when any one input promise rejects.
	 * @param {array|Promise} promises array (or promise for an array) of promises
	 * @returns {Promise}
...
```

#### <a name="apidoc.element.when.Promise.any"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>any (promises)](#apidoc.element.when.Promise.any)
- description and source-code
```javascript
function any(promises) {
			var p = Promise._defer();
			var resolver = p._handler;
			var l = promises.length>>>0;

			var pending = l;
			var errors = [];

			for (var h, x, i = 0; i < l; ++i) {
				x = promises[i];
				if(x === void 0 && !(i in promises)) {
					--pending;
					continue;
				}

				h = Promise._handler(x);
				if(h.state() > 0) {
					resolver.become(h);
					Promise._visitRemaining(promises, i, h);
					break;
				} else {
					h.visit(resolver, handleFulfill, handleReject);
				}
			}

			if(pending === 0) {
				resolver.reject(new RangeError('any(): array must not be empty'));
			}

			return p;

			function handleFulfill(x) {
				<span class="apidocCodeCommentSpan">/*jshint validthis:true*/
</span>				errors = null;
				this.resolve(x); // this === resolver
			}

			function handleReject(e) {
				/*jshint validthis:true*/
				if(this.resolved) { // this === resolver
					return;
				}

				errors.push(e);
				if(--pending === 0) {
					this.reject(errors);
				}
			}
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.createContext"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>createContext ()](#apidoc.element.when.Promise.createContext)
- description and source-code
```javascript
function noop() {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.enterContext"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>enterContext ()](#apidoc.element.when.Promise.enterContext)
- description and source-code
```javascript
function noop() {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.exitContext"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>exitContext ()](#apidoc.element.when.Promise.exitContext)
- description and source-code
```javascript
function noop() {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.filter"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>filter (promises, predicate)](#apidoc.element.when.Promise.filter)
- description and source-code
```javascript
function filter(promises, predicate) {
			var a = slice.call(promises);
			return Promise._traverse(predicate, a).then(function(keep) {
				return filterSync(a, keep);
			});
		}
```
- example usage
```shell
...
	when.settle      = settle;               // Settle a list of promises

	when.any         = lift(Promise.any);    // One-winner race
	when.some        = lift(Promise.some);   // Multi-winner race
	when.race        = lift(Promise.race);   // First-to-settle race

	when.map         = map;                  // Array.map() for promises
	when.filter      = filter;               // Array.filter() for promises
	when.reduce      = lift(Promise.reduce);       // Array.reduce() for promises
	when.reduceRight = lift(Promise.reduceRight);  // Array.reduceRight() for promises

	when.isPromiseLike = isPromiseLike;      // Is something promise-like, aka thenable

	when.Promise     = Promise;              // Promise constructor
	when.defer       = defer;                // Create a {promise, resolve, reject} tuple
...
```

#### <a name="apidoc.element.when.Promise.iterate"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>iterate (f, condition, handler, x)](#apidoc.element.when.Promise.iterate)
- description and source-code
```javascript
function iterate(f, condition, handler, x) {
			return unfold(function(x) {
				return [x, f(x)];
			}, condition, handler, x);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.map"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>map (promises, f)](#apidoc.element.when.Promise.map)
- description and source-code
```javascript
function map(promises, f) {
			return Promise._traverse(f, promises);
		}
```
- example usage
```shell
...

The second example shows off the power that comes with when's promise logic. Here, we get an array of numbers from a remote source
 and reduce them. The example will print '150' if all went well, and if there was a problem will print a full stack trace.

'''js
var when = require('when');
var rest = require('rest');

when.reduce(when.map(getRemoteNumberList(), times10), sum)
.done(function(result) {
    console.log(result);
});

function getRemoteNumberList() {
// Get a remote array [1, 2, 3, 4, 5]
return rest('http://example.com/numbers').then(JSON.parse);
...
```

#### <a name="apidoc.element.when.Promise.never"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>never ()](#apidoc.element.when.Promise.never)
- description and source-code
```javascript
function never() {
			return foreverPendingPromise; // Should be frozen
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.onFatalRejection"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>onFatalRejection (rejection)](#apidoc.element.when.Promise.onFatalRejection)
- description and source-code
```javascript
onFatalRejection = function (rejection) {
			enqueue(throwit, rejection.value);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.onPotentiallyUnhandledRejection"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejection (rejection)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejection)
- description and source-code
```javascript
onPotentiallyUnhandledRejection = function (rejection) {
			enqueue(report, rejection);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.onPotentiallyUnhandledRejectionHandled"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejectionHandled (rejection)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejectionHandled)
- description and source-code
```javascript
onPotentiallyUnhandledRejectionHandled = function (rejection) {
			enqueue(unreport, rejection);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.race"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>race (promises)](#apidoc.element.when.Promise.race)
- description and source-code
```javascript
function race(promises) {
			if(typeof promises !== 'object' || promises === null) {
				return reject(new TypeError('non-iterable passed to race()'));
			}

			// Sigh, race([]) is untestable unless we return *something*
			// that is recognizable without calling .then() on it.
			return promises.length === 0 ? never()
				 : promises.length === 1 ? resolve(promises[0])
				 : runRace(promises);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.reduce"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>reduce (promises, f)](#apidoc.element.when.Promise.reduce)
- description and source-code
```javascript
function reduce(promises, f) {
			return arguments.length > 2 ? ar.call(promises, liftCombine(f), arguments[2])
					: ar.call(promises, liftCombine(f));
		}
```
- example usage
```shell
...

The second example shows off the power that comes with when's promise logic. Here, we get an array of numbers from a remote source
 and reduce them. The example will print '150' if all went well, and if there was a problem will print a full stack trace.

'''js
var when = require('when');
var rest = require('rest');

when.reduce(when.map(getRemoteNumberList(), times10), sum)
.done(function(result) {
    console.log(result);
});

function getRemoteNumberList() {
// Get a remote array [1, 2, 3, 4, 5]
return rest('http://example.com/numbers').then(JSON.parse);
...
```

#### <a name="apidoc.element.when.Promise.reduceRight"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>reduceRight (promises, f)](#apidoc.element.when.Promise.reduceRight)
- description and source-code
```javascript
function reduceRight(promises, f) {
			return arguments.length > 2 ? arr.call(promises, liftCombine(f), arguments[2])
					: arr.call(promises, liftCombine(f));
		}
```
- example usage
```shell
...
	when.any         = lift(Promise.any);    // One-winner race
	when.some        = lift(Promise.some);   // Multi-winner race
	when.race        = lift(Promise.race);   // First-to-settle race

	when.map         = map;                  // Array.map() for promises
	when.filter      = filter;               // Array.filter() for promises
	when.reduce      = lift(Promise.reduce);       // Array.reduce() for promises
	when.reduceRight = lift(Promise.reduceRight);  // Array.reduceRight() for promises

	when.isPromiseLike = isPromiseLike;      // Is something promise-like, aka thenable

	when.Promise     = Promise;              // Promise constructor
	when.defer       = defer;                // Create a {promise, resolve, reject} tuple

	// Error types
...
```

#### <a name="apidoc.element.when.Promise.reject"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>reject (x)](#apidoc.element.when.Promise.reject)
- description and source-code
```javascript
function reject(x) {
			return new Promise(Handler, new Async(new Rejected(x)));
		}
```
- example usage
```shell
...
		return new Deferred();
	}

	function Deferred() {
		var p = Promise._defer();

		function resolve(x) { p._handler.resolve(x); }
		function reject(x) { p._handler.reject(x); }
		function notify(x) { p._handler.notify(x); }

		this.promise = p;
		this.resolve = resolve;
		this.reject = reject;
		this.notify = notify;
		this.resolver = { resolve: resolve, reject: reject, notify: notify };
...
```

#### <a name="apidoc.element.when.Promise.resolve"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>resolve (x)](#apidoc.element.when.Promise.resolve)
- description and source-code
```javascript
function resolve(x) {
			return isPromise(x) ? x
				: new Promise(Handler, new Async(getHandler(x)));
		}
```
- example usage
```shell
...
	 * @param {function?} onProgress callback to be called when progress updates
	 *   are issued for x. @deprecated
	 * @returns {Promise} a new promise that will fulfill with the return
	 *   value of callback or errback or the completion value of promiseOrValue if
	 *   callback and/or errback is not supplied.
	 */
	function when(x, onFulfilled, onRejected, onProgress) {
		var p = Promise.resolve(x);
		if (arguments.length < 2) {
			return p;
		}

		return p.then(onFulfilled, onRejected, onProgress);
	}
...
```

#### <a name="apidoc.element.when.Promise.settle"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>settle (promises)](#apidoc.element.when.Promise.settle)
- description and source-code
```javascript
function settle(promises) {
			return all(promises.map(settleOne));
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.some"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>some (promises, n)](#apidoc.element.when.Promise.some)
- description and source-code
```javascript
function some(promises, n) {
			<span class="apidocCodeCommentSpan">/*jshint maxcomplexity:7*/
</span>			var p = Promise._defer();
			var resolver = p._handler;

			var results = [];
			var errors = [];

			var l = promises.length>>>0;
			var nFulfill = 0;
			var nReject;
			var x, i; // reused in both for() loops

			// First pass: count actual array items
			for(i=0; i<l; ++i) {
				x = promises[i];
				if(x === void 0 && !(i in promises)) {
					continue;
				}
				++nFulfill;
			}

			// Compute actual goals
			n = Math.max(n, 0);
			nReject = (nFulfill - n + 1);
			nFulfill = Math.min(n, nFulfill);

			if(n > nFulfill) {
				resolver.reject(new RangeError('some(): array must contain at least '
				+ n + ' item(s), but had ' + nFulfill));
			} else if(nFulfill === 0) {
				resolver.resolve(results);
			}

			// Second pass: observe each array item, make progress toward goals
			for(i=0; i<l; ++i) {
				x = promises[i];
				if(x === void 0 && !(i in promises)) {
					continue;
				}

				Promise._handler(x).visit(resolver, fulfill, reject, resolver.notify);
			}

			return p;

			function fulfill(x) {
				/*jshint validthis:true*/
				if(this.resolved) { // this === resolver
					return;
				}

				results.push(x);
				if(--nFulfill === 0) {
					errors = null;
					this.resolve(results);
				}
			}

			function reject(e) {
				/*jshint validthis:true*/
				if(this.resolved) { // this === resolver
					return;
				}

				errors.push(e);
				if(--nReject === 0) {
					results = null;
					this.reject(errors);
				}
			}
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.unfold"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>unfold (unspool, condition, handler, x)](#apidoc.element.when.Promise.unfold)
- description and source-code
```javascript
function unfold(unspool, condition, handler, x) {
			return resolve(x).then(function(seed) {
				return resolve(condition(seed)).then(function(done) {
					return done ? seed : resolve(unspool(seed)).spread(next);
				});
			});

			function next(item, newSeed) {
				return resolve(handler(item)).then(function() {
					return unfold(unspool, condition, handler, newSeed);
				});
			}
		}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.Promise.prototype"></a>[module when.Promise.prototype](#apidoc.module.when.Promise.prototype)

#### <a name="apidoc.element.when.Promise.prototype._beget"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>_beget ()](#apidoc.element.when.Promise.prototype._beget)
- description and source-code
```javascript
_beget = function () {
			return begetFrom(this._handler, this.constructor);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.catch"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>catch (onRejected)](#apidoc.element.when.Promise.prototype.catch)
- description and source-code
```javascript
catch = function (onRejected) {
			if (arguments.length < 2) {
				return origCatch.call(this, onRejected);
			}

			if(typeof onRejected !== 'function') {
				return this.ensure(rejectInvalidPredicate);
			}

			return origCatch.call(this, createCatchFilter(arguments[1], onRejected));
		}
```
- example usage
```shell
...
This first example will print '"hello world!!!!"' if all went well, or '"drat!"' if there was a problem. It also uses [rest](https
://github.com/cujojs/rest) to make an ajax request to a (fictional) external service.

'''js
var rest = require('rest');

fetchRemoteGreeting()
.then(addExclamation)
.catch(handleError)
.done(function(greeting) {
    console.log(greeting);
});

function fetchRemoteGreeting() {
// returns a when.js promise for 'hello world'
return rest('http://example.com/greeting');
...
```

#### <a name="apidoc.element.when.Promise.prototype.delay"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>delay (ms)](#apidoc.element.when.Promise.prototype.delay)
- description and source-code
```javascript
delay = function (ms) {
			var p = this._beget();
			this._handler.fold(handleDelay, ms, void 0, p._handler);
			return p;
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.done"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>done (onResult, onError)](#apidoc.element.when.Promise.prototype.done)
- description and source-code
```javascript
done = function (onResult, onError) {
			this._handler.visit(this._handler.receiver, onResult, onError);
		}
```
- example usage
```shell
...

'''js
var rest = require('rest');

fetchRemoteGreeting()
    .then(addExclamation)
    .catch(handleError)
    .done(function(greeting) {
        console.log(greeting);
    });

function fetchRemoteGreeting() {
    // returns a when.js promise for 'hello world'
    return rest('http://example.com/greeting');
}
...
```

#### <a name="apidoc.element.when.Promise.prototype.else"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>else (defaultValue)](#apidoc.element.when.Promise.prototype.else)
- description and source-code
```javascript
else = function (defaultValue) {
			return this.then(void 0, function() {
				return defaultValue;
			});
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.ensure"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>ensure (handler)](#apidoc.element.when.Promise.prototype.ensure)
- description and source-code
```javascript
ensure = function (handler) {
			if(typeof handler !== 'function') {
				return this;
			}

			return this.then(function(x) {
				return runSideEffect(handler, this, identity, x);
			}, function(e) {
				return runSideEffect(handler, this, reject, e);
			});
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.finally"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>finally (handler)](#apidoc.element.when.Promise.prototype.finally)
- description and source-code
```javascript
finally = function (handler) {
			if(typeof handler !== 'function') {
				return this;
			}

			return this.then(function(x) {
				return runSideEffect(handler, this, identity, x);
			}, function(e) {
				return runSideEffect(handler, this, reject, e);
			});
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.fold"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>fold (f, z)](#apidoc.element.when.Promise.prototype.fold)
- description and source-code
```javascript
fold = function (f, z) {
			var promise = this._beget();

			this._handler.fold(function(z, x, to) {
				Promise._handler(z).fold(function(x, z, to) {
					to.resolve(f.call(this, z, x));
				}, x, this, to);
			}, z, promise._handler.receiver, promise._handler);

			return promise;
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.inspect"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>inspect ()](#apidoc.element.when.Promise.prototype.inspect)
- description and source-code
```javascript
inspect = function () {
			return inspect(Promise._handler(this));
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.orElse"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>orElse (defaultValue)](#apidoc.element.when.Promise.prototype.orElse)
- description and source-code
```javascript
orElse = function (defaultValue) {
			return this.then(void 0, function() {
				return defaultValue;
			});
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.otherwise"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>otherwise (onRejected)](#apidoc.element.when.Promise.prototype.otherwise)
- description and source-code
```javascript
otherwise = function (onRejected) {
			if (arguments.length < 2) {
				return origCatch.call(this, onRejected);
			}

			if(typeof onRejected !== 'function') {
				return this.ensure(rejectInvalidPredicate);
			}

			return origCatch.call(this, createCatchFilter(arguments[1], onRejected));
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.progress"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>progress (onProgress)](#apidoc.element.when.Promise.prototype.progress)
- description and source-code
```javascript
progress = function (onProgress) {
			return this.then(void 0, void 0, onProgress);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.spread"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>spread (onFulfilled)](#apidoc.element.when.Promise.prototype.spread)
- description and source-code
```javascript
spread = function (onFulfilled) {
			return this.then(all).then(function(array) {
				return onFulfilled.apply(this, array);
			});
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.tap"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>tap (onFulfilledSideEffect)](#apidoc.element.when.Promise.prototype.tap)
- description and source-code
```javascript
tap = function (onFulfilledSideEffect) {
			return this.then(onFulfilledSideEffect)['yield'](this);
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.then"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>then (onFulfilled, onRejected, onProgress)](#apidoc.element.when.Promise.prototype.then)
- description and source-code
```javascript
then = function (onFulfilled, onRejected, onProgress) {
			var parent = this._handler;
			var state = parent.join().state();

			if ((typeof onFulfilled !== 'function' && state > 0) ||
				(typeof onRejected !== 'function' && state < 0)) {
				// Short circuit: value will not change, simply share handler
				return new this.constructor(Handler, parent);
			}

			var p = this._beget();
			var child = p._handler;

			parent.chain(child, parent.receiver, onFulfilled, onRejected, onProgress);

			return p;
		}
```
- example usage
```shell
...

This first example will print '"hello world!!!!"' if all went well, or '"drat!"' if there was a problem. It also uses [rest](https
://github.com/cujojs/rest) to make an ajax request to a (fictional) external service.

'''js
var rest = require('rest');

fetchRemoteGreeting()
.then(addExclamation)
.catch(handleError)
.done(function(greeting) {
    console.log(greeting);
});

function fetchRemoteGreeting() {
// returns a when.js promise for 'hello world'
...
```

#### <a name="apidoc.element.when.Promise.prototype.timeout"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>timeout (ms, reason)](#apidoc.element.when.Promise.prototype.timeout)
- description and source-code
```javascript
timeout = function (ms, reason) {
			var p = this._beget();
			var h = p._handler;

			var t = setTimeout(onTimeout, ms, reason, p._handler);

			this._handler.visit(h,
				function onFulfill(x) {
					env.clearTimer(t);
					this.resolve(x); // this = h
				},
				function onReject(x) {
					env.clearTimer(t);
					this.reject(x); // this = h
				},
				h.notify);

			return p;
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.with"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>with (receiver)](#apidoc.element.when.Promise.prototype.with)
- description and source-code
```javascript
with = function (receiver) {
			var p = this._beget();
			var child = p._handler;
			child.receiver = receiver;
			this._handler.chain(child, receiver);
			return p;
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.withThis"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>withThis (receiver)](#apidoc.element.when.Promise.prototype.withThis)
- description and source-code
```javascript
withThis = function (receiver) {
			var p = this._beget();
			var child = p._handler;
			child.receiver = receiver;
			this._handler.chain(child, receiver);
			return p;
		}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Promise.prototype.yield"></a>[function <span class="apidocSignatureSpan">when.Promise.prototype.</span>yield (value)](#apidoc.element.when.Promise.prototype.yield)
- description and source-code
```javascript
yield = function (value) {
			return this.then(function() {
				return value;
			});
		}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.TimeoutError"></a>[module when.TimeoutError](#apidoc.module.when.TimeoutError)

#### <a name="apidoc.element.when.TimeoutError.TimeoutError"></a>[function <span class="apidocSignatureSpan">when.</span>TimeoutError (message)](#apidoc.element.when.TimeoutError.TimeoutError)
- description and source-code
```javascript
function TimeoutError(message) {
		Error.call(this);
		this.message = message;
		this.name = TimeoutError.name;
		if (typeof Error.captureStackTrace === 'function') {
			Error.captureStackTrace(this, TimeoutError);
		}
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.TimeoutError.prototype"></a>[module when.TimeoutError.prototype](#apidoc.module.when.TimeoutError.prototype)

#### <a name="apidoc.element.when.TimeoutError.prototype.constructor"></a>[function <span class="apidocSignatureSpan">when.TimeoutError.prototype.</span>constructor (message)](#apidoc.element.when.TimeoutError.prototype.constructor)
- description and source-code
```javascript
function TimeoutError(message) {
		Error.call(this);
		this.message = message;
		this.name = TimeoutError.name;
		if (typeof Error.captureStackTrace === 'function') {
			Error.captureStackTrace(this, TimeoutError);
		}
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.callbacks"></a>[module when.callbacks](#apidoc.module.when.callbacks)

#### <a name="apidoc.element.when.callbacks.apply"></a>[function <span class="apidocSignatureSpan">when.callbacks.</span>apply (asyncFunction, extraAsyncArgs)](#apidoc.element.when.callbacks.apply)
- description and source-code
```javascript
function apply(asyncFunction, extraAsyncArgs) {
		return _apply(asyncFunction, this, extraAsyncArgs || []);
	}
```
- example usage
```shell
...
	 * Takes a 'traditional' callback-taking function and returns a promise for its
	 * result, accepting an optional array of arguments (that might be values or
	 * promises). It assumes that the function takes its callback and errback as
	 * the last two arguments. The resolution of the promise depends on whether the
	 * function will call its callback or its errback.
	 *
	 * @example
	 *    var domIsLoaded = callbacks.apply($);
	 *    domIsLoaded.then(function() {
	 *		doMyDomStuff();
	 *	});
	 *
	 * @example
	 *    function existingAjaxyFunction(url, callback, errback) {
	 *		// Complex logic you'd rather not change
...
```

#### <a name="apidoc.element.when.callbacks.call"></a>[function <span class="apidocSignatureSpan">when.callbacks.</span>call (asyncFunction)](#apidoc.element.when.callbacks.call)
- description and source-code
```javascript
function call(asyncFunction) {
		return _apply(asyncFunction, this, slice.call(arguments, 1));
	}
```
- example usage
```shell
...
	 * @example
	 *    function sumInFiveSeconds(a, b, callback) {
	 *		setTimeout(function() {
	 *			callback(a + b);
	 *		}, 5000);
	 *	}
	 *
	 *    var sumPromise = callbacks.call(sumInFiveSeconds, 5, 10);
	 *
	 *    // Logs '15' 5 seconds later
	 *    sumPromise.then(console.log);
	 *
	 * @param {function} asyncFunction function to be called
	 * @param {...*} args arguments that will be forwarded to the function
	 * @returns {Promise} promise for the callback value of asyncFunction
...
```

#### <a name="apidoc.element.when.callbacks.lift"></a>[function <span class="apidocSignatureSpan">when.callbacks.</span>lift (f)](#apidoc.element.when.callbacks.lift)
- description and source-code
```javascript
function lift(f) {
		var args = arguments.length > 1 ? slice.call(arguments, 1) : [];
		return function() {
			return _apply(f, this, args.concat(slice.call(arguments)));
		};
	}
```
- example usage
```shell
...
	 *
	 *		xhr.onload = callback;
	 *		xhr.onerror = errback;
	 *
	 *		xhr.send();
	 *	}
	 *
	 *    var promiseAjax = callbacks.lift(traditionalAjax);
	 *    promiseAjax("GET", "/movies.json").then(console.log, console.error);
	 *
	 *    var promiseAjaxGet = callbacks.lift(traditionalAjax, "GET");
	 *    promiseAjaxGet("/movies.json").then(console.log, console.error);
	 *
	 * @param {Function} f traditional async function to be decorated
	 * @param {...*} [args] arguments to be prepended for the new function @deprecated
...
```

#### <a name="apidoc.element.when.callbacks.liftAll"></a>[function <span class="apidocSignatureSpan">when.callbacks.</span>liftAll (src, combine, dst)](#apidoc.element.when.callbacks.liftAll)
- description and source-code
```javascript
function liftAll(src, combine, dst) {
		return _liftAll(lift, combine, dst, src);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.callbacks.promisify"></a>[function <span class="apidocSignatureSpan">when.callbacks.</span>promisify (asyncFunction, positions)](#apidoc.element.when.callbacks.promisify)
- description and source-code
```javascript
function promisify(asyncFunction, positions) {

		return function() {
			var thisArg = this;
			return Promise.all(arguments).then(function(args) {
				var p = Promise._defer();

				var callbackPos, errbackPos;

				if(typeof positions.callback === 'number') {
					callbackPos = normalizePosition(args, positions.callback);
				}

				if(typeof positions.errback === 'number') {
					errbackPos = normalizePosition(args, positions.errback);
				}

				if(errbackPos < callbackPos) {
					insertCallback(args, errbackPos, p._handler.reject, p._handler);
					insertCallback(args, callbackPos, p._handler.resolve, p._handler);
				} else {
					insertCallback(args, callbackPos, p._handler.resolve, p._handler);
					insertCallback(args, errbackPos, p._handler.reject, p._handler);
				}

				asyncFunction.apply(thisArg, args);

				return p;
			});
		};
	}
```
- example usage
```shell
...
	 * of the arguments array.
	 *
	 * If arguments are given on the call to the 'promisified' function, they are
	 * intermingled with the callback and errback. If a promise is given among them,
	 * the execution of the function will only occur after its resolution.
	 *
	 * @example
	 *    var delay = callbacks.promisify(setTimeout, {
	 *		callback: 0
	 *	});
	 *
	 *    delay(100).then(function() {
	 *		console.log("This happens 100ms afterwards");
	 *	});
	 *
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
