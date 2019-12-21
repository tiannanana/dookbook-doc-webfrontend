TOPICS: isFinite
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `isFinite()`

The global **`isFinite()`** function determines whether the passed value is a finite number. If
needed, the parameter is first converted to a number.

## Syntax

```javascript
isFinite(testValue)
```

| parameter | Description |
| :-- | :-- |
| `testValue` | The value to be tested for finiteness. |

**Return value**: **`false`** if the argument is positive or negative `Infinity` or `NaN` or `undefined`;
otherwise, `true`.

## Description

`isFinite` is a top-level function and is not associated with any object.

You can use this function to determine whether a number is a finite number. The `isFinite` function
examines the number in its argument. If the argument is `NaN`, positive infinity, or negative
infinity, this method returns `false`; otherwise, it returns `true`.

## Examples

```javascript
isFinite(Infinity);  // false
isFinite(NaN);       // false
isFinite(-Infinity); // false

isFinite(0);         // true
isFinite(2e64);      // true
isFinite(910);       // true

isFinite(null);      // true, would've been false with the
                     // more robust Number.isFinite(null)

isFinite('0');       // true, would've been false with the
                     // more robust Number.isFinite("0")
```
