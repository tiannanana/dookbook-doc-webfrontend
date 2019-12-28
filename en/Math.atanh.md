TOPICS: Math.atanh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.atanh()`

The **`Math.atanh()`** function returns the hyperbolic arctangent of a number, that is

$$
\forall x \in \left( -1, 1 \right), \mathtt{\operatorname{Math.atanh}(x)} = \operatorname{arctanh}(x)
= \text{ the unique } \; y \; \text{such that} \; \tanh(y) = x
$$

## Syntax

```javascript
Math.atanh(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `atanh()` is a static method of `Math`, you always use it as `Math.atanh()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.atanh()`

```javascript
Math.atanh(-2);  // NaN
Math.atanh(-1);  // -Infinity
Math.atanh(0);   // 0
Math.atanh(0.5); // 0.5493061443340548
Math.atanh(1);   // Infinity
Math.atanh(2);   // NaN
```

For values greater than `1` or less than `-1`, `NaN` is returned.
