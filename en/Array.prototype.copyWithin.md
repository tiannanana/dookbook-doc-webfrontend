TOPICS: Array.prototype.copyWithin
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.prototype.copyWithin()`

The `copyWithin()` method shallow copies part of an array to another location in the same array and
returns it without modifying its length.

## Syntax

```html
arr.copyWithin(target[, start[, end]])
```

| parameter | Description |
| :-- | :-- |
| `target` | Zero-based index at which to copy the sequence to. If negative, `target` will be counted from the end.<br>If `target` is at or greater than `arr.length`, nothing will be copied. If `target` is positioned after start, the copied sequence will be trimmed to fit `arr.length`. |
| `start` | Zero-based index at which to `start` copying elements from. If negative, `start` will be counted from the end.<br>If `start` is omitted, `copyWithin` will copy from index 0. |
| `end` | Zero-based index at which to `end` copying elements from. `copyWithin` copies up to but not including `end`. If negative, `end` will be counted from the `end`.<br>If `end` is omitted, `copyWithin` will copy until the last index (default to arr.length).|

**Return value**：Array

## Description

The `copyWithin` works like C and C++'s `memmove`, and is a high-performance method to shift the
data of an [`Array`](/en/webfrontend/Array_Object). This especially applies to the [`TypedArray`](/en/webfrontend/TypedArray)
method of the same name. The sequence is copied and pasted as one operation; pasted sequence will
have the copied values even when the copy and paste region overlap.

The `copyWithin` function is intentionally generic, it does not require that its `this` value be an
[`Array`](/en/webfrontend/Array_Object) object.

The `copyWithin` method is a mutable method. It does not alter the length of `this`, but it will change
its content and create new properties, if necessary.

## Examples

```javascript
let numbers = [1, 2, 3, 4, 5];

numbers.copyWithin(-2);
// [1, 2, 3, 1, 2]

numbers.copyWithin(0, 3);
// [4, 5, 3, 4, 5]

numbers.copyWithin(0, 3, 4);
// [4, 2, 3, 4, 5]

numbers.copyWithin(-2, -3, -1);
// [1, 2, 3, 3, 4]

[].copyWithin.call({length: 5, 3: 1}, 0, 3);
// {0: 1, 3: 1, length: 5}

// ES2015 Typed Arrays are subclasses of Array
var i32a = new Int32Array([1, 2, 3, 4, 5]);

i32a.copyWithin(0, 2);
// Int32Array [3, 4, 5, 4, 5]

// On platforms that are not yet ES2015 compliant:
[].copyWithin.call(new Int32Array([1, 2, 3, 4, 5]), 0, 3, 4);
// Int32Array [4, 2, 3, 4, 5]
```

## Polyfill

```javascript
if (!Array.prototype.copyWithin) {
  Array.prototype.copyWithin = function(target, start/*, end*/) {
    // Steps 1-2.
    if (this == null) {
      throw new TypeError('this is null or not defined');
    }

    var O = Object(this);

    // Steps 3-5.
    var len = O.length >>> 0;

    // Steps 6-8.
    var relativeTarget = target >> 0;

    var to = relativeTarget < 0 ?
      Math.max(len + relativeTarget, 0) :
      Math.min(relativeTarget, len);

    // Steps 9-11.
    var relativeStart = start >> 0;

    var from = relativeStart < 0 ?
      Math.max(len + relativeStart, 0) :
      Math.min(relativeStart, len);

    // Steps 12-14.
    var end = arguments[2];
    var relativeEnd = end === undefined ? len : end >> 0;

    var final = relativeEnd < 0 ?
      Math.max(len + relativeEnd, 0) :
      Math.min(relativeEnd, len);

    // Step 15.
    var count = Math.min(final - from, len - to);

    // Steps 16-17.
    var direction = 1;

    if (from < to && to < (from + count)) {
      direction = -1;
      from += count - 1;
      to += count - 1;
    }

    // Step 18.
    while (count > 0) {
      if (from in O) {
        O[to] = O[from];
      } else {
        delete O[to];
      }

      from += direction;
      to += direction;
      count--;
    }

    // Step 19.
    return O;
  };
}
```
