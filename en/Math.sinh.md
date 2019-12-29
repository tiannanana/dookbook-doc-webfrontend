TOPICS: Math.sinh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sinh()`

The **`Math.sinh()`** function returns the hyperbolic sine of a number, that can be expressed using
the constant e:

$$
\mathtt{\operatorname{Math.sinh(x)}} = \frac{e^x - e^{-x}}{2}
$$

## Syntax

```javascript
Math.sinh(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `sinh()` is a static method of `Math`, you always use it as `Math.sinh()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.sinh()`

```javascript
Math.sinh(0); // 0
Math.sinh(1); // 1.1752011936438014
```

## Polyfill

This can be emulated with the help of the [`Math.exp()`](/en/webfrontend/Math.exp) function:

```javascript
Math.sinh = Math.sinh || function(x) {
  return (Math.exp(x) - Math.exp(-x)) / 2;
}
```

or using only one call to the [`Math.exp()`](/en/webfrontend/Math.exp) function:

```javascript
Math.sinh = Math.sinh || function(x) {
  var y = Math.exp(x);
  return (y - 1 / y) / 2;
}
```
