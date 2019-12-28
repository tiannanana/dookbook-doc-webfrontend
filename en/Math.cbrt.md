TOPICS: Math.cbrt
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.cbrt()`

The **`Math.cbrt()`** function returns the cube root of a number, that is

$$
\mathtt{Math.cbrt(x)} = \sqrt[3]{x} = \text{the unique} \; y \; \text{such that} \; y^3 = x
$$

## Syntax

```javascript
Math.cbrt(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `cbrt()` is a static method of `Math`, you always use it as `Math.cbrt()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.cbrt()`

```javascript
Math.cbrt(NaN); // NaN
Math.cbrt(-1); // -1
Math.cbrt(-0); // -0
Math.cbrt(-Infinity); // -Infinity
Math.cbrt(0); // 0
Math.cbrt(1); // 1
Math.cbrt(Infinity); // Infinity
Math.cbrt(null); // 0
Math.cbrt(2);  // 1.2599210498948734
```

## Polyfill

For all \\(x \geq 0\\), have \\(\sqrt[3]{x} = x^^{1/3}\\) so this can be emulated by the following function:

```javascript
if (!Math.cbrt) {
  Math.cbrt = (function(pow) {
    return function cbrt(x){
      // ensure negative numbers remain negative:
      return x < 0 ? -pow(-x, 1/3) : pow(x, 1/3);
    };
  })(Math.pow); // localize Math.pow to increase efficiency
}
```
