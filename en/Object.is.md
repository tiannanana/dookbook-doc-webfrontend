TOPICS: Object.is
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.is()`

The **`Object.is()`** method determines whether two values are the same value.

## Syntax

```javascript
Object.is(value1, value2);
```

| parameter | Description |
| :-- | :-- |
| `value1` | The first value to compare. |
| `value2` | The second value to compare. |

**Return value**: A `Boolean` indicating whether or not the two arguments are the same value.

## Description

`Object.is()` determines whether two values are the same value. Two values are the same if one
of the following holds:

- both `undefined`
- both `null`
- both `true` or both `false`
- both strings of the same length with the same characters in the same order
- both the same object (means both object have same reference)
- both numbers and
    - both `+0`
    - both `-0`
    - both `NaN`
    - or both non-zero and both not `NaN` and both have the same value

This is not the same as being equal according to the `==` operator. The `==` operator applies
various coercions to both sides (if they are not the same Type) before testing for equality
(resulting in such behavior as `"" == false` being `true`), but `Object.is` doesn't coerce either value.

This is also not the same as being equal according to the `===` operator. The `===` operator
(and the `==` operator as well) treats the number values `-0` and `+0` as equal and treats
[`Number.NaN`](/en/webfrontend/Number) as not equal to `NaN`.

## Examples

```javascript
Object.is('foo', 'foo');     // true
Object.is(window, window);   // true

Object.is('foo', 'bar');     // false
Object.is([], []);           // false

var foo = { a: 1 };
var bar = { a: 1 };
Object.is(foo, foo);         // true
Object.is(foo, bar);         // false

Object.is(null, null);       // true

// Special Cases
Object.is(0, -0);            // false
Object.is(-0, -0);           // true
Object.is(NaN, 0/0);         // true
```

### Polyfill

```javascript
if (!Object.is) {
  Object.is = function(x, y) {
    // SameValue algorithm
    if (x === y) { // Steps 1-5, 7-10
      // Steps 6.b-6.e: +0 != -0
      return x !== 0 || 1 / x === 1 / y;
    } else {
      // Step 6.a: NaN == NaN
      return x !== x && y !== y;
    }
  };
}
```
