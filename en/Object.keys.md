TOPICS: Object.keys
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.keys()`

The **`Object.keys()`** method returns an array of a given object's own enumerable property **names**,
in the same order as we get with a normal loop.

## Syntax

```javascript
Object.keys(obj)
```

| parameter | Description |
| :-- | :-- |
| `obj` | The object of which the enumerable's own properties are to be returned. |

**Return value**: An array of strings that represent all the enumerable properties of the given object.

## Description

`Object.keys()` returns an array whose elements are strings corresponding to the enumerable
properties found directly upon `object`. The ordering of the properties is the same as that given by
looping over the properties of the object manually.

## Examples

```javascript
// simple array
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// array like object
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // console: ['0', '1', '2']

// array like object with random key ordering
var anObj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(anObj)); // console: ['2', '7', '100']

// getFoo is a property which isn't enumerable
var myObj = Object.create({}, {
  getFoo: {
    value: function () { return this.foo; }
  }
});
myObj.foo = 1;
console.log(Object.keys(myObj)); // console: ['foo']
```

If you want all properties, even non-enumerables, see [`Object.getOwnPropertyNames()`](/en/webfrontend/Object.getOwnPropertyNames).

## Notes

In ES5, if the argument to this method is not an object (a primitive), then it will cause a `TypeError`.
In ES2015, a non-object argument will be coerced to an object.

```javascript
Object.keys('foo');
// TypeError: "foo" is not an object (ES5 code)

Object.keys('foo');
// ["0", "1", "2"]                   (ES2015 code)
```

## Polyfill

To add compatible `Object.keys` support in older environments that do not natively support it,
copy the following snippet:

```javascript
// From https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys
if (!Object.keys) {
  Object.keys = (function() {
    'use strict';
    var hasOwnProperty = Object.prototype.hasOwnProperty,
        hasDontEnumBug = !({ toString: null }).propertyIsEnumerable('toString'),
        dontEnums = [
          'toString',
          'toLocaleString',
          'valueOf',
          'hasOwnProperty',
          'isPrototypeOf',
          'propertyIsEnumerable',
          'constructor'
        ],
        dontEnumsLength = dontEnums.length;

    return function(obj) {
      if (typeof obj !== 'function' && (typeof obj !== 'object' || obj === null)) {
        throw new TypeError('Object.keys called on non-object');
      }

      var result = [], prop, i;

      for (prop in obj) {
        if (hasOwnProperty.call(obj, prop)) {
          result.push(prop);
        }
      }

      if (hasDontEnumBug) {
        for (i = 0; i < dontEnumsLength; i++) {
          if (hasOwnProperty.call(obj, dontEnums[i])) {
            result.push(dontEnums[i]);
          }
        }
      }
      return result;
    };
  }());
}
```

Please note that the above code includes non-enumerable keys in IE7 (and maybe IE8), when passing in
an object from a different window.
