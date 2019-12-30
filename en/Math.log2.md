TOPICS: Math.log2
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log2()`

The **`Math.log2()`** function returns the base 2 logarithm of a number, that is

$$
\forall x > 0, \mathtt{\operatorname{Math.log2}(x)} = \log_2(x) = \text{the unique} \; y \;
\text{such that} \; 2^y = x
$$

## Syntax

```javascript
Math.log2(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

If the value of `x` is less than `0`, the return value is always `NaN`.

Because `log2()` is a static method of `Math`, you always use it as `Math.log2()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

This function is the equivalent of `Math.log(x)` / `Math.log(2)`.  For `log2(e)` use the constant
[`Math.LOG2E`](/en/webfrontend/Math.LOG2E) which is 1 / [`Math.LN2`](/en/webfrontend/Math.LN2).  

## Examples

### Using `Math.log2()`

```javascript
Math.log2(3);    // 1.584962500721156
Math.log2(2);    // 1
Math.log2(1);    // 0
Math.log2(0);    // -Infinity
Math.log2(-2);   // NaN
Math.log2(1024); // 10
```

## Polyfill

This Polyfill emulates the `Math.log2` function. Note that it returns imprecise values on some
inputs (like 1 << 29), wrap into [`Math.round()`](/en/webfrontend/Math.round) if working with bit masks.

```javascript
if (!Math.log2) Math.log2 = function(x) {
  return Math.log(x) * Math.LOG2E;
};
```
