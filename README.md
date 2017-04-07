# api documentation for  [qs (v6.4.0)](https://github.com/ljharb/qs)  [![npm package](https://img.shields.io/npm/v/npmdoc-qs.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-qs) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-qs.svg)](https://travis-ci.org/npmdoc/node-npmdoc-qs)
#### A querystring parser that supports nesting and arrays, with a depth limit

[![NPM](https://nodei.co/npm/qs.png?downloads=true)](https://www.npmjs.com/package/qs)

[![apidoc](https://npmdoc.github.io/node-npmdoc-qs/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-qs_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-qs/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-qs/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-qs/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/ljharb/qs/issues"
    },
    "contributors": [
        {
            "name": "Jordan Harband",
            "email": "ljharb@gmail.com",
            "url": "http://ljharb.codes"
        }
    ],
    "dependencies": {},
    "description": "A querystring parser that supports nesting and arrays, with a depth limit",
    "devDependencies": {
        "@ljharb/eslint-config": "^11.0.0",
        "browserify": "^14.1.0",
        "covert": "^1.1.0",
        "eslint": "^3.17.0",
        "evalmd": "^0.0.17",
        "iconv-lite": "^0.4.15",
        "mkdirp": "^0.5.1",
        "parallelshell": "^2.0.0",
        "qs-iconv": "^1.0.4",
        "safe-publish-latest": "^1.1.1",
        "tape": "^4.6.3"
    },
    "directories": {},
    "dist": {
        "shasum": "13e26d28ad6b0ffaa91312cd3bf708ed351e7233",
        "tarball": "https://registry.npmjs.org/qs/-/qs-6.4.0.tgz"
    },
    "engines": {
        "node": ">=0.6"
    },
    "gitHead": "c7f87b8d2eedd377f6ace065655201f51bee6334",
    "homepage": "https://github.com/ljharb/qs",
    "keywords": [
        "querystring",
        "qs"
    ],
    "license": "BSD-3-Clause",
    "main": "lib/index.js",
    "maintainers": [
        {
            "name": "hueniverse",
            "email": "eran@hammer.io"
        },
        {
            "name": "ljharb",
            "email": "ljharb@gmail.com"
        },
        {
            "name": "nlf",
            "email": "quitlahok@gmail.com"
        }
    ],
    "name": "qs",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/ljharb/qs.git"
    },
    "scripts": {
        "coverage": "covert test",
        "dist": "mkdirp dist && browserify --standalone Qs lib/index.js > dist/qs.js",
        "lint": "eslint lib/*.js test/*.js",
        "prepublish": "safe-publish-latest && npm run dist",
        "pretest": "npm run --silent readme && npm run --silent lint",
        "readme": "evalmd README.md",
        "test": "npm run --silent coverage",
        "tests-only": "node test"
    },
    "version": "6.4.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module qs](#apidoc.module.qs)
1.  [function <span class="apidocSignatureSpan">qs.</span>parse (str, opts)](#apidoc.element.qs.parse)
1.  [function <span class="apidocSignatureSpan">qs.</span>stringify (object, opts)](#apidoc.element.qs.stringify)
1.  object <span class="apidocSignatureSpan">qs.</span>formats
1.  object <span class="apidocSignatureSpan">qs.</span>utils

#### [module qs.utils](#apidoc.module.qs.utils)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>arrayToObject (source, options)](#apidoc.element.qs.utils.arrayToObject)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>compact (obj, references)](#apidoc.element.qs.utils.compact)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>decode (str)](#apidoc.element.qs.utils.decode)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>encode (str)](#apidoc.element.qs.utils.encode)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>isBuffer (obj)](#apidoc.element.qs.utils.isBuffer)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>isRegExp (obj)](#apidoc.element.qs.utils.isRegExp)
1.  [function <span class="apidocSignatureSpan">qs.utils.</span>merge (target, source, options)](#apidoc.element.qs.utils.merge)



# <a name="apidoc.module.qs"></a>[module qs](#apidoc.module.qs)

#### <a name="apidoc.element.qs.parse"></a>[function <span class="apidocSignatureSpan">qs.</span>parse (str, opts)](#apidoc.element.qs.parse)
- description and source-code
```javascript
parse = function (str, opts) {
    var options = opts || {};

    if (options.decoder !== null && options.decoder !== undefined && typeof options.decoder !== 'function') {
        throw new TypeError('Decoder has to be a function.');
    }

    options.delimiter = typeof options.delimiter === 'string' || utils.isRegExp(options.delimiter) ? options.delimiter : defaults
.delimiter;
    options.depth = typeof options.depth === 'number' ? options.depth : defaults.depth;
    options.arrayLimit = typeof options.arrayLimit === 'number' ? options.arrayLimit : defaults.arrayLimit;
    options.parseArrays = options.parseArrays !== false;
    options.decoder = typeof options.decoder === 'function' ? options.decoder : defaults.decoder;
    options.allowDots = typeof options.allowDots === 'boolean' ? options.allowDots : defaults.allowDots;
    options.plainObjects = typeof options.plainObjects === 'boolean' ? options.plainObjects : defaults.plainObjects;
    options.allowPrototypes = typeof options.allowPrototypes === 'boolean' ? options.allowPrototypes : defaults.allowPrototypes;
    options.parameterLimit = typeof options.parameterLimit === 'number' ? options.parameterLimit : defaults.parameterLimit;
    options.strictNullHandling = typeof options.strictNullHandling === 'boolean' ? options.strictNullHandling : defaults.strictNullHandling
;

    if (str === '' || str === null || typeof str === 'undefined') {
        return options.plainObjects ? Object.create(null) : {};
    }

    var tempObj = typeof str === 'string' ? parseValues(str, options) : str;
    var obj = options.plainObjects ? Object.create(null) : {};

    // Iterate over the keys and setup the new object

    var keys = Object.keys(tempObj);
    for (var i = 0; i < keys.length; ++i) {
        var key = keys[i];
        var newObj = parseKeys(key, tempObj[key], options);
        obj = utils.merge(obj, newObj, options);
    }

    return utils.compact(obj);
}
```
- example usage
```shell
...

## Usage

'''javascript
var qs = require('qs');
var assert = require('assert');

var obj = qs.parse('a=c');
assert.deepEqual(obj, { a: 'c' });

var str = qs.stringify(obj);
assert.equal(str, 'a=c');
'''

### Parsing Objects
...
```

#### <a name="apidoc.element.qs.stringify"></a>[function <span class="apidocSignatureSpan">qs.</span>stringify (object, opts)](#apidoc.element.qs.stringify)
- description and source-code
```javascript
stringify = function (object, opts) {
    var obj = object;
    var options = opts || {};

    if (options.encoder !== null && options.encoder !== undefined && typeof options.encoder !== 'function') {
        throw new TypeError('Encoder has to be a function.');
    }

    var delimiter = typeof options.delimiter === 'undefined' ? defaults.delimiter : options.delimiter;
    var strictNullHandling = typeof options.strictNullHandling === 'boolean' ? options.strictNullHandling : defaults.strictNullHandling
;
    var skipNulls = typeof options.skipNulls === 'boolean' ? options.skipNulls : defaults.skipNulls;
    var encode = typeof options.encode === 'boolean' ? options.encode : defaults.encode;
    var encoder = typeof options.encoder === 'function' ? options.encoder : defaults.encoder;
    var sort = typeof options.sort === 'function' ? options.sort : null;
    var allowDots = typeof options.allowDots === 'undefined' ? false : options.allowDots;
    var serializeDate = typeof options.serializeDate === 'function' ? options.serializeDate : defaults.serializeDate;
    var encodeValuesOnly = typeof options.encodeValuesOnly === 'boolean' ? options.encodeValuesOnly : defaults.encodeValuesOnly;
    if (typeof options.format === 'undefined') {
        options.format = formats.default;
    } else if (!Object.prototype.hasOwnProperty.call(formats.formatters, options.format)) {
        throw new TypeError('Unknown format option provided.');
    }
    var formatter = formats.formatters[options.format];
    var objKeys;
    var filter;

    if (typeof options.filter === 'function') {
        filter = options.filter;
        obj = filter('', obj);
    } else if (Array.isArray(options.filter)) {
        filter = options.filter;
        objKeys = filter;
    }

    var keys = [];

    if (typeof obj !== 'object' || obj === null) {
        return '';
    }

    var arrayFormat;
    if (options.arrayFormat in arrayPrefixGenerators) {
        arrayFormat = options.arrayFormat;
    } else if ('indices' in options) {
        arrayFormat = options.indices ? 'indices' : 'repeat';
    } else {
        arrayFormat = 'indices';
    }

    var generateArrayPrefix = arrayPrefixGenerators[arrayFormat];

    if (!objKeys) {
        objKeys = Object.keys(obj);
    }

    if (sort) {
        objKeys.sort(sort);
    }

    for (var i = 0; i < objKeys.length; ++i) {
        var key = objKeys[i];

        if (skipNulls && obj[key] === null) {
            continue;
        }

        keys = keys.concat(stringify(
            obj[key],
            key,
            generateArrayPrefix,
            strictNullHandling,
            skipNulls,
            encode ? encoder : null,
            filter,
            sort,
            allowDots,
            serializeDate,
            formatter,
            encodeValuesOnly
        ));
    }

    return keys.join(delimiter);
}
```
- example usage
```shell
...
'''javascript
var qs = require('qs');
var assert = require('assert');

var obj = qs.parse('a=c');
assert.deepEqual(obj, { a: 'c' });

var str = qs.stringify(obj);
assert.equal(str, 'a=c');
'''

### Parsing Objects

[](#preventEval)
'''javascript
...
```



# <a name="apidoc.module.qs.utils"></a>[module qs.utils](#apidoc.module.qs.utils)

#### <a name="apidoc.element.qs.utils.arrayToObject"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>arrayToObject (source, options)](#apidoc.element.qs.utils.arrayToObject)
- description and source-code
```javascript
arrayToObject = function (source, options) {
    var obj = options && options.plainObjects ? Object.create(null) : {};
    for (var i = 0; i < source.length; ++i) {
        if (typeof source[i] !== 'undefined') {
            obj[i] = source[i];
        }
    }

    return obj;
}
```
- example usage
```shell
...

if (typeof target !== 'object') {
    return [target].concat(source);
}

var mergeTarget = target;
if (Array.isArray(target) && !Array.isArray(source)) {
    mergeTarget = exports.arrayToObject(target, options);
}

if (Array.isArray(target) && Array.isArray(source)) {
    source.forEach(function (item, i) {
        if (has.call(target, i)) {
            if (target[i] && typeof target[i] === 'object') {
                target[i] = exports.merge(target[i], item, options);
...
```

#### <a name="apidoc.element.qs.utils.compact"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>compact (obj, references)](#apidoc.element.qs.utils.compact)
- description and source-code
```javascript
compact = function (obj, references) {
    if (typeof obj !== 'object' || obj === null) {
        return obj;
    }

    var refs = references || [];
    var lookup = refs.indexOf(obj);
    if (lookup !== -1) {
        return refs[lookup];
    }

    refs.push(obj);

    if (Array.isArray(obj)) {
        var compacted = [];

        for (var i = 0; i < obj.length; ++i) {
            if (obj[i] && typeof obj[i] === 'object') {
                compacted.push(exports.compact(obj[i], refs));
            } else if (typeof obj[i] !== 'undefined') {
                compacted.push(obj[i]);
            }
        }

        return compacted;
    }

    var keys = Object.keys(obj);
    keys.forEach(function (key) {
        obj[key] = exports.compact(obj[key], refs);
    });

    return obj;
}
```
- example usage
```shell
...
    var keys = Object.keys(tempObj);
    for (var i = 0; i < keys.length; ++i) {
        var key = keys[i];
        var newObj = parseKeys(key, tempObj[key], options);
        obj = utils.merge(obj, newObj, options);
    }

    return utils.compact(obj);
};
...
```

#### <a name="apidoc.element.qs.utils.decode"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>decode (str)](#apidoc.element.qs.utils.decode)
- description and source-code
```javascript
decode = function (str) {
    try {
        return decodeURIComponent(str.replace(/\+/g, ' '));
    } catch (e) {
        return str;
    }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.qs.utils.encode"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>encode (str)](#apidoc.element.qs.utils.encode)
- description and source-code
```javascript
encode = function (str) {
    // This code was originally written by Brian White (mscdex) for the io.js core querystring library.
    // It has been adapted here for stricter adherence to RFC 3986
    if (str.length === 0) {
        return str;
    }

    var string = typeof str === 'string' ? str : String(str);

    var out = '';
    for (var i = 0; i < string.length; ++i) {
        var c = string.charCodeAt(i);

        if (
            c === 0x2D || // -
            c === 0x2E || // .
            c === 0x5F || // _
            c === 0x7E || // ~
            (c >= 0x30 && c <= 0x39) || // 0-9
            (c >= 0x41 && c <= 0x5A) || // a-z
            (c >= 0x61 && c <= 0x7A) // A-Z
        ) {
            out += string.charAt(i);
            continue;
        }

        if (c < 0x80) {
            out = out + hexTable[c];
            continue;
        }

        if (c < 0x800) {
            out = out + (hexTable[0xC0 | (c >> 6)] + hexTable[0x80 | (c & 0x3F)]);
            continue;
        }

        if (c < 0xD800 || c >= 0xE000) {
            out = out + (hexTable[0xE0 | (c >> 12)] + hexTable[0x80 | ((c >> 6) & 0x3F)] + hexTable[0x80 | (c & 0x3F)]);
            continue;
        }

        i += 1;
        c = 0x10000 + (((c & 0x3FF) << 10) | (string.charCodeAt(i) & 0x3FF));
        out += hexTable[0xF0 | (c >> 18)] + hexTable[0x80 | ((c >> 12) & 0x3F)] + hexTable[0x80 | ((c >> 6) & 0x3F)] + hexTable[
0x80 | (c & 0x3F)]; // eslint-disable-line max-len
    }

    return out;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.qs.utils.isBuffer"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>isBuffer (obj)](#apidoc.element.qs.utils.isBuffer)
- description and source-code
```javascript
isBuffer = function (obj) {
    if (obj === null || typeof obj === 'undefined') {
        return false;
    }

    return !!(obj.constructor && obj.constructor.isBuffer && obj.constructor.isBuffer(obj));
}
```
- example usage
```shell
...
    if (strictNullHandling) {
        return encoder && !encodeValuesOnly ? encoder(prefix) : prefix;
    }

    obj = '';
}

if (typeof obj === 'string' || typeof obj === 'number' || typeof obj === 'boolean' || utils.isBuffer(obj)) {
    if (encoder) {
        var keyValue = encodeValuesOnly ? prefix : encoder(prefix);
        return [formatter(keyValue) + '=' + formatter(encoder(obj))];
    }
    return [formatter(prefix) + '=' + formatter(String(obj))];
}
...
```

#### <a name="apidoc.element.qs.utils.isRegExp"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>isRegExp (obj)](#apidoc.element.qs.utils.isRegExp)
- description and source-code
```javascript
isRegExp = function (obj) {
    return Object.prototype.toString.call(obj) === '[object RegExp]';
}
```
- example usage
```shell
...
module.exports = function (str, opts) {
var options = opts || {};

if (options.decoder !== null && options.decoder !== undefined && typeof options.decoder !== 'function') {
    throw new TypeError('Decoder has to be a function.');
}

options.delimiter = typeof options.delimiter === 'string' || utils.isRegExp(options.delimiter) ? options.delimiter : defaults.delimiter
;
options.depth = typeof options.depth === 'number' ? options.depth : defaults.depth;
options.arrayLimit = typeof options.arrayLimit === 'number' ? options.arrayLimit : defaults.arrayLimit;
options.parseArrays = options.parseArrays !== false;
options.decoder = typeof options.decoder === 'function' ? options.decoder : defaults.decoder;
options.allowDots = typeof options.allowDots === 'boolean' ? options.allowDots : defaults.allowDots;
options.plainObjects = typeof options.plainObjects === 'boolean' ? options.plainObjects : defaults.plainObjects;
options.allowPrototypes = typeof options.allowPrototypes === 'boolean' ? options.allowPrototypes : defaults.allowPrototypes;
...
```

#### <a name="apidoc.element.qs.utils.merge"></a>[function <span class="apidocSignatureSpan">qs.utils.</span>merge (target, source, options)](#apidoc.element.qs.utils.merge)
- description and source-code
```javascript
merge = function (target, source, options) {
    if (!source) {
        return target;
    }

    if (typeof source !== 'object') {
        if (Array.isArray(target)) {
            target.push(source);
        } else if (typeof target === 'object') {
            if (options.plainObjects || options.allowPrototypes || !has.call(Object.prototype, source)) {
                target[source] = true;
            }
        } else {
            return [target, source];
        }

        return target;
    }

    if (typeof target !== 'object') {
        return [target].concat(source);
    }

    var mergeTarget = target;
    if (Array.isArray(target) && !Array.isArray(source)) {
        mergeTarget = exports.arrayToObject(target, options);
    }

    if (Array.isArray(target) && Array.isArray(source)) {
        source.forEach(function (item, i) {
            if (has.call(target, i)) {
                if (target[i] && typeof target[i] === 'object') {
                    target[i] = exports.merge(target[i], item, options);
                } else {
                    target.push(item);
                }
            } else {
                target[i] = item;
            }
        });
        return target;
    }

    return Object.keys(source).reduce(function (acc, key) {
        var value = source[key];

        if (Object.prototype.hasOwnProperty.call(acc, key)) {
            acc[key] = exports.merge(acc[key], value, options);
        } else {
            acc[key] = value;
        }
        return acc;
    }, mergeTarget);
}
```
- example usage
```shell
...

    // Iterate over the keys and setup the new object

    var keys = Object.keys(tempObj);
    for (var i = 0; i < keys.length; ++i) {
        var key = keys[i];
        var newObj = parseKeys(key, tempObj[key], options);
        obj = utils.merge(obj, newObj, options);
    }

    return utils.compact(obj);
};
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
