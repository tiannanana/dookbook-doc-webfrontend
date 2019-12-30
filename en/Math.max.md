TOPICS: Math.max
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.max()`

The **`Math.max()`** function returns the largest of zero or more numbers.

## Syntax

```javascript
Math.max([value1[, value2[, ...]]])
```

| parameter | Description |
| :-- | :-- |
| `value1, value2, ...` | Numbers. |

**Return value**: The largest of the given numbers. If at least one of the arguments cannot be
converted to a number, `NaN` is returned.

## Description

Because `max()` is a static method of `Math`, you always use it as `Math.max()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

If no arguments are given, the result is `-Infinity`.

If at least one of arguments cannot be converted to a number, the result is `NaN`.

## Examples

### Using `Math.max()`

```javascript
Math.max(10, 20);   //  20
Math.max(-10, -20); // -10
Math.max(-10, 20);  //  20
```

Getting the maximum element of an array

[`Array.reduce()`](/en/webfrontend/Array.reduce) can be used to find the maximum element in a
numeric array, by comparing each value:

```javascript
var arr = [1,2,3];
var max = arr.reduce(function(a, b) {
    return Math.max(a, b);
});
```

The following function uses [`Function.apply()`](/en/webfrontend/Function.apply) to get the
maximum of an array. `getMaxOfArray([1, 2, 3])` is equivalent to `Math.max(1, 2, 3)`, but you can
use `getMaxOfArray()` on programmatically constructed arrays. This should only be used for
arrays with relatively few elements.

```javascript
function getMaxOfArray(numArray) {
  return Math.max.apply(null, numArray);
}
```

The new spread operator is a shorter way of writing the `apply` solution to get the maximum of an array:

```javascript
var arr = [1, 2, 3];
var max = Math.max(...arr);
```

However, both `spread (...)` and `apply` will either fail or return the wrong result if the array
has too many elements, because they try to pass the array elements as function parameters. See
Using `apply` and built-in functions for more details. The `reduce` solution does not have this problem.
