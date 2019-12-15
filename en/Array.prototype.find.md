TOPICS: Array.prototype.find
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.prototype.find()`

The `find()` method returns the value of the first element in the provided array that satisfies the
provided testing function.

- If you need the index of the found element in the array, use [`findIndex()`](/en/webfrontend/findIndex).
- If you need to find the index of a value, use [`Array.prototype.indexOf()`](/en/webfrontend/Array.prototype.indexOf).
(It’s similar to [`findIndex()`](/en/webfrontend/findIndex), but checks each element for equality
with the value instead of using a testing function.)
- If you need to find if a value exists in an array, use [`Array.prototype.includes()`](/en/webfrontend/Array.prototype.includes).

## Syntax

```html
arr.find(callback[, thisArg])
```

| parameter | Description |
| :-- | :-- |
| `callback` | Function to execute on each value in the array, taking 3 arguments:<br>**`element`**<br>The current element in the array.<br><br>**`index`** Optional<br>The index (position) of the current element in the array.<br><br>**`array`** Optional<br>The array that `find` was called on.
| `thisValue` | Object to use as `this` inside callback. |

**Return value**：The value of the first element in the array that satisfies the provided testing
function. Otherwise, [`undefined`](/en/webfrontend/undefined) is returned.

## Description

The `find` method executes the `callback` function once for each index of the array until the callback
returns a truthy value. If so, `find` immediately returns the value of that element. Otherwise,
`find` returns [`undefined`](/en/webfrontend/undefined).

`callback` is invoked for every index of the array, not just those with assigned values. This means
it may be less efficient for sparse arrays, compared to methods that only visit assigned values.

If a thisArg parameter is provided to `find`, it will be used as the this value inside each
invocation of the `callback`. If it is not provided, then
[`undefined`](/en/webfrontend/undefined) is used.

The `find` method does not mutate the array on which it is called, but the function provided to
`callback` can. If so, the elements processed by `find` are set before the first invocation of
`callback`. Therefore:

- `callback` will not visit any elements added to the array after the call to `find` begins.
- If an existing, yet-unvisited element of the array is changed by `callback`, its value passed to
the `callback` will be the value at the time `find` visits that element's index.
- Elements that are [`deleted`](/en/webfrontend/deleted) are still visited.

## Examples

### Find an object in an array by one of its properties

```javascript
const inventory = [
  {name: 'apples', quantity: 2},
  {name: 'bananas', quantity: 0},
  {name: 'cherries', quantity: 5}
];

function isCherries(fruit) {
  return fruit.name === 'cherries';
}

console.log(inventory.find(isCherries));
// { name: 'cherries', quantity: 5 }
```

Using arrow function and destructuring

```javascript
const inventory = [
  {name: 'apples', quantity: 2},
  {name: 'bananas', quantity: 0},
  {name: 'cherries', quantity: 5}
];

const result = inventory.find( ({ name }) => name === 'cherries' );

console.log(result) // { name: 'cherries', quantity: 5 }
```

### Find a prime number in an array

The following example finds an element in the array that is a prime number (or returns undefined if
there is no prime number):

```javascript
function isPrime(element, index, array) {
  let start = 2;
  while (start <= Math.sqrt(element)) {
    if (element % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}

console.log([4, 6, 8, 12].find(isPrime)); // undefined, not found
console.log([4, 5, 8, 12].find(isPrime)); // 5
```

The following examples show that nonexistent and deleted elements are visited, and that the value
passed to the callback is their value when visited:

```javascript
// Declare array with no elements at indexes 2, 3, and 4
const array = [0,1,,,,5,6];

// Shows all indexes, not just those with assigned values
array.find(function(value, index) {
  console.log('Visited index ', index, ' with value ', value);
});

// Shows all indexes, including deleted
array.find(function(value, index) {
  // Delete element 5 on first iteration
  if (index === 0) {
    console.log('Deleting array[5] with value ', array[5]);
    delete array[5];
  }
  // Element 5 is still visited even though deleted
  console.log('Visited index ', index, ' with value ', value);
});
// expected output:
// Deleting array[5] with value 5
// Visited index 0 with value 0
// Visited index 1 with value 1
// Visited index 2 with value undefined
// Visited index 3 with value undefined
// Visited index 4 with value undefined
// Visited index 5 with value undefined
// Visited index 6 with value 6
});
```

## Polyfill

This method has been added to the ECMAScript 2015 specification and may not be available in all
JavaScript implementations yet. However, you can polyfill Array.prototype.find with the following snippet:

```javascript
// https://tc39.github.io/ecma262/#sec-array.prototype.find
if (!Array.prototype.find) {
  Object.defineProperty(Array.prototype, 'find', {
    value: function(predicate) {
      // 1. Let O be ? ToObject(this value).
      if (this == null) {
        throw TypeError('"this" is null or not defined');
      }

      var o = Object(this);

      // 2. Let len be ? ToLength(? Get(O, "length")).
      var len = o.length >>> 0;

      // 3. If IsCallable(predicate) is false, throw a TypeError exception.
      if (typeof predicate !== 'function') {
        throw TypeError('predicate must be a function');
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
        // d. If testResult is true, return kValue.
        var kValue = o[k];
        if (predicate.call(thisArg, kValue, k, o)) {
          return kValue;
        }
        // e. Increase k by 1.
        k++;
      }

      // 7. Return undefined.
      return undefined;
    },
    configurable: true,
    writable: true
  });
}
```

If you need to support truly obsolete JavaScript engines that don't support [`Object.defineProperty`](/en/webfrontend/Object.defineProperty),
it is best not to polyfill `Array.prototype` at all, as you cannot make it non-enumerable.
