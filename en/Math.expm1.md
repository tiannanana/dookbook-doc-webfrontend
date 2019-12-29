TOPICS: Math.expm1
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.expm1()`

The **`Math.expm1()`** function returns e^^x - 1, where `x` is the argument, and `e` the base of
the natural logarithms.

## Syntax

```javascript
Math.expm1(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `expm1()` is a static method of `Math`, you always use it as `Math.expm1()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.expm1()`

```javascript
Math.expm1(-1); // -0.6321205588285577
Math.expm1(0);  // 0
Math.expm1(1);  // 1.718281828459045
```

## Polyfill

This can be emulated with the help of the [`Math.exp()`](/en/webfrontend/Math.exp) function:

```javascript
Math.expm1 = Math.expm1 || function(x) {
  return Math.exp(x) - 1;
};
```
