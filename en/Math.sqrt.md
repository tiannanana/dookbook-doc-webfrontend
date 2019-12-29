TOPICS: Math.sqrt
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sqrt()`

The **`Math.sqrt()`** function returns the square root of a number, that is

$$
\forall x \geq 0, \mathtt{Math.sqrt(x)} = \sqrt{x} = \text{the unique} \; y \geq 0 \;
\text{such that} \; y^2 = x
$$

## Syntax

```javascript
Math.sqrt(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

If the value of x is negative, `Math.sqrt()` returns `NaN`.

Because `sqrt()` is a static method of `Math`, you always use it as `Math.sqrt()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.sqrt()`

```javascript
Math.sqrt(9); // 3
Math.sqrt(2); // 1.414213562373095

Math.sqrt(1);  // 1
Math.sqrt(0);  // 0
Math.sqrt(-1); // NaN
Math.sqrt(-0); // -0
```
