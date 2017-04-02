# api documentation for  [when (v3.7.8)](http://cujojs.com)  [![npm package](https://img.shields.io/npm/v/npmdoc-when.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-when) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-when.svg)](https://travis-ci.org/npmdoc/node-npmdoc-when)
#### A lightweight Promises/A+ and when() implementation, plus other async goodies.

[![NPM](https://nodei.co/npm/when.png?downloads=true)](https://www.npmjs.com/package/when)

[![apidoc](https://npmdoc.github.io/node-npmdoc-when/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-when_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-when/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-when/build/screen-capture.npmPackageListing.svg)



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
            "name": "cujojs",
            "email": "info@cujojs.com"
        }
    ],
    "name": "when",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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
1.  [function <span class="apidocSignatureSpan">when.</span>ConsoleReporter ()](#apidoc.element.when.ConsoleReporter)
1.  [function <span class="apidocSignatureSpan">when.</span>Promise (resolver, handler)](#apidoc.element.when.Promise)
1.  [function <span class="apidocSignatureSpan">when.</span>PromiseMonitor (reporter)](#apidoc.element.when.PromiseMonitor)
1.  [function <span class="apidocSignatureSpan">when.</span>Scheduler (async)](#apidoc.element.when.Scheduler)
1.  [function <span class="apidocSignatureSpan">when.</span>TimeoutError (message)](#apidoc.element.when.TimeoutError)
1.  [function <span class="apidocSignatureSpan">when.</span>all (promises)](#apidoc.element.when.all)
1.  [function <span class="apidocSignatureSpan">when.</span>any ()](#apidoc.element.when.any)
1.  [function <span class="apidocSignatureSpan">when.</span>apply (Promise, call)](#apidoc.element.when.apply)
1.  [function <span class="apidocSignatureSpan">when.</span>attempt (f)](#apidoc.element.when.attempt)
1.  [function <span class="apidocSignatureSpan">when.</span>defer ()](#apidoc.element.when.defer)
1.  [function <span class="apidocSignatureSpan">when.</span>filter (promises, predicate)](#apidoc.element.when.filter)
1.  [function <span class="apidocSignatureSpan">when.</span>guard (condition, f)](#apidoc.element.when.guard)
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
1.  [function <span class="apidocSignatureSpan">when.</span>try (f)](#apidoc.element.when.try)
1.  [function <span class="apidocSignatureSpan">when.</span>unfold (unspool, condition, handler, x)](#apidoc.element.when.unfold)
1.  object <span class="apidocSignatureSpan">when.</span>ConsoleReporter.prototype
1.  object <span class="apidocSignatureSpan">when.</span>Promise.prototype
1.  object <span class="apidocSignatureSpan">when.</span>PromiseMonitor.prototype
1.  object <span class="apidocSignatureSpan">when.</span>Scheduler.prototype
1.  object <span class="apidocSignatureSpan">when.</span>TimeoutError.prototype
1.  object <span class="apidocSignatureSpan">when.</span>callbacks
1.  object <span class="apidocSignatureSpan">when.</span>console
1.  object <span class="apidocSignatureSpan">when.</span>env
1.  object <span class="apidocSignatureSpan">when.</span>error
1.  object <span class="apidocSignatureSpan">when.</span>format
1.  object <span class="apidocSignatureSpan">when.</span>function
1.  object <span class="apidocSignatureSpan">when.</span>generator
1.  object <span class="apidocSignatureSpan">when.</span>keys
1.  object <span class="apidocSignatureSpan">when.</span>node
1.  object <span class="apidocSignatureSpan">when.</span>state

#### [module when.ConsoleReporter](#apidoc.module.when.ConsoleReporter)
1.  [function <span class="apidocSignatureSpan">when.</span>ConsoleReporter ()](#apidoc.element.when.ConsoleReporter.ConsoleReporter)

#### [module when.ConsoleReporter.prototype](#apidoc.module.when.ConsoleReporter.prototype)
1.  [function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>_log (traces)](#apidoc.element.when.ConsoleReporter.prototype._log)
1.  [function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>groupEnd ()](#apidoc.element.when.ConsoleReporter.prototype.groupEnd)
1.  [function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>groupStart (s)](#apidoc.element.when.ConsoleReporter.prototype.groupStart)
1.  [function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>log (traces)](#apidoc.element.when.ConsoleReporter.prototype.log)
1.  [function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>msg (s)](#apidoc.element.when.ConsoleReporter.prototype.msg)
1.  [function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>warn (s)](#apidoc.element.when.ConsoleReporter.prototype.warn)

#### [module when.Promise](#apidoc.module.when.Promise)
1.  [function <span class="apidocSignatureSpan">when.</span>Promise (resolver, handler)](#apidoc.element.when.Promise.Promise)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_defer ()](#apidoc.element.when.Promise._defer)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_handler (x)](#apidoc.element.when.Promise._handler)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_traverse (f, promises)](#apidoc.element.when.Promise._traverse)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>_visitRemaining (promises, start, handler)](#apidoc.element.when.Promise._visitRemaining)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>all (promises)](#apidoc.element.when.Promise.all)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>any (promises)](#apidoc.element.when.Promise.any)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>createContext (p, context)](#apidoc.element.when.Promise.createContext)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>enterContext (p)](#apidoc.element.when.Promise.enterContext)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>exitContext ()](#apidoc.element.when.Promise.exitContext)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>filter (promises, predicate)](#apidoc.element.when.Promise.filter)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>iterate (f, condition, handler, x)](#apidoc.element.when.Promise.iterate)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>map (promises, f)](#apidoc.element.when.Promise.map)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>never ()](#apidoc.element.when.Promise.never)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>onFatalRejection (rejection, extraContext)](#apidoc.element.when.Promise.onFatalRejection)
1.  [function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejection (rejection, extraContext)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejection)
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

#### [module when.PromiseMonitor](#apidoc.module.when.PromiseMonitor)
1.  [function <span class="apidocSignatureSpan">when.</span>PromiseMonitor (reporter)](#apidoc.element.when.PromiseMonitor.PromiseMonitor)

#### [module when.PromiseMonitor.prototype](#apidoc.module.when.PromiseMonitor.prototype)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_appendContext (trace, context)](#apidoc.element.when.PromiseMonitor.prototype._appendContext)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_createLongTrace (e, context, extraContext)](#apidoc.element.when.PromiseMonitor.prototype._createLongTrace)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_createTrace (traceChain)](#apidoc.element.when.PromiseMonitor.prototype._createTrace)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_logTraces ()](#apidoc.element.when.PromiseMonitor.prototype._logTraces)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_removeDuplicates (trace)](#apidoc.element.when.PromiseMonitor.prototype._removeDuplicates)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>addTrace (handler, extraContext)](#apidoc.element.when.PromiseMonitor.prototype.addTrace)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>createContext (at, parentContext)](#apidoc.element.when.PromiseMonitor.prototype.createContext)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>fatal (handler, extraContext)](#apidoc.element.when.PromiseMonitor.prototype.fatal)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>formatTraces (traces)](#apidoc.element.when.PromiseMonitor.prototype.formatTraces)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>logTraces ()](#apidoc.element.when.PromiseMonitor.prototype.logTraces)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>monitor (Promise)](#apidoc.element.when.PromiseMonitor.prototype.monitor)
1.  [function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>removeTrace ()](#apidoc.element.when.PromiseMonitor.prototype.removeTrace)

#### [module when.Scheduler](#apidoc.module.when.Scheduler)
1.  [function <span class="apidocSignatureSpan">when.</span>Scheduler (async)](#apidoc.element.when.Scheduler.Scheduler)

#### [module when.Scheduler.prototype](#apidoc.module.when.Scheduler.prototype)
1.  [function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>_drain ()](#apidoc.element.when.Scheduler.prototype._drain)
1.  [function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>afterQueue (task)](#apidoc.element.when.Scheduler.prototype.afterQueue)
1.  [function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>enqueue (task)](#apidoc.element.when.Scheduler.prototype.enqueue)
1.  [function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>run ()](#apidoc.element.when.Scheduler.prototype.run)

#### [module when.TimeoutError](#apidoc.module.when.TimeoutError)
1.  [function <span class="apidocSignatureSpan">when.</span>TimeoutError (message)](#apidoc.element.when.TimeoutError.TimeoutError)

#### [module when.TimeoutError.prototype](#apidoc.module.when.TimeoutError.prototype)
1.  [function <span class="apidocSignatureSpan">when.TimeoutError.prototype.</span>constructor (message)](#apidoc.element.when.TimeoutError.prototype.constructor)

#### [module when.apply](#apidoc.module.when.apply)
1.  [function <span class="apidocSignatureSpan">when.</span>apply ()](#apidoc.element.when.apply.apply)
1.  [function <span class="apidocSignatureSpan">when.apply.</span>tryCatchResolve (f, thisArg, args, resolver)](#apidoc.element.when.apply.tryCatchResolve)

#### [module when.callbacks](#apidoc.module.when.callbacks)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>apply (asyncFunction, extraAsyncArgs)](#apidoc.element.when.callbacks.apply)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>call (asyncFunction)](#apidoc.element.when.callbacks.call)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>lift (f)](#apidoc.element.when.callbacks.lift)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>liftAll (src, combine, dst)](#apidoc.element.when.callbacks.liftAll)
1.  [function <span class="apidocSignatureSpan">when.callbacks.</span>promisify (asyncFunction, positions)](#apidoc.element.when.callbacks.promisify)

#### [module when.console](#apidoc.module.when.console)
1.  boolean <span class="apidocSignatureSpan">when.console.</span>filterDuplicateFrames
1.  [function <span class="apidocSignatureSpan">when.console.</span>_doLogTraces ()](#apidoc.element.when.console._doLogTraces)
1.  number <span class="apidocSignatureSpan">when.console.</span>_traceTask
1.  number <span class="apidocSignatureSpan">when.console.</span>logDelay
1.  object <span class="apidocSignatureSpan">when.console.</span>_reporter
1.  object <span class="apidocSignatureSpan">when.console.</span>_traces
1.  object <span class="apidocSignatureSpan">when.console.</span>stackFilter
1.  string <span class="apidocSignatureSpan">when.console.</span>stackJumpSeparator

#### [module when.env](#apidoc.module.when.env)
1.  [function <span class="apidocSignatureSpan">when.env.</span>asap (f)](#apidoc.element.when.env.asap)
1.  [function <span class="apidocSignatureSpan">when.env.</span>clearTimer (t)](#apidoc.element.when.env.clearTimer)
1.  [function <span class="apidocSignatureSpan">when.env.</span>setTimer (f, ms)](#apidoc.element.when.env.setTimer)

#### [module when.error](#apidoc.module.when.error)
1.  [function <span class="apidocSignatureSpan">when.error.</span>captureStack ()](#apidoc.element.when.error.captureStack)
1.  [function <span class="apidocSignatureSpan">when.error.</span>format (longTrace)](#apidoc.element.when.error.format)
1.  [function <span class="apidocSignatureSpan">when.error.</span>parse (e)](#apidoc.element.when.error.parse)

#### [module when.format](#apidoc.module.when.format)
1.  [function <span class="apidocSignatureSpan">when.format.</span>formatError (e)](#apidoc.element.when.format.formatError)
1.  [function <span class="apidocSignatureSpan">when.format.</span>formatObject (o)](#apidoc.element.when.format.formatObject)
1.  [function <span class="apidocSignatureSpan">when.format.</span>tryStringify (x, defaultValue)](#apidoc.element.when.format.tryStringify)

#### [module when.function](#apidoc.module.when.function)
1.  [function <span class="apidocSignatureSpan">when.function.</span>apply (f, args)](#apidoc.element.when.function.apply)
1.  [function <span class="apidocSignatureSpan">when.function.</span>call (f)](#apidoc.element.when.function.call)
1.  [function <span class="apidocSignatureSpan">when.function.</span>compose (f)](#apidoc.element.when.function.compose)
1.  [function <span class="apidocSignatureSpan">when.function.</span>lift (f)](#apidoc.element.when.function.lift)
1.  [function <span class="apidocSignatureSpan">when.function.</span>liftAll (src, combine, dst)](#apidoc.element.when.function.liftAll)

#### [module when.generator](#apidoc.module.when.generator)
1.  [function <span class="apidocSignatureSpan">when.generator.</span>apply (generator, args)](#apidoc.element.when.generator.apply)
1.  [function <span class="apidocSignatureSpan">when.generator.</span>call (generator)](#apidoc.element.when.generator.call)
1.  [function <span class="apidocSignatureSpan">when.generator.</span>lift (generator)](#apidoc.element.when.generator.lift)

#### [module when.guard](#apidoc.module.when.guard)
1.  [function <span class="apidocSignatureSpan">when.</span>guard (condition, f)](#apidoc.element.when.guard.guard)
1.  [function <span class="apidocSignatureSpan">when.guard.</span>n (allowed)](#apidoc.element.when.guard.n)

#### [module when.keys](#apidoc.module.when.keys)
1.  [function <span class="apidocSignatureSpan">when.keys.</span>all ()](#apidoc.element.when.keys.all)
1.  [function <span class="apidocSignatureSpan">when.keys.</span>map (object, f)](#apidoc.element.when.keys.map)
1.  [function <span class="apidocSignatureSpan">when.keys.</span>settle (object)](#apidoc.element.when.keys.settle)

#### [module when.node](#apidoc.module.when.node)
1.  [function <span class="apidocSignatureSpan">when.node.</span>apply (f, args)](#apidoc.element.when.node.apply)
1.  [function <span class="apidocSignatureSpan">when.node.</span>bindCallback (promise, callback)](#apidoc.element.when.node.bindCallback)
1.  [function <span class="apidocSignatureSpan">when.node.</span>call (f)](#apidoc.element.when.node.call)
1.  [function <span class="apidocSignatureSpan">when.node.</span>createCallback (resolver)](#apidoc.element.when.node.createCallback)
1.  [function <span class="apidocSignatureSpan">when.node.</span>lift (f)](#apidoc.element.when.node.lift)
1.  [function <span class="apidocSignatureSpan">when.node.</span>liftAll (src, combine, dst)](#apidoc.element.when.node.liftAll)
1.  [function <span class="apidocSignatureSpan">when.node.</span>liftCallback (callback)](#apidoc.element.when.node.liftCallback)

#### [module when.state](#apidoc.module.when.state)
1.  [function <span class="apidocSignatureSpan">when.state.</span>fulfilled (x)](#apidoc.element.when.state.fulfilled)
1.  [function <span class="apidocSignatureSpan">when.state.</span>inspect (handler)](#apidoc.element.when.state.inspect)
1.  [function <span class="apidocSignatureSpan">when.state.</span>pending ()](#apidoc.element.when.state.pending)
1.  [function <span class="apidocSignatureSpan">when.state.</span>rejected (e)](#apidoc.element.when.state.rejected)



# <a name="apidoc.module.when"></a>[module when](#apidoc.module.when)

#### <a name="apidoc.element.when.ConsoleReporter"></a>[function <span class="apidocSignatureSpan">when.</span>ConsoleReporter ()](#apidoc.element.when.ConsoleReporter)
- description and source-code
```javascript
function ConsoleReporter() {
		this._previouslyReported = false;
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

#### <a name="apidoc.element.when.PromiseMonitor"></a>[function <span class="apidocSignatureSpan">when.</span>PromiseMonitor (reporter)](#apidoc.element.when.PromiseMonitor)
- description and source-code
```javascript
function PromiseMonitor(reporter) {
		this.logDelay = 0;
		this.stackFilter = defaultStackFilter;
		this.stackJumpSeparator = defaultStackJumpSeparator;
		this.filterDuplicateFrames = true;

		this._reporter = reporter;
		if(typeof reporter.configurePromiseMonitor === 'function') {
			reporter.configurePromiseMonitor(this);
		}

		this._traces = [];
		this._traceTask = 0;

		var self = this;
		this._doLogTraces = function() {
			self._logTraces();
		};
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.Scheduler"></a>[function <span class="apidocSignatureSpan">when.</span>Scheduler (async)](#apidoc.element.when.Scheduler)
- description and source-code
```javascript
function Scheduler(async) {
		this._async = async;
		this._running = false;

		this._queue = this;
		this._queueLen = 0;
		this._afterQueue = {};
		this._afterQueueLen = 0;

		var self = this;
		this.drain = function() {
			self._drain();
		};
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

#### <a name="apidoc.element.when.apply"></a>[function <span class="apidocSignatureSpan">when.</span>apply (Promise, call)](#apidoc.element.when.apply)
- description and source-code
```javascript
function makeApply(Promise, call) {
		if(arguments.length < 2) {
			call = tryCatchResolve;
		}

		return apply;

		function apply(f, thisArg, args) {
			var p = Promise._defer();
			var l = args.length;
			var params = new Array(l);
			callAndResolve({ f:f, thisArg:thisArg, args:args, params:params, i:l-1, call:call }, p._handler);

			return p;
		}

		function callAndResolve(c, h) {
			if(c.i < 0) {
				return call(c.f, c.thisArg, c.params, h);
			}

			var handler = Promise._handler(c.args[c.i]);
			handler.fold(callAndResolveNext, c, void 0, h);
		}

		function callAndResolveNext(c, x, h) {
			c.params[c.i] = x;
			c.i -= 1;
			callAndResolve(c, h);
		}
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
...
 * Decorator that makes a deferred "cancelable".  It adds a cancel() method that
 * will call a special cancel handler function and then reject the deferred.  The
 * cancel handler can be used to do resource cleanup, or anything else that should
 * be done before any other rejection handlers are executed.
 *
 * Usage:
 *
 * var cancelableDeferred = cancelable(when.defer(), myCancelHandler);
 *
 * @author brian@hovercraftstudios.com
 */

(function(define) {
define(function() {
...
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

#### <a name="apidoc.element.when.guard"></a>[function <span class="apidocSignatureSpan">when.</span>guard (condition, f)](#apidoc.element.when.guard)
- description and source-code
```javascript
function guard(condition, f) {
		return function() {
			var args = slice.call(arguments);

			return when(condition()).withThis(this).then(function(exit) {
				return when(f.apply(this, args))['finally'](exit);
			});
		};
	}
```
- example usage
```shell
n/a
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
...
		 * @param {function=} onFulfilled fulfillment handler
		 * @param {function=} onRejected rejection handler
		 * @param {function=} onProgress @deprecated progress handler
		 * @return {Promise} new promise
		 */
		Promise.prototype.then = function(onFulfilled, onRejected, onProgress) {
			var parent = this._handler;
			var state = parent.join().state();

			if ((typeof onFulfilled !== 'function' && state > 0) ||
				(typeof onRejected !== 'function' && state < 0)) {
				// Short circuit: value will not change, simply share handler
				return new this.constructor(Handler, parent);
			}
...
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
...
	 *  section has been exited.
	 */
	function n(allowed) {
		var count = 0;
		var waiting = [];

		return function enter() {
			return when.promise(function(resolve) {
				if(count < allowed) {
					resolve(exit);
				} else {
					waiting.push(resolve);
				}
				count += 1;
			});
...
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
...
			return toPromise(results);
		}

		var p = Promise._defer();
		var resolver = Promise._handler(p);
		var promises = keys.map(function(k) { return object[k]; });

		when.settle(promises).then(function(states) {
			populateResults(keys, states, results, resolver);
		});

		return p;
	}

	function populateResults(keys, states, results, resolver) {
...
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



# <a name="apidoc.module.when.ConsoleReporter"></a>[module when.ConsoleReporter](#apidoc.module.when.ConsoleReporter)

#### <a name="apidoc.element.when.ConsoleReporter.ConsoleReporter"></a>[function <span class="apidocSignatureSpan">when.</span>ConsoleReporter ()](#apidoc.element.when.ConsoleReporter.ConsoleReporter)
- description and source-code
```javascript
function ConsoleReporter() {
		this._previouslyReported = false;
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.ConsoleReporter.prototype"></a>[module when.ConsoleReporter.prototype](#apidoc.module.when.ConsoleReporter.prototype)

#### <a name="apidoc.element.when.ConsoleReporter.prototype._log"></a>[function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>_log (traces)](#apidoc.element.when.ConsoleReporter.prototype._log)
- description and source-code
```javascript
_log = function (traces) {
		for(var i=0; i<traces.length; ++i) {
			this.warn(error.format(traces[i]));
		}
	}
```
- example usage
```shell
...
			}
			return;
		}

		this._previouslyReported = true;
		this.groupStart(unhandledRejectionsMsg + traces.length);
		try {
			this._log(traces);
		} finally {
			this.groupEnd();
		}
	};

	ConsoleReporter.prototype._log = function(traces) {
		for(var i=0; i<traces.length; ++i) {
...
```

#### <a name="apidoc.element.when.ConsoleReporter.prototype.groupEnd"></a>[function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>groupEnd ()](#apidoc.element.when.ConsoleReporter.prototype.groupEnd)
- description and source-code
```javascript
function consoleNotAvailable() {}
```
- example usage
```shell
...
		}

		this._previouslyReported = true;
		this.groupStart(unhandledRejectionsMsg + traces.length);
		try {
			this._log(traces);
		} finally {
			this.groupEnd();
		}
	};

	ConsoleReporter.prototype._log = function(traces) {
		for(var i=0; i<traces.length; ++i) {
			this.warn(error.format(traces[i]));
		}
...
```

#### <a name="apidoc.element.when.ConsoleReporter.prototype.groupStart"></a>[function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>groupStart (s)](#apidoc.element.when.ConsoleReporter.prototype.groupStart)
- description and source-code
```javascript
groupStart = function (s) {
					localConsole.error(s);
				}
```
- example usage
```shell
...
				this._previouslyReported = false;
				this.msg(allHandledMsg);
			}
			return;
		}

		this._previouslyReported = true;
		this.groupStart(unhandledRejectionsMsg + traces.length);
		try {
			this._log(traces);
		} finally {
			this.groupEnd();
		}
	};
...
```

#### <a name="apidoc.element.when.ConsoleReporter.prototype.log"></a>[function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>log (traces)](#apidoc.element.when.ConsoleReporter.prototype.log)
- description and source-code
```javascript
log = function (traces) {
		if(traces.length === 0) {
			if(this._previouslyReported) {
				this._previouslyReported = false;
				this.msg(allHandledMsg);
			}
			return;
		}

		this._previouslyReported = true;
		this.groupStart(unhandledRejectionsMsg + traces.length);
		try {
			this._log(traces);
		} finally {
			this.groupEnd();
		}
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

#### <a name="apidoc.element.when.ConsoleReporter.prototype.msg"></a>[function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>msg (s)](#apidoc.element.when.ConsoleReporter.prototype.msg)
- description and source-code
```javascript
msg = function (s) {
					localConsole.log(s);
				}
```
- example usage
```shell
...

	ConsoleReporter.prototype = initDefaultLogging();

	ConsoleReporter.prototype.log = function(traces) {
		if(traces.length === 0) {
			if(this._previouslyReported) {
				this._previouslyReported = false;
				this.msg(allHandledMsg);
			}
			return;
		}

		this._previouslyReported = true;
		this.groupStart(unhandledRejectionsMsg + traces.length);
		try {
...
```

#### <a name="apidoc.element.when.ConsoleReporter.prototype.warn"></a>[function <span class="apidocSignatureSpan">when.ConsoleReporter.prototype.</span>warn (s)](#apidoc.element.when.ConsoleReporter.prototype.warn)
- description and source-code
```javascript
warn = function (s) {
					localConsole.error(s);
				}
```
- example usage
```shell
...
		} finally {
			this.groupEnd();
		}
	};

	ConsoleReporter.prototype._log = function(traces) {
		for(var i=0; i<traces.length; ++i) {
			this.warn(error.format(traces[i]));
		}
	};

	function initDefaultLogging() {
		/*jshint maxcomplexity:7*/
		var log, warn, groupStart, groupEnd;
...
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
...
	}

	function handle(result, iterator) {
		if(result.done) {
			return result.value;
		}

		var h = Promise._handler(result.value);
		if(h.state() > 0) {
			return runNext(h.value, iterator);
		}

		var p = Promise._defer();
		h.chain(p._handler, iterator, next, error);
		return p;
...
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

#### <a name="apidoc.element.when.Promise.createContext"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>createContext (p, context)](#apidoc.element.when.Promise.createContext)
- description and source-code
```javascript
createContext = function (p, context) {
			p.context = self.createContext(p, context);
		}
```
- example usage
```shell
...
		var failIfRejected = new FailIfRejected();

		/**
		 * Handler that manages a queue of consumers waiting on a pending promise
		 * @constructor
		 */
		function Pending(receiver, inheritedContext) {
			Promise.createContext(this, inheritedContext);

			this.consumers = void 0;
			this.receiver = receiver;
			this.handler = void 0;
			this.resolved = false;
		}
...
```

#### <a name="apidoc.element.when.Promise.enterContext"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>enterContext (p)](#apidoc.element.when.Promise.enterContext)
- description and source-code
```javascript
enterContext = function (p) {
			executionContext.push(p.context);
		}
```
- example usage
```shell
...
		}

		function runContinuation1(f, h, receiver, next) {
			if(typeof f !== 'function') {
				return next.become(h);
			}

			Promise.enterContext(h);
			tryCatchReject(f, h.value, receiver, next);
			Promise.exitContext();
		}

		function runContinuation3(f, x, h, receiver, next) {
			if(typeof f !== 'function') {
				return next.become(h);
...
```

#### <a name="apidoc.element.when.Promise.exitContext"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>exitContext ()](#apidoc.element.when.Promise.exitContext)
- description and source-code
```javascript
exitContext = function () {
			executionContext.pop();
		}
```
- example usage
```shell
...
		function runContinuation1(f, h, receiver, next) {
			if(typeof f !== 'function') {
				return next.become(h);
			}

			Promise.enterContext(h);
			tryCatchReject(f, h.value, receiver, next);
			Promise.exitContext();
		}

		function runContinuation3(f, x, h, receiver, next) {
			if(typeof f !== 'function') {
				return next.become(h);
			}
...
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
...
		/**
		 * Fulfill-reject competitive race. Return a promise that will settle
		 * to the same state as the earliest input promise to settle.
		 *
		 * WARNING: The ES6 Promise spec requires that race()ing an empty array
		 * must return a promise that is pending forever.  This implementation
		 * returns a singleton forever-pending promise, the same singleton that is
		 * returned by Promise.never(), thus can be checked with ===
		 *
		 * @param {array} promises array of promises to race
		 * @returns {Promise} if input is non-empty, a promise that will settle
		 * to the same outcome as the earliest input promise to settle. if empty
		 * is empty, returns a promise that will never settle.
		 */
		function race(promises) {
...
```

#### <a name="apidoc.element.when.Promise.onFatalRejection"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>onFatalRejection (rejection, extraContext)](#apidoc.element.when.Promise.onFatalRejection)
- description and source-code
```javascript
onFatalRejection = function (rejection, extraContext) {
			return self.fatal(rejection, extraContext);
		}
```
- example usage
```shell
...
			this.handled = true;
			tasks.afterQueue(new UnreportTask(this));
		};

		Rejected.prototype.fail = function(context) {
			this.reported = true;
			emitRejection('unhandledRejection', this);
			Promise.onFatalRejection(this, context === void 0 ? this.context : context);
		};

		function ReportTask(rejection, context) {
			this.rejection = rejection;
			this.context = context;
		}
...
```

#### <a name="apidoc.element.when.Promise.onPotentiallyUnhandledRejection"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejection (rejection, extraContext)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejection)
- description and source-code
```javascript
onPotentiallyUnhandledRejection = function (rejection, extraContext) {
			return self.addTrace(rejection, extraContext);
		}
```
- example usage
```shell
...
			this.context = context;
		}

		ReportTask.prototype.run = function() {
			if(!this.rejection.handled && !this.rejection.reported) {
				this.rejection.reported = true;
				emitRejection('unhandledRejection', this.rejection) ||
					Promise.onPotentiallyUnhandledRejection(this.rejection, this.context);
			}
		};

		function UnreportTask(rejection) {
			this.rejection = rejection;
		}
...
```

#### <a name="apidoc.element.when.Promise.onPotentiallyUnhandledRejectionHandled"></a>[function <span class="apidocSignatureSpan">when.Promise.</span>onPotentiallyUnhandledRejectionHandled (rejection)](#apidoc.element.when.Promise.onPotentiallyUnhandledRejectionHandled)
- description and source-code
```javascript
onPotentiallyUnhandledRejectionHandled = function (rejection) {
			return self.removeTrace(rejection);
		}
```
- example usage
```shell
...
		function UnreportTask(rejection) {
			this.rejection = rejection;
		}

		UnreportTask.prototype.run = function() {
			if(this.rejection.reported) {
				emitRejection('rejectionHandled', this.rejection) ||
					Promise.onPotentiallyUnhandledRejectionHandled(this.rejection);
			}
		};

		// Unhandled rejection hooks
		// By default, everything is a noop

		Promise.createContext
...
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
...
			return toPromise(results);
		}

		var p = Promise._defer();
		var resolver = Promise._handler(p);
		var promises = keys.map(function(k) { return object[k]; });

		when.settle(promises).then(function(states) {
			populateResults(keys, states, results, resolver);
		});

		return p;
	}

	function populateResults(keys, states, results, resolver) {
...
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
...

			if ((typeof onFulfilled !== 'function' && state > 0) ||
				(typeof onRejected !== 'function' && state < 0)) {
				// Short circuit: value will not change, simply share handler
				return new this.constructor(Handler, parent);
			}

			var p = this._beget();
			var child = p._handler;

			parent.chain(child, parent.receiver, onFulfilled, onRejected, onProgress);

			return p;
		};
...
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
...

(function(define) {
define(function(require) {

	var when = require('./when');

    /**
	 * @deprecated Use when(value).delay(ms)
     */
    return function delay(msec, value) {
		return when(value).delay(msec);
    };

});
})(typeof define === 'function' && define.amd ? define : function (factory) { module.exports = factory(require); });
...
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
...

		function traverseAt(promises, handler, i, x, resolver) {
			if (maybeThenable(x)) {
				var h = getHandlerMaybeThenable(x);
				var s = h.state();

				if (s === 0) {
					h.fold(handler, i, void 0, resolver);
				} else if (s > 0) {
					handler(i, h.value, resolver);
				} else {
					resolver.become(h);
					visitRemaining(promises, i+1, h);
				}
			} else {
...
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
...

(function(define) {
define(function(require) {

	var when = require('./when');

    /**
	 * @deprecated Use when(trigger).timeout(ms)
     */
    return function timeout(msec, trigger) {
		return when(trigger).timeout(msec);
    };
});
})(typeof define === 'function' && define.amd ? define : function (factory) { module.exports = factory(require); });
...
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
...
	 * @param {function} f function to guard
	 * @returns {function} guarded version of f
	 */
	function guard(condition, f) {
		return function() {
			var args = slice.call(arguments);

			return when(condition()).withThis(this).then(function(exit) {
				return when(f.apply(this, args))['finally'](exit);
			});
		};
	}

	/**
	 * Creates a condition that allows only n simultaneous executions
...
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



# <a name="apidoc.module.when.PromiseMonitor"></a>[module when.PromiseMonitor](#apidoc.module.when.PromiseMonitor)

#### <a name="apidoc.element.when.PromiseMonitor.PromiseMonitor"></a>[function <span class="apidocSignatureSpan">when.</span>PromiseMonitor (reporter)](#apidoc.element.when.PromiseMonitor.PromiseMonitor)
- description and source-code
```javascript
function PromiseMonitor(reporter) {
		this.logDelay = 0;
		this.stackFilter = defaultStackFilter;
		this.stackJumpSeparator = defaultStackJumpSeparator;
		this.filterDuplicateFrames = true;

		this._reporter = reporter;
		if(typeof reporter.configurePromiseMonitor === 'function') {
			reporter.configurePromiseMonitor(this);
		}

		this._traces = [];
		this._traceTask = 0;

		var self = this;
		this._doLogTraces = function() {
			self._logTraces();
		};
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.PromiseMonitor.prototype"></a>[module when.PromiseMonitor.prototype](#apidoc.module.when.PromiseMonitor.prototype)

#### <a name="apidoc.element.when.PromiseMonitor.prototype._appendContext"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_appendContext (trace, context)](#apidoc.element.when.PromiseMonitor.prototype._appendContext)
- description and source-code
```javascript
_appendContext = function (trace, context) {
		trace.push.apply(trace, this._createTrace(context));
	}
```
- example usage
```shell
...
			return this._createLongTrace(t.handler.value, t.handler.context, t.extraContext);
		}, this);
	};

	PromiseMonitor.prototype._createLongTrace = function(e, context, extraContext) {
		var trace = error.parse(e) || [String(e) + ' (WARNING: non-Error used)'];
		trace = filterFrames(this.stackFilter, trace, 0);
		this._appendContext(trace, context);
		this._appendContext(trace, extraContext);
		return this.filterDuplicateFrames ? this._removeDuplicates(trace) : trace;
	};

	PromiseMonitor.prototype._removeDuplicates = function(trace) {
		var seen = {};
		var sep = this.stackJumpSeparator;
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype._createLongTrace"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_createLongTrace (e, context, extraContext)](#apidoc.element.when.PromiseMonitor.prototype._createLongTrace)
- description and source-code
```javascript
_createLongTrace = function (e, context, extraContext) {
		var trace = error.parse(e) || [String(e) + ' (WARNING: non-Error used)'];
		trace = filterFrames(this.stackFilter, trace, 0);
		this._appendContext(trace, context);
		this._appendContext(trace, extraContext);
		return this.filterDuplicateFrames ? this._removeDuplicates(trace) : trace;
	}
```
- example usage
```shell
...

	PromiseMonitor.prototype.removeTrace = function(/*handler*/) {
		this.logTraces();
	};

	PromiseMonitor.prototype.fatal = function(handler, extraContext) {
		var err = new Error();
		err.stack = this._createLongTrace(handler.value, handler.context, extraContext).join('\n');
		setTimer(function() {
			throw err;
		}, 0);
	};

	PromiseMonitor.prototype.logTraces = function() {
		if(!this._traceTask) {
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype._createTrace"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_createTrace (traceChain)](#apidoc.element.when.PromiseMonitor.prototype._createTrace)
- description and source-code
```javascript
_createTrace = function (traceChain) {
		var trace = [];
		var stack;

		while(traceChain) {
			stack = error.parse(traceChain);

			if (stack) {
				stack = filterFrames(this.stackFilter, stack);
				appendStack(trace, stack, this.stackJumpSeparator);
			}

			traceChain = traceChain.parent;
		}

		return trace;
	}
```
- example usage
```shell
...
				++count;
			}
			return deduped;
		}, []);
	};

	PromiseMonitor.prototype._appendContext = function(trace, context) {
		trace.push.apply(trace, this._createTrace(context));
	};

	PromiseMonitor.prototype._createTrace = function(traceChain) {
		var trace = [];
		var stack;

		while(traceChain) {
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype._logTraces"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_logTraces ()](#apidoc.element.when.PromiseMonitor.prototype._logTraces)
- description and source-code
```javascript
_logTraces = function () {
		this._traceTask = void 0;
		this._traces = this._traces.filter(filterHandled);
		this._reporter.log(this.formatTraces(this._traces));
	}
```
- example usage
```shell
...
		}

		this._traces = [];
		this._traceTask = 0;

		var self = this;
		this._doLogTraces = function() {
			self._logTraces();
		};
	}

	PromiseMonitor.prototype.monitor = function(Promise) {
		var self = this;
		Promise.createContext = function(p, context) {
			p.context = self.createContext(p, context);
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype._removeDuplicates"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>_removeDuplicates (trace)](#apidoc.element.when.PromiseMonitor.prototype._removeDuplicates)
- description and source-code
```javascript
_removeDuplicates = function (trace) {
		var seen = {};
		var sep = this.stackJumpSeparator;
		var count = 0;
		return trace.reduceRight(function(deduped, line, i) {
			if(i === 0) {
				deduped.unshift(line);
			} else if(line === sep) {
				if(count > 0) {
					deduped.unshift(line);
					count = 0;
				}
			} else if(!seen[line]) {
				seen[line] = true;
				deduped.unshift(line);
				++count;
			}
			return deduped;
		}, []);
	}
```
- example usage
```shell
...
	};

	PromiseMonitor.prototype._createLongTrace = function(e, context, extraContext) {
		var trace = error.parse(e) || [String(e) + ' (WARNING: non-Error used)'];
		trace = filterFrames(this.stackFilter, trace, 0);
		this._appendContext(trace, context);
		this._appendContext(trace, extraContext);
		return this.filterDuplicateFrames ? this._removeDuplicates(trace) : trace;
	};

	PromiseMonitor.prototype._removeDuplicates = function(trace) {
		var seen = {};
		var sep = this.stackJumpSeparator;
		var count = 0;
		return trace.reduceRight(function(deduped, line, i) {
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.addTrace"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>addTrace (handler, extraContext)](#apidoc.element.when.PromiseMonitor.prototype.addTrace)
- description and source-code
```javascript
addTrace = function (handler, extraContext) {
		var t, i;

		for(i = this._traces.length-1; i >= 0; --i) {
			t = this._traces[i];
			if(t.handler === handler) {
				break;
			}
		}

		if(i >= 0) {
			t.extraContext = extraContext;
		} else {
			this._traces.push({
				handler: handler,
				extraContext: extraContext
			});
		}

		this.logTraces();
	}
```
- example usage
```shell
...
		};

		Promise.exitContext = function() {
			executionContext.pop();
		};

		Promise.onPotentiallyUnhandledRejection = function(rejection, extraContext) {
			return self.addTrace(rejection, extraContext);
		};

		Promise.onPotentiallyUnhandledRejectionHandled = function(rejection) {
			return self.removeTrace(rejection);
		};

		Promise.onFatalRejection = function(rejection, extraContext) {
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.createContext"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>createContext (at, parentContext)](#apidoc.element.when.PromiseMonitor.prototype.createContext)
- description and source-code
```javascript
createContext = function (at, parentContext) {
		var context = {
			parent: parentContext || executionContext[executionContext.length - 1],
			stack: void 0
		};
		error.captureStack(context, at.constructor);
		return context;
	}
```
- example usage
```shell
...
		var failIfRejected = new FailIfRejected();

		/**
		 * Handler that manages a queue of consumers waiting on a pending promise
		 * @constructor
		 */
		function Pending(receiver, inheritedContext) {
			Promise.createContext(this, inheritedContext);

			this.consumers = void 0;
			this.receiver = receiver;
			this.handler = void 0;
			this.resolved = false;
		}
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.fatal"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>fatal (handler, extraContext)](#apidoc.element.when.PromiseMonitor.prototype.fatal)
- description and source-code
```javascript
fatal = function (handler, extraContext) {
		var err = new Error();
		err.stack = this._createLongTrace(handler.value, handler.context, extraContext).join('\n');
		setTimer(function() {
			throw err;
		}, 0);
	}
```
- example usage
```shell
...
		};

		Promise.onPotentiallyUnhandledRejectionHandled = function(rejection) {
			return self.removeTrace(rejection);
		};

		Promise.onFatalRejection = function(rejection, extraContext) {
			return self.fatal(rejection, extraContext);
		};

		return this;
	};

	PromiseMonitor.prototype.createContext = function(at, parentContext) {
		var context = {
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.formatTraces"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>formatTraces (traces)](#apidoc.element.when.PromiseMonitor.prototype.formatTraces)
- description and source-code
```javascript
formatTraces = function (traces) {
		return traces.map(function(t) {
			return this._createLongTrace(t.handler.value, t.handler.context, t.extraContext);
		}, this);
	}
```
- example usage
```shell
...
			this._traceTask = setTimer(this._doLogTraces, this.logDelay);
		}
	};

	PromiseMonitor.prototype._logTraces = function() {
		this._traceTask = void 0;
		this._traces = this._traces.filter(filterHandled);
		this._reporter.log(this.formatTraces(this._traces));
	};


	PromiseMonitor.prototype.formatTraces = function(traces) {
		return traces.map(function(t) {
			return this._createLongTrace(t.handler.value, t.handler.context, t.extraContext);
		}, this);
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.logTraces"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>logTraces ()](#apidoc.element.when.PromiseMonitor.prototype.logTraces)
- description and source-code
```javascript
logTraces = function () {
		if(!this._traceTask) {
			this._traceTask = setTimer(this._doLogTraces, this.logDelay);
		}
	}
```
- example usage
```shell
...
		} else {
			this._traces.push({
				handler: handler,
				extraContext: extraContext
			});
		}

		this.logTraces();
	};

	PromiseMonitor.prototype.removeTrace = function(/*handler*/) {
		this.logTraces();
	};

	PromiseMonitor.prototype.fatal = function(handler, extraContext) {
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.monitor"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>monitor (Promise)](#apidoc.element.when.PromiseMonitor.prototype.monitor)
- description and source-code
```javascript
monitor = function (Promise) {
		var self = this;
		Promise.createContext = function(p, context) {
			p.context = self.createContext(p, context);
		};

		Promise.enterContext = function(p) {
			executionContext.push(p.context);
		};

		Promise.exitContext = function() {
			executionContext.pop();
		};

		Promise.onPotentiallyUnhandledRejection = function(rejection, extraContext) {
			return self.addTrace(rejection, extraContext);
		};

		Promise.onPotentiallyUnhandledRejectionHandled = function(rejection) {
			return self.removeTrace(rejection);
		};

		Promise.onFatalRejection = function(rejection, extraContext) {
			return self.fatal(rejection, extraContext);
		};

		return this;
	}
```
- example usage
```shell
...

	var PromiseMonitor = require('./monitor/PromiseMonitor');
	var ConsoleReporter = require('./monitor/ConsoleReporter');

	var promiseMonitor = new PromiseMonitor(new ConsoleReporter());

	return function(Promise) {
		return promiseMonitor.monitor(Promise);
	};
});
}(typeof define === 'function' && define.amd ? define : function(factory) { module.exports = factory(require); }));
...
```

#### <a name="apidoc.element.when.PromiseMonitor.prototype.removeTrace"></a>[function <span class="apidocSignatureSpan">when.PromiseMonitor.prototype.</span>removeTrace ()](#apidoc.element.when.PromiseMonitor.prototype.removeTrace)
- description and source-code
```javascript
removeTrace = function () {
		this.logTraces();
	}
```
- example usage
```shell
...
		};

		Promise.onPotentiallyUnhandledRejection = function(rejection, extraContext) {
			return self.addTrace(rejection, extraContext);
		};

		Promise.onPotentiallyUnhandledRejectionHandled = function(rejection) {
			return self.removeTrace(rejection);
		};

		Promise.onFatalRejection = function(rejection, extraContext) {
			return self.fatal(rejection, extraContext);
		};

		return this;
...
```



# <a name="apidoc.module.when.Scheduler"></a>[module when.Scheduler](#apidoc.module.when.Scheduler)

#### <a name="apidoc.element.when.Scheduler.Scheduler"></a>[function <span class="apidocSignatureSpan">when.</span>Scheduler (async)](#apidoc.element.when.Scheduler.Scheduler)
- description and source-code
```javascript
function Scheduler(async) {
		this._async = async;
		this._running = false;

		this._queue = this;
		this._queueLen = 0;
		this._afterQueue = {};
		this._afterQueueLen = 0;

		var self = this;
		this.drain = function() {
			self._drain();
		};
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.Scheduler.prototype"></a>[module when.Scheduler.prototype](#apidoc.module.when.Scheduler.prototype)

#### <a name="apidoc.element.when.Scheduler.prototype._drain"></a>[function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>_drain ()](#apidoc.element.when.Scheduler.prototype._drain)
- description and source-code
```javascript
_drain = function () {
		var i = 0;
		for (; i < this._queueLen; ++i) {
			this._queue[i].run();
			this._queue[i] = void 0;
		}

		this._queueLen = 0;
		this._running = false;

		for (i = 0; i < this._afterQueueLen; ++i) {
			this._afterQueue[i].run();
			this._afterQueue[i] = void 0;
		}

		this._afterQueueLen = 0;
	}
```
- example usage
```shell
...
		this._queue = this;
		this._queueLen = 0;
		this._afterQueue = {};
		this._afterQueueLen = 0;

		var self = this;
		this.drain = function() {
			self._drain();
		};
	}

	/**
	 * Enqueue a task
	 * @param {{ run:function }} task
	 */
...
```

#### <a name="apidoc.element.when.Scheduler.prototype.afterQueue"></a>[function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>afterQueue (task)](#apidoc.element.when.Scheduler.prototype.afterQueue)
- description and source-code
```javascript
afterQueue = function (task) {
		this._afterQueue[this._afterQueueLen++] = task;
		this.run();
	}
```
- example usage
```shell
...
			if(typeof cont.rejected === 'function') {
				this._unreport();
			}
			runContinuation1(cont.rejected, this, cont.receiver, cont.resolver);
		};

		Rejected.prototype._report = function(context) {
			tasks.afterQueue(new ReportTask(this, context));
		};

		Rejected.prototype._unreport = function() {
			if(this.handled) {
				return;
			}
			this.handled = true;
...
```

#### <a name="apidoc.element.when.Scheduler.prototype.enqueue"></a>[function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>enqueue (task)](#apidoc.element.when.Scheduler.prototype.enqueue)
- description and source-code
```javascript
enqueue = function (task) {
		this._queue[this._queueLen++] = task;
		this.run();
	}
```
- example usage
```shell
...
			if(this.resolved) {
				return;
			}

			this.resolved = true;
			this.handler = handler;
			if(this.consumers !== void 0) {
				tasks.enqueue(this);
			}

			if(this.context !== void 0) {
				handler._report(this.context);
			}
		};
...
```

#### <a name="apidoc.element.when.Scheduler.prototype.run"></a>[function <span class="apidocSignatureSpan">when.Scheduler.prototype.</span>run ()](#apidoc.element.when.Scheduler.prototype.run)
- description and source-code
```javascript
run = function () {
		if (!this._running) {
			this._running = true;
			this._async(this.drain);
		}
	}
```
- example usage
```shell
...

	/**
	 * Enqueue a task
	 * @param {{ run:function }} task
	 */
	Scheduler.prototype.enqueue = function(task) {
		this._queue[this._queueLen++] = task;
		this.run();
	};

	/**
	 * Enqueue a task to run after the main task queue
	 * @param {{ run:function }} task
	 */
	Scheduler.prototype.afterQueue = function(task) {
...
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
...
		Promise.prototype.then = function(onFulfilled, onRejected, onProgress) {
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
...
```



# <a name="apidoc.module.when.apply"></a>[module when.apply](#apidoc.module.when.apply)

#### <a name="apidoc.element.when.apply.apply"></a>[function <span class="apidocSignatureSpan">when.</span>apply ()](#apidoc.element.when.apply.apply)
- description and source-code
```javascript
function apply() { [native code] }
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

#### <a name="apidoc.element.when.apply.tryCatchResolve"></a>[function <span class="apidocSignatureSpan">when.apply.</span>tryCatchResolve (f, thisArg, args, resolver)](#apidoc.element.when.apply.tryCatchResolve)
- description and source-code
```javascript
function tryCatchResolve(f, thisArg, args, resolver) {
		try {
			resolver.resolve(f.apply(thisArg, args));
		} catch(e) {
			resolver.reject(e);
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



# <a name="apidoc.module.when.console"></a>[module when.console](#apidoc.module.when.console)

#### <a name="apidoc.element.when.console._doLogTraces"></a>[function <span class="apidocSignatureSpan">when.console.</span>_doLogTraces ()](#apidoc.element.when.console._doLogTraces)
- description and source-code
```javascript
_doLogTraces = function () {
			self._logTraces();
		}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.env"></a>[module when.env](#apidoc.module.when.env)

#### <a name="apidoc.element.when.env.asap"></a>[function <span class="apidocSignatureSpan">when.env.</span>asap (f)](#apidoc.element.when.env.asap)
- description and source-code
```javascript
asap = function (f) { return process.nextTick(f); }
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.env.clearTimer"></a>[function <span class="apidocSignatureSpan">when.env.</span>clearTimer (t)](#apidoc.element.when.env.clearTimer)
- description and source-code
```javascript
clearTimer = function (t) { return clearTimeout(t); }
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.env.setTimer"></a>[function <span class="apidocSignatureSpan">when.env.</span>setTimer (f, ms)](#apidoc.element.when.env.setTimer)
- description and source-code
```javascript
setTimer = function (f, ms) { return setTimeout(f, ms); }
```
- example usage
```shell
...

	} else if (MutationObs = hasMutationObserver()) { // Modern browser
		asap = initMutationObserver(MutationObs);

	} else if (!capturedSetTimeout) { // vert.x
		var vertxRequire = require;
		var vertx = vertxRequire('vertx');
		setTimer = function (f, ms) { return vertx.setTimer(ms, f); };
		clearTimer = vertx.cancelTimer;
		asap = vertx.runOnLoop || vertx.runOnContext;
	}

	return {
		setTimer: setTimer,
		clearTimer: clearTimer,
...
```



# <a name="apidoc.module.when.error"></a>[module when.error](#apidoc.module.when.error)

#### <a name="apidoc.element.when.error.captureStack"></a>[function <span class="apidocSignatureSpan">when.error.</span>captureStack ()](#apidoc.element.when.error.captureStack)
- description and source-code
```javascript
function captureStackTrace() { [native code] }
```
- example usage
```shell
...
	};

	PromiseMonitor.prototype.createContext = function(at, parentContext) {
		var context = {
			parent: parentContext || executionContext[executionContext.length - 1],
			stack: void 0
		};
		error.captureStack(context, at.constructor);
		return context;
	};

	PromiseMonitor.prototype.addTrace = function(handler, extraContext) {
		var t, i;

		for(i = this._traces.length-1; i >= 0; --i) {
...
```

#### <a name="apidoc.element.when.error.format"></a>[function <span class="apidocSignatureSpan">when.error.</span>format (longTrace)](#apidoc.element.when.error.format)
- description and source-code
```javascript
function formatAsString(longTrace) {
		return join(longTrace);
	}
```
- example usage
```shell
...
		} finally {
			this.groupEnd();
		}
	};

	ConsoleReporter.prototype._log = function(traces) {
		for(var i=0; i<traces.length; ++i) {
			this.warn(error.format(traces[i]));
		}
	};

	function initDefaultLogging() {
		/*jshint maxcomplexity:7*/
		var log, warn, groupStart, groupEnd;
...
```

#### <a name="apidoc.element.when.error.parse"></a>[function <span class="apidocSignatureSpan">when.error.</span>parse (e)](#apidoc.element.when.error.parse)
- description and source-code
```javascript
parse = function (e) {
			return e && e.stack && e.stack.split('\n');
		}
```
- example usage
```shell
...
	PromiseMonitor.prototype.formatTraces = function(traces) {
		return traces.map(function(t) {
			return this._createLongTrace(t.handler.value, t.handler.context, t.extraContext);
		}, this);
	};

	PromiseMonitor.prototype._createLongTrace = function(e, context, extraContext) {
		var trace = error.parse(e) || [String(e) + ' (WARNING: non-Error used)'];
		trace = filterFrames(this.stackFilter, trace, 0);
		this._appendContext(trace, context);
		this._appendContext(trace, extraContext);
		return this.filterDuplicateFrames ? this._removeDuplicates(trace) : trace;
	};

	PromiseMonitor.prototype._removeDuplicates = function(trace) {
...
```



# <a name="apidoc.module.when.format"></a>[module when.format](#apidoc.module.when.format)

#### <a name="apidoc.element.when.format.formatError"></a>[function <span class="apidocSignatureSpan">when.format.</span>formatError (e)](#apidoc.element.when.format.formatError)
- description and source-code
```javascript
function formatError(e) {
		var s = typeof e === 'object' && e !== null && (e.stack || e.message) ? e.stack || e.message : formatObject(e);
		return e instanceof Error ? s : s + ' (WARNING: non-Error used)';
	}
```
- example usage
```shell
...
		var tasks = [];
		var reported = [];
		var running = null;

		function report(r) {
			if(!r.handled) {
				reported.push(r);
				logError('Potentially unhandled rejection [' + r.id + '] ' + format.formatError(r.value));
			}
		}

		function unreport(r) {
			var i = reported.indexOf(r);
			if(i >= 0) {
				reported.splice(i, 1);
...
```

#### <a name="apidoc.element.when.format.formatObject"></a>[function <span class="apidocSignatureSpan">when.format.</span>formatObject (o)](#apidoc.element.when.format.formatObject)
- description and source-code
```javascript
function formatObject(o) {
		var s = String(o);
		if(s === '[object Object]' && typeof JSON !== 'undefined') {
			s = tryStringify(o, s);
		}
		return s;
	}
```
- example usage
```shell
...
			}
		}

		function unreport(r) {
			var i = reported.indexOf(r);
			if(i >= 0) {
				reported.splice(i, 1);
				logInfo('Handled previous rejection [' + r.id + '] ' + format.formatObject(r.value));
			}
		}

		function enqueue(f, x) {
			tasks.push(f, x);
			if(running === null) {
				running = setTimer(flush, 0);
...
```

#### <a name="apidoc.element.when.format.tryStringify"></a>[function <span class="apidocSignatureSpan">when.format.</span>tryStringify (x, defaultValue)](#apidoc.element.when.format.tryStringify)
- description and source-code
```javascript
function tryStringify(x, defaultValue) {
		try {
			return JSON.stringify(x);
		} catch(e) {
			return defaultValue;
		}
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.function"></a>[module when.function](#apidoc.module.when.function)

#### <a name="apidoc.element.when.function.apply"></a>[function <span class="apidocSignatureSpan">when.function.</span>apply (f, args)](#apidoc.element.when.function.apply)
- description and source-code
```javascript
function apply(f, args) {
		// slice args just in case the caller passed an Arguments instance
		return _apply(f, this, args == null ? [] : slice.call(args));
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

#### <a name="apidoc.element.when.function.call"></a>[function <span class="apidocSignatureSpan">when.function.</span>call (f)](#apidoc.element.when.function.call)
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

#### <a name="apidoc.element.when.function.compose"></a>[function <span class="apidocSignatureSpan">when.function.</span>compose (f)](#apidoc.element.when.function.compose)
- description and source-code
```javascript
function compose(f) {
		var funcs = slice.call(arguments, 1);

		return function() {
			var thisArg = this;
			var args = slice.call(arguments);
			var firstPromise = attempt.apply(thisArg, [f].concat(args));

			return when.reduce(funcs, function(arg, func) {
				return func.call(thisArg, arg);
			}, firstPromise);
		};
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.function.lift"></a>[function <span class="apidocSignatureSpan">when.function.</span>lift (f)](#apidoc.element.when.function.lift)
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

#### <a name="apidoc.element.when.function.liftAll"></a>[function <span class="apidocSignatureSpan">when.function.</span>liftAll (src, combine, dst)](#apidoc.element.when.function.liftAll)
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



# <a name="apidoc.module.when.generator"></a>[module when.generator](#apidoc.module.when.generator)

#### <a name="apidoc.element.when.generator.apply"></a>[function <span class="apidocSignatureSpan">when.generator.</span>apply (generator, args)](#apidoc.element.when.generator.apply)
- description and source-code
```javascript
function apply(generator, args) {
		<span class="apidocCodeCommentSpan">/*jshint validthis:true*/
</span>		return run(generator, this, args || []);
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

#### <a name="apidoc.element.when.generator.call"></a>[function <span class="apidocSignatureSpan">when.generator.</span>call (generator)](#apidoc.element.when.generator.call)
- description and source-code
```javascript
function call(generator) {
		<span class="apidocCodeCommentSpan">/*jshint validthis:true*/
</span>		return run(generator, this, slice.call(arguments, 1));
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

#### <a name="apidoc.element.when.generator.lift"></a>[function <span class="apidocSignatureSpan">when.generator.</span>lift (generator)](#apidoc.element.when.generator.lift)
- description and source-code
```javascript
function lift(generator) {
		return function() {
			return run(generator, this, arguments);
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



# <a name="apidoc.module.when.guard"></a>[module when.guard](#apidoc.module.when.guard)

#### <a name="apidoc.element.when.guard.guard"></a>[function <span class="apidocSignatureSpan">when.</span>guard (condition, f)](#apidoc.element.when.guard.guard)
- description and source-code
```javascript
function guard(condition, f) {
		return function() {
			var args = slice.call(arguments);

			return when(condition()).withThis(this).then(function(exit) {
				return when(f.apply(this, args))['finally'](exit);
			});
		};
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.guard.n"></a>[function <span class="apidocSignatureSpan">when.guard.</span>n (allowed)](#apidoc.element.when.guard.n)
- description and source-code
```javascript
function n(allowed) {
		var count = 0;
		var waiting = [];

		return function enter() {
			return when.promise(function(resolve) {
				if(count < allowed) {
					resolve(exit);
				} else {
					waiting.push(resolve);
				}
				count += 1;
			});
		};

		function exit() {
			count = Math.max(count - 1, 0);
			if(waiting.length > 0) {
				waiting.shift()(exit);
			}
		}
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.keys"></a>[module when.keys](#apidoc.module.when.keys)

#### <a name="apidoc.element.when.keys.all"></a>[function <span class="apidocSignatureSpan">when.keys.</span>all ()](#apidoc.element.when.keys.all)
- description and source-code
```javascript
all = function () {
			for(var i=0, l=arguments.length, a=new Array(l); i<l; ++i) {
				a[i] = arguments[i];
			}
			return apply(f, this, a);
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

#### <a name="apidoc.element.when.keys.map"></a>[function <span class="apidocSignatureSpan">when.keys.</span>map (object, f)](#apidoc.element.when.keys.map)
- description and source-code
```javascript
function map(object, f) {
		return toPromise(object).then(function(object) {
			return all(Object.keys(object).reduce(function(o, k) {
				o[k] = toPromise(object[k]).fold(mapWithKey, k);
				return o;
			}, {}));
		});

		function mapWithKey(k, x) {
			return f(x, k);
		}
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

#### <a name="apidoc.element.when.keys.settle"></a>[function <span class="apidocSignatureSpan">when.keys.</span>settle (object)](#apidoc.element.when.keys.settle)
- description and source-code
```javascript
function settle(object) {
		var keys = Object.keys(object);
		var results = {};

		if(keys.length === 0) {
			return toPromise(results);
		}

		var p = Promise._defer();
		var resolver = Promise._handler(p);
		var promises = keys.map(function(k) { return object[k]; });

		when.settle(promises).then(function(states) {
			populateResults(keys, states, results, resolver);
		});

		return p;
	}
```
- example usage
```shell
...
			return toPromise(results);
		}

		var p = Promise._defer();
		var resolver = Promise._handler(p);
		var promises = keys.map(function(k) { return object[k]; });

		when.settle(promises).then(function(states) {
			populateResults(keys, states, results, resolver);
		});

		return p;
	}

	function populateResults(keys, states, results, resolver) {
...
```



# <a name="apidoc.module.when.node"></a>[module when.node](#apidoc.module.when.node)

#### <a name="apidoc.element.when.node.apply"></a>[function <span class="apidocSignatureSpan">when.node.</span>apply (f, args)](#apidoc.element.when.node.apply)
- description and source-code
```javascript
function apply(f, args) {
		return _apply(f, this, args || []);
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

#### <a name="apidoc.element.when.node.bindCallback"></a>[function <span class="apidocSignatureSpan">when.node.</span>bindCallback (promise, callback)](#apidoc.element.when.node.bindCallback)
- description and source-code
```javascript
function bindCallback(promise, callback) {
		promise = when(promise);

		if (callback) {
			promise.then(success, wrapped);
		}

		return promise;

		function success(value) {
			wrapped(null, value);
		}

		function wrapped(err, value) {
			setTimer(function () {
				callback(err, value);
			}, 0);
		}
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.node.call"></a>[function <span class="apidocSignatureSpan">when.node.</span>call (f)](#apidoc.element.when.node.call)
- description and source-code
```javascript
function call(f) {
		return _apply(f, this, slice.call(arguments, 1));
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

#### <a name="apidoc.element.when.node.createCallback"></a>[function <span class="apidocSignatureSpan">when.node.</span>createCallback (resolver)](#apidoc.element.when.node.createCallback)
- description and source-code
```javascript
function createCallback(resolver) {
		return function(err, value) {
			if(err) {
				resolver.reject(err);
			} else if(arguments.length > 2) {
				resolver.resolve(slice.call(arguments, 1));
			} else {
				resolver.resolve(value);
			}
		};
	}
```
- example usage
```shell
...
	 *			callback(null, interestingValue);
	 *		}
	 *	}
	 *
	 *	var when = require('when'), nodefn = require('when/node/function');
	 *
	 *	var deferred = when.defer();
	 *	callbackTakingFunction(nodefn.createCallback(deferred.resolver));
	 *
	 *	deferred.promise.then(function(interestingValue) {
	 *		// Use interestingValue
	 *	});
	 *
	 * @param {Resolver} resolver that will be 'attached' to the callback
	 * @returns {Function} a node-style callback function
...
```

#### <a name="apidoc.element.when.node.lift"></a>[function <span class="apidocSignatureSpan">when.node.</span>lift (f)](#apidoc.element.when.node.lift)
- description and source-code
```javascript
function lift(f) {
		var args1 = arguments.length > 1 ? slice.call(arguments, 1) : [];
		return function() {
			// TODO: Simplify once partialing has been removed
			var l = args1.length;
			var al = arguments.length;
			var args = new Array(al + l);
			var i;
			for(i=0; i<l; ++i) {
				args[i] = args1[i];
			}
			for(i=0; i<al; ++i) {
				args[i+l] = arguments[i];
			}
			return _apply(f, this, args);
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

#### <a name="apidoc.element.when.node.liftAll"></a>[function <span class="apidocSignatureSpan">when.node.</span>liftAll (src, combine, dst)](#apidoc.element.when.node.liftAll)
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

#### <a name="apidoc.element.when.node.liftCallback"></a>[function <span class="apidocSignatureSpan">when.node.</span>liftCallback (callback)](#apidoc.element.when.node.liftCallback)
- description and source-code
```javascript
function liftCallback(callback) {
		return function(promise) {
			return bindCallback(promise, callback);
		};
	}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.when.state"></a>[module when.state](#apidoc.module.when.state)

#### <a name="apidoc.element.when.state.fulfilled"></a>[function <span class="apidocSignatureSpan">when.state.</span>fulfilled (x)](#apidoc.element.when.state.fulfilled)
- description and source-code
```javascript
function toFulfilledState(x) {
		return { state: 'fulfilled', value: x };
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.state.inspect"></a>[function <span class="apidocSignatureSpan">when.state.</span>inspect (handler)](#apidoc.element.when.state.inspect)
- description and source-code
```javascript
function inspect(handler) {
		var state = handler.state();
		return state === 0 ? toPendingState()
			 : state > 0   ? toFulfilledState(handler.value)
			               : toRejectedState(handler.value);
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.state.pending"></a>[function <span class="apidocSignatureSpan">when.state.</span>pending ()](#apidoc.element.when.state.pending)
- description and source-code
```javascript
function toPendingState() {
		return { state: 'pending' };
	}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.when.state.rejected"></a>[function <span class="apidocSignatureSpan">when.state.</span>rejected (e)](#apidoc.element.when.state.rejected)
- description and source-code
```javascript
function toRejectedState(e) {
		return { state: 'rejected', reason: e };
	}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
