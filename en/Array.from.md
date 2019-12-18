TOPICS: Array.from
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.from()`

The `Array.from()` method creates a new, shallow-copied `Array` instance from an array-like or
iterable object.

## Syntax

```javascript
Array.from(arrayLike[, mapFn[, thisArg]])
```

| parameter | Description |
| :-- | :-- |
| `arrayLike` | An array-like or iterable object to convert to an array. |
| `mapFn` Optional | Map function to call on every element of the array. |
| `thisArg` Optional | Value to use as this when executing mapFn. |

**Return value**: A new `Array` instance.

## Description

`Array.from()` lets you create Arrays `from`:

- array-like objects (objects with a length property and indexed elements) or
- iterable objects (objects where you can get its elements, such as Map and Set).

`Array.from()` has an optional parameter mapFn, which allows you to execute a [`map`](/en/webfrontend/Array.map)
function on each element of the array (or subclass object) that is being created. More clearly,
`Array.from(obj, mapFn, thisArg)` has the same result as `Array.from(obj).map(mapFn, thisArg)`,
except that it does not create an intermediate array. This is especially important for certain
array subclasses, like typed arrays, since the intermediate array would necessarily have values
truncated to fit into the appropriate type.

The length property of the `from()` method is `1`.

In ES2015, the class syntax allows for sub-classing of both built-in and user defined classes; as a
result, static methods such as `Array.from` are "inherited" by subclasses of Array and create new
instances of the subclass, not Array.

## Examples

### Array from a `String`

```javascript
Array.from('foo');
// [ "f", "o", "o" ]
```

### Array from a `Set`

```javascript
const set = new Set(['foo', 'bar', 'baz', 'foo']);
Array.from(set);
// [ "foo", "bar", "baz" ]
```

### Array from a `Map`

```javascript
const map = new Map([[1, 2], [2, 4], [4, 8]]);
Array.from(map);
// [[1, 2], [2, 4], [4, 8]]

const mapper = new Map([['1', 'a'], ['2', 'b']]);
Array.from(mapper.values());
// ['a', 'b'];

Array.from(mapper.keys());
// ['1', '2'];
```

### Array from an Array-like object (arguments)

```javascript
function f() {
  return Array.from(arguments);
}

f(1, 2, 3);

// [ 1, 2, 3 ]
```

### Using arrow functions and `Array.from()`

```javascript
// Using an arrow function as the map function to
// manipulate the elements
Array.from([1, 2, 3], x => x + x);
// [2, 4, 6]


// Generate a sequence of numbers
// Since the array is initialized with `undefined` on each position,
// the value of `v` below will be `undefined`
Array.from({length: 5}, (v, i) => i);
// [0, 1, 2, 3, 4]
```

### Sequence generator (range)

```javascript
// Sequence generator function (commonly referred to as "range", e.g. Clojure, PHP etc)
const range = (start, stop, step) => Array.from({ length: (stop - start) / step + 1}, (_, i) => start + (i * step));

// Generate numbers range 0..4
range(0, 4, 1);
// [0, 1, 2, 3, 4]

// Generate numbers range 1..10 with step of 2
range(1, 10, 2);
// [1, 3, 5, 7, 9]

// Generate the alphabet using Array.from making use of it being ordered as a sequence
range('A'.charCodeAt(0), 'Z'.charCodeAt(0), 1).map(x => String.fromCharCode(x));
// ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"]
```

## Polyfill

`Array.from()` was added to the ECMA-262 standard in the 6th edition (ES2015); as such it may not be
present in other implementations of the standard. You can work around this by inserting the
following code at the beginning of your scripts, allowing use of `Array.from()` in implementations
that don't natively support it. This algorithm is exactly the one specified in ECMA-262,
6th edition, assuming [`Object`](/en/webfrontend/Object) and [`TypeError`](/en/webfrontend/TypeError)
have their original values and that `callback.call` evaluates to the original value of [`Function.call`](/en/webfrontend/Function.call).
In addition, since true iterables can not be polyfilled, this implementation does not support
generic iterables as defined in the 6th edition of ECMA-262.

```javascript
// Production steps of ECMA-262, Edition 6, 22.1.2.1
if (!Array.from) {
  Array.from = (function () {
    var toStr = Object.toString;
    var isCallable = function (fn) {
      return typeof fn === 'function' || toStr.call(fn) === '[object Function]';
    };
    var toInteger = function (value) {
      var number = Number(value);
      if (isNaN(number)) { return 0; }
      if (number === 0 || !isFinite(number)) { return number; }
      return (number > 0 ? 1 : -1) * Math.floor(Math.abs(number));
    };
    var maxSafeInteger = Math.pow(2, 53) - 1;
    var toLength = function (value) {
      var len = toInteger(value);
      return Math.min(Math.max(len, 0), maxSafeInteger);
    };

    // The length property of the from method is 1.
    return function from(arrayLike/*, mapFn, thisArg */) {
      // 1. Let C be the this value.
      var C = this;

      // 2. Let items be ToObject(arrayLike).
      var items = Object(arrayLike);

      // 3. ReturnIfAbrupt(items).
      if (arrayLike == null) {
        throw new TypeError('Array.from requires an array-like object - not null or undefined');
      }

      // 4. If mapfn is undefined, then let mapping be false.
      var mapFn = arguments.length > 1 ? arguments[1] : void undefined;
      var T;
      if (typeof mapFn !== 'undefined') {
        // 5. else
        // 5. a If IsCallable(mapfn) is false, throw a TypeError exception.
        if (!isCallable(mapFn)) {
          throw new TypeError('Array.from: when provided, the second argument must be a function');
        }

        // 5. b. If thisArg was supplied, let T be thisArg; else let T be undefined.
        if (arguments.length > 2) {
          T = arguments[2];
        }
      }

      // 10. Let lenValue be Get(items, "length").
      // 11. Let len be ToLength(lenValue).
      var len = toLength(items.length);

      // 13. If IsConstructor(C) is true, then
      // 13. a. Let A be the result of calling the [[Construct]] internal method
      // of C with an argument list containing the single item len.
      // 14. a. Else, Let A be ArrayCreate(len).
      var A = isCallable(C) ? Object(new C(len)) : new Array(len);

      // 16. Let k be 0.
      var k = 0;
      // 17. Repeat, while k < len… (also steps a - h)
      var kValue;
      while (k < len) {
        kValue = items[k];
        if (mapFn) {
          A[k] = typeof T === 'undefined' ? mapFn(kValue, k) : mapFn.call(T, kValue, k);
        } else {
          A[k] = kValue;
        }
        k += 1;
      }
      // 18. Let putStatus be Put(A, "length", len, true).
      A.length = len;
      // 20. Return A.
      return A;
    };
  }());
}
```
