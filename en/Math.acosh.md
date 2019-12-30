TOPICS: Math.acosh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.acosh()`

The **`Math.acosh()`** function returns the hyperbolic arc-cosine of a number, that is

$$
\forall x \geq 1, \mathtt{\operatorname{Math.acosh}(x)} = \operatorname{arcosh}(x)
= \text{ the unique } \; y \geq 0 \; \text{such that} \; \cosh(y) = x
$$

## Syntax

```javascript
Math.acosh(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: The hyperbolic arc-cosine of the given number. If the number is less than `1`, `NaN`.

## Description

Because `acosh()` is a static method of [`Math`](/en/webfrontend/Math), you always use it as
`Math.acosh()`, rather than as a method of a [`Math`](/en/webfrontend/Math) object you created
(`Math` is no constructor).

## Examples

### Using `Math.acosh()`

```javascript
Math.acosh(-1);  // NaN
Math.acosh(0);   // NaN
Math.acosh(0.5); // NaN
Math.acosh(1);   // 0
Math.acosh(2);   // 1.3169578969248166
```

For values less than 1 `Math.acosh()` returns `NaN`.

## Polyfill

For \\(x \geq 1\\), we have \\(\operatorname {arcosh} (x) = \ln \left(x + \sqrt{x^{2} - 1} \right)\\),
and so this can be emulated with the following function:

```javascript
Math.acosh = Math.acosh || function(x) {
  return Math.log(x + Math.sqrt(x * x - 1));
};
```
