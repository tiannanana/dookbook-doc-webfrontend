TOPICS: Math.log10
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log10()`

The **`Math.log10()`** function returns the base `10` logarithm of a number, that is

$$
\forall x > 0, \mathtt{\operatorname{Math.log10}(x)} = \log_10(x) = \text{the unique} \; y \;
\text{such that} \; 10^y = x
$$

## Syntax

```javascript
Math.log10(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

If the value of `x` is less than `0`, the return value is always `NaN`.

Because `log10()` is a static method of `Math`, you always use it as `Math.log10()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

This function is the equivalent of `Math.log(x)` / `Math.log(10)`.  For `log10(e)` use the constant
[`Math.LOG10E`](/en/webfrontend/Math.LOG10E) which is 1 / [`Math.LN10`](/en/webfrontend/Math.LN10).

## Examples

### Using `Math.log10()`

```javascript
Math.log10(2);      // 0.3010299956639812
Math.log10(1);      // 0
Math.log10(0);      // -Infinity
Math.log10(-2);     // NaN
Math.log10(100000); // 5
```

## Polyfill

This can be emulated with the following function:

```javascript
Math.log10 = Math.log10 || function(x) {
  return Math.log(x) * Math.LOG10E;
};
```
