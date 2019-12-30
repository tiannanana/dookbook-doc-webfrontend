TOPICS: Math.sin
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sin()`

The **`Math.sin()`** function returns the sine of a number.

## Syntax

```javascript
Math.sin(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

The `Math.sin()` method returns a numeric value between `-1` and `1`, which represents the sine of
the angle given in radians.

Because `sin()` is a static method of `Math`, you always use it as `Math.sin()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.sin()`

```javascript
Math.sin(0);           // 0
Math.sin(1);           // 0.8414709848078965

Math.sin(Math.PI / 2); // 1
```
