TOPICS: Array.reverse
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.reverse()`

The `reverse()` method reverses an array in place. The first array element becomes the last, and the
last array element becomes the first.

## Syntax

```javascript
a.reverse()
```

**parameter**: No parameters

**Return value**: The reversed array.

## Description

The `reverse` method transposes the elements of the calling array object in place, mutating the array,
and returning a reference to the array.

`reverse` is intentionally generic; this method can be [`called`](/en/webfrontend/Function.call)
or [`applied`](/en/webfrontend/Function.apply) to objects resembling arrays. Objects which
do not contain a `length` property reflecting the last in a series of consecutive, zero-based numerical
properties may not behave in any meaningful manner.

## Examples

### Reversing the elements in an array

The following example creates an array `a`, containing three elements, then reverses the array.
The call to `reverse()` returns a reference to the reversed array `a`.

```javascript
const a = [1, 2, 3];

console.log(a); // [1, 2, 3]

a.reverse();

console.log(a); // [3, 2, 1]
```

### Reversing the elements in an array-like object

The following example creates an array-like object `a`, containing three elements and a length
property, then reverses the array-like object. The call to `reverse()` returns a reference to the
reversed array-like object `a`.

```javascript
const a = {0: 1, 1: 2, 2: 3, length: 3};

console.log(a); // {0: 1, 1: 2, 2: 3, length: 3}

Array.reverse.call(a); //same syntax for using apply()

console.log(a); // {0: 3, 1: 2, 2: 1, length: 3}
```
