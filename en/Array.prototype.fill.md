TOPICS: Array.prototype.fill
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.prototype.fill()`

The `fill()` method fills (modifies) all the elements of an array from a start index (default zero)
to an end index (default array length) with a static value. It returns the modified array.

## Syntax

```html
arr.fill(value[, start[, end]])
```

| parameter | Description |
| :-- | :-- |
| `value` | Value to fill an array. |
| `start` | Start index, defaults to `0`. |
| `end` | End index, defaults to arr.length. |

**Return value**：Array

## Description

The `fill` method takes up to three arguments `value`, `start` and `end`. The `start` and `end`
arguments are optional with default values of `0` and the `length` of the array.

If `start` is negative, it is treated as `length+start` where `length` is the length of the array.
If `end` is negative, it is treated as `length+end`.

`fill` is intentionally generic, it does not require that its `this` value be an Array object.

`fill` is a mutator method, it will change array itself, and return it, not just return a copy of it.

When the first parameter given to `fill` is an object, it will copy the reference and `fill` the
array with references to that object.

## Examples

```javascript
[1, 2, 3].fill(4);               // [4, 4, 4]
[1, 2, 3].fill(4, 1);            // [1, 4, 4]
[1, 2, 3].fill(4, 1, 2);         // [1, 4, 3]
[1, 2, 3].fill(4, 1, 1);         // [1, 2, 3]
[1, 2, 3].fill(4, 3, 3);         // [1, 2, 3]
[1, 2, 3].fill(4, -3, -2);       // [4, 2, 3]
[1, 2, 3].fill(4, NaN, NaN);     // [1, 2, 3]
[1, 2, 3].fill(4, 3, 5);         // [1, 2, 3]
Array(3).fill(4);                // [4, 4, 4]
[].fill.call({ length: 3 }, 4);  // {0: 4, 1: 4, 2: 4, length: 3}

// Objects by reference.
var arr = Array(3).fill({}) // [{}, {}, {}];
arr[0].hi = "hi"; // [{ hi: "hi" }, { hi: "hi" }, { hi: "hi" }]
```

## Polyfill

```javascript
if (!Array.prototype.fill) {
  Object.defineProperty(Array.prototype, 'fill', {
    value: function(value) {

      // Steps 1-2.
      if (this == null) {
        throw new TypeError('this is null or not defined');
      }

      var O = Object(this);

      // Steps 3-5.
      var len = O.length >>> 0;

      // Steps 6-7.
      var start = arguments[1];
      var relativeStart = start >> 0;

      // Step 8.
      var k = relativeStart < 0 ?
        Math.max(len + relativeStart, 0) :
        Math.min(relativeStart, len);

      // Steps 9-10.
      var end = arguments[2];
      var relativeEnd = end === undefined ?
        len : end >> 0;

      // Step 11.
      var final = relativeEnd < 0 ?
        Math.max(len + relativeEnd, 0) :
        Math.min(relativeEnd, len);

      // Step 12.
      while (k < final) {
        O[k] = value;
        k++;
      }

      // Step 13.
      return O;
    }
  });
}
```

If you need to support truly obsolete JavaScript engines that don't support [`Object.defineProperty`](/en/webfrontend/Object.defineProperty),
it's best not to polyfill `Array.prototype` methods at all, as you can't make them non-enumerable.
