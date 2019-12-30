TOPICS: Math.log
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log()`

The **`Math.log()`** function returns the natural logarithm (base e) of a number, that is

$$
\forall x > 0, \mathtt{\operatorname{Math.log}(x)} = \ln(x) = \text{the unique} \; y \;
\text{such that} \; e^y = x
$$

The JavaScript **`Math.log()`** function is equivalent to `ln(x)` in mathematics.

## Syntax

```javascript
Math.log(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

If the value of `x` is `0`, the return value is always `-Infinity`.

If the value of `x` is negative, the return value is always `NaN`.

Because `log()` is a static method of `Math`, you always use it as `Math.log()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

If you need the natural log of `2` or `10`, use the constants [`Math.LN2`](/en/webfrontend/Math.LN2)
or [`Math.LN10`](/en/webfrontend/Math.LN10). If you need a logarithm to base `2` or `10`, use
[`Math.log2()`](/en/webfrontend/Math.log2) or [`Math.log10()`](/en/webfrontend/Math.log10). If you
need a logarithm to other bases, use `Math.log(x)` / `Math.log(otherBase)` as in the example below;
you might want to precalculate `1` / `Math.log(otherBase)` .

## Examples

### Using `Math.log()`

```javascript
Math.log(-1); // NaN, out of range
Math.log(0);  // -Infinity
Math.log(1);  // 0
Math.log(10); // 2.302585092994046
```

### Using `Math.log()` with a different base

The following function returns the logarithm of `y` with base `x` (ie. log~x~y):

```javascript
function getBaseLog(x, y) {
  return Math.log(y) / Math.log(x);
}
```

If you run `getBaseLog(10, 1000)` it returns `2.9999999999999996` due to floating-point rounding,
which is very close to the actual answer of 3.
