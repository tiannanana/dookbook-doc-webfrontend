TOPICS: Number.isInteger
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.isInteger()`

The **`Number.isInteger()`** method determines whether the passed value is an integer.

## Syntax

```javascript
Number.isInteger(value)
```

| parameter | Description |
| :-- | :-- |
| `value` | The value to be tested for being an integer. |

**Return value**: A `Boolean` indicating whether or not the given value is an integer.

## Description

If the target value is an integer, return `true`, otherwise return `false`. If the value is
`NaN` or `Infinity`, return `false`. The method will also return `true` for floating point
numbers that can be represented as integer.

## Examples

```javascript
Number.isInteger(0);         // true
Number.isInteger(1);         // true
Number.isInteger(-100000);   // true
Number.isInteger(99999999999999999999999); // true

Number.isInteger(0.1);       // false
Number.isInteger(Math.PI);   // false

Number.isInteger(NaN);       // false
Number.isInteger(Infinity);  // false
Number.isInteger(-Infinity); // false
Number.isInteger('10');      // false
Number.isInteger(true);      // false
Number.isInteger(false);     // false
Number.isInteger([1]);       // false

Number.isInteger(5.0);       // true
Number.isInteger(5.000000000000001); // false
Number.isInteger(5.0000000000000001); // true
```
