TOPICS: Array.prototype.findIndex
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.findIndex()`

The `findIndex()` method returns the index of the first element in the array that satisfies the
provided testing function. Otherwise, it returns -1, indicating that no element passed the test.

See also the [`find()`](/en/webfrontend/Array.prototype.find) method, which returns the value of an
array element, instead of its index.

## Syntax

```html
arr.findIndex(callback[, thisArg])
```

| parameter | Description |
| :-- | :-- |
| `callback` | A function to execute on each value in the array until the function returns true, indicating that the satisfying element was found. It takes three arguments:<br>**`element`**<br>The current element being processed in the array.<br><br>**`index`** Optional<br>The index of the current element being processed in the array.<br><br>**`array`** Optional<br>The array `findIndex` was called upon.
| `thisValue` | Optional object to use as `this` when executing `callback`. |

**Return value**：The index of the first element in the array that passes the test. Otherwise, -1.

## Description

The `findIndex` method executes the `callback` function once for every index `0..length-1` (inclusive)
in the array until it finds the one where `callback` returns a truthy value
(a value that coerces to `true`).

If such an element is found, `findIndex` immediately returns the element's index. If the `callback`
never returns a truthy value (or the array's `length` is 0), `findIndex` returns -1. Unlike other
array methods such as [`Array.some`](/en/webfrontend/Array.prototype.some), the `callback` is called
even for indexes with unassigned values.

`callback` is invoked with three arguments:

- The value of the element
- The index of the element
- The Array object being traversed

If a thisArg parameter is passed to `findIndex`, it will be used as the this inside each invocation
of the `callback`. If it is not provided, then [`undefined`](/en/webfrontend/undefined) is used.

The range of elements processed by `findIndex` is set before the first invocation of `callback`.
`callback` will not process the elements appended to the array after the call to `findIndex` begins.
If an existing, unvisited element of the array is changed by callback, its value passed to the
`callback` will be the value at the time `findIndex` visits the element's index. Elements that are
[`deleted`](/en/webfrontend/deleted) are still visited.

## Examples

### Find the index of a prime number in an array

The following example returns the index of the first element in the array that is a prime number,
or -1 if there is no prime number.

```javascript
function isPrime(element, index, array) {
  let start = 2;
  while (start <= Math.sqrt(element)) {
    if (element % start < 1) {
      return false;
    } else {
      start++;
    }
  }
  return element > 2;
}

console.log([4, 6, 8, 12].findIndex(isPrime)); // -1, not found
console.log([4, 6, 7, 12].findIndex(isPrime)); // 2 (array[2] is 7)
```

### Find index using arrow function

The following example finds the index of a fruit using an arrow function:

```javascript
const fruits = ["apple", "banana", "cantaloupe", "blueberries", "grapefruit"];

const index = fruits.findIndex(fruit => fruit === "blueberries");

console.log(index); // 3
console.log(fruits[index]); // blueberries
```

## Polyfill

```javascript
// https://tc39.github.io/ecma262/#sec-array.prototype.findindex
if (!Array.prototype.findIndex) {
  Object.defineProperty(Array.prototype, 'findIndex', {
    value: function(predicate) {
     // 1. Let O be ? ToObject(this value).
      if (this == null) {
        throw new TypeError('"this" is null or not defined');
      }

      var o = Object(this);

      // 2. Let len be ? ToLength(? Get(O, "length")).
      var len = o.length >>> 0;

      // 3. If IsCallable(predicate) is false, throw a TypeError exception.
      if (typeof predicate !== 'function') {
        throw new TypeError('predicate must be a function');
      }

      // 4. If thisArg was supplied, let T be thisArg; else let T be undefined.
      var thisArg = arguments[1];

      // 5. Let k be 0.
      var k = 0;

      // 6. Repeat, while k < len
      while (k < len) {
        // a. Let Pk be ! ToString(k).
        // b. Let kValue be ? Get(O, Pk).
        // c. Let testResult be ToBoolean(? Call(predicate, T, « kValue, k, O »)).
        // d. If testResult is true, return k.
        var kValue = o[k];
        if (predicate.call(thisArg, kValue, k, o)) {
          return k;
        }
        // e. Increase k by 1.
        k++;
      }

      // 7. Return -1.
      return -1;
    },
    configurable: true,
    writable: true
  });
}
```

If you need to support truly obsolete JavaScript engines that do not support [`Object.defineProperty`](/en/webfrontend/Object.defineProperty),
it is best not to polyfill `Array.prototype` methods at all, as you cannot make them non-enumerable.
