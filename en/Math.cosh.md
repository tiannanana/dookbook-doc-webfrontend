TOPICS: Math.cosh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.cosh()`

The **`Math.cosh()`** function returns the hyperbolic cosine of a number, that can be expressed
using the constant e:

$$
\mathtt{\operatorname{Math.cosh(x)}} = \frac{e^^x + e^^{-x}}{2}
$$

## Syntax

```javascript
Math.cosh(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `cosh()` is a static method of `Math`, you always use it as `Math.cosh()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.cosh()`

```javascript
Math.cosh(0);  // 1
Math.cosh(1);  // 1.5430806348152437
Math.cosh(-1); // 1.5430806348152437
```
