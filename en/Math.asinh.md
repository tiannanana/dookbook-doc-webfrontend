TOPICS: Math.asinh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.asinh()`

The **`Math.asinh()`** function returns the hyperbolic arcsine of a number, that is

$$
\mathtt{\operatorname{Math.asinh}(x)} = \operatorname{arsinh}(x) = \text{ the unique } \; y \;
\text{such that} \; \sinh(y) = x
$$

## Syntax

```javascript
Math.asinh(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `asinh()` is a static method of [`Math`](/en/webfrontend/Math), you always use it as `Math.asinh()`,
rather than as a method of a [`Math`](/en/webfrontend/Math) object you created (Math is not a constructor).

## Examples

### Using `Math.asinh()`

```javascript
Math.asinh(1);  // 0.881373587019543
Math.asinh(0);  // 0
```

## PolyfillSection

As a quick and dirty hack the expression
\\(\operatorname {arsinh} (x) = \ln \left(x + \sqrt{x^{2} + 1} \right)\\) may be used directly for
a coarse emulation by the following function:

```javascript
Math.asinh = Math.asinh || function(x) {
  if (x === -Infinity) {
    return x;
  } else {
    return Math.log(x + Math.sqrt(x * x + 1));
  }
};
```
