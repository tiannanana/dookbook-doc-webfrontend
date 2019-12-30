TOPICS: Math.exp
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.exp()`

The **`Math.exp()`** function returns e^^x^^, where `x` is the argument, and `e` is Euler's number
(also known as Napier's constant), the base of the natural logarithms.

## Syntax

```javascript
Math.exp(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `exp()` is a static method of `Math`, you always use it as `Math.exp()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.exp()`

```javascript
Math.exp(-1); // 0.36787944117144233
Math.exp(0);  // 1
Math.exp(1);  // 2.718281828459045
```
