TOPICS: Array.prototype.includes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.includes()`

The `includes()` method determines whether an array `includes` a certain value among its entries,
returning true or false as appropriate.

## Syntax

```html
arr.includes(valueToFind[, fromIndex])
```

| parameter | Description |
| :-- | :-- |
| `valueToFind` | The value to search for. <br>**Note:** When comparing strings and characters, `includes()` is **case-sensitive**. |
| `fromIndex` | Optional, The position in this array at which to begin searching for `valueToFind`; the first character to be searched is found at `fromIndex` for positive values of `fromIndex`, or at array.length + `fromIndex` for negative values of `fromIndex` (using the absolute value of `fromIndex` as the number of characters from the end of the array at which to start the search). Defaults to 0. |

**Return value**：A Boolean which is true if the value valueToFind is found within the array (or the
part of the array indicated by the index fromIndex, if specified). Values of zero are all considered
to be equal regardless of sign (that is, -0 is considered to be equal to both 0 and +0), but false is
not considered to be the same as 0.

!!! warn "Note"
    Technically speaking, `includes()` uses the [`sameValueZero`](/en/webfrontend/sameValueZero)
    algorithm to determine whether the given element is found.

## Examples

```javascript
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

### fromIndex is greater than or equal to the array length

If `fromIndex` is greater than or equal to the length of the array, `false` is returned. The array will
not be searched.

```javascript
var arr = ['a', 'b', 'c'];

arr.includes('c', 3);   // false
arr.includes('c', 100); // false
```

### Computed index is less than 0

If `fromIndex` is negative, the computed index is calculated to be used as a position in the array
at which to begin searching for `valueToFind`. If the computed index is less or equal than
`-1 * array.length`, the entire array will be searched.

```javascript
// array length is 3
// fromIndex is -100
// computed index is 3 + (-100) = -97

var arr = ['a', 'b', 'c'];

arr.includes('a', -100); // true
arr.includes('b', -100); // true
arr.includes('c', -100); // true
arr.includes('a', -2); // false
```

### includes() used as a generic method

`includes()` method is intentionally generic. It does not require `this` value to be an Array object,
so it can be applied to other kinds of objects (e.g. array-like objects). The example below illustrates
`includes()` method called on the function's arguments object.

```javascript
(function() {
  console.log([].includes.call(arguments, 'a')); // true
  console.log([].includes.call(arguments, 'd')); // false
})('a','b','c');
```
