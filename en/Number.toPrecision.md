TOPICS: Number.toPrecision
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.toPrecision()`

The **`toPrecision()`** method returns a string representing the [`Number`](/en/webfrontend/Number)
object to the specified precision.

## Syntax

```javascript
numObj.toPrecision([precision])
```

| parameter | Description |
| :-- | :-- |
| `precision` | Optional. An integer specifying the number of significant digits. |

## Return value

A string representing a [`Number`](/en/webfrontend/Number) object in fixed-point or exponential
notation rounded to `precision` significant digits. See the discussion of rounding in the
description of the [`Number.toFixed()`](/en/webfrontend/Number.toFixed) method, which also
applies to `toPrecision()`.

If the `precision` argument is omitted, behaves as [`Number.toString()`](/en/webfrontend/Number.toString).
If the `precision` argument is a non-integer value, it is rounded to the nearest integer.

## Exceptions

|  |  |
| :-- | :-- |
| `RangeError` | If precision is not between `1` and `100` (inclusive), a `RangeError` is thrown. Implementations are allowed to support larger and smaller values as well. ECMA-262 only requires a precision of up to `21` significant digits. |

## Examples

### Using `toPrecision`

```javascript
let numObj = 5.123456

console.log(numObj.toPrecision())    // logs '5.123456'
console.log(numObj.toPrecision(5))   // logs '5.1235'
console.log(numObj.toPrecision(2))   // logs '5.1'
console.log(numObj.toPrecision(1))   // logs '5'

numObj = 0.000123

console.log(numObj.toPrecision())    // logs '0.000123'
console.log(numObj.toPrecision(5))   // logs '0.00012300'
console.log(numObj.toPrecision(2))   // logs '0.00012'
console.log(numObj.toPrecision(1))   // logs '0.0001'

// note that exponential notation might be returned in some circumstances
console.log((1234.5).toPrecision(2)) // logs '1.2e+3'
```
