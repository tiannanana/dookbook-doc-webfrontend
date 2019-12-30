TOPICS: Math.tanh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.tanh()`

The **`Math.tanh()`** function returns the hyperbolic tangent of a number, that is

$$
\tanh x = \frac{\sinh x}{\cosh x} = \frac {e^x - e^{-x}} {e^x + e^{-x}} = \frac{e^{2x} - 1}{e^{2x}+1}
$$

## Syntax

```javascript
Math.tanh(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `tanh()` is a static method of `Math`, you always use it as `Math.tanh()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.tanh()`

```javascript
Math.tanh(0);        // 0
Math.tanh(Infinity); // 1
Math.tanh(1);        // 0.7615941559557649
```

## Polyfill

This can be emulated with the help of the `Math.exp()` function:

```javascript
Math.tanh = Math.tanh || function(x){
  var a = Math.exp(+x), b = Math.exp(-x);
  return a == Infinity ? 1 : b == Infinity ? -1 : (a - b) / (a + b);
}
```
