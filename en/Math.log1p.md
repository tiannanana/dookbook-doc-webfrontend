TOPICS: Math.log1p
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log1p()`

The **`Math.log1p()`** function returns the natural logarithm (base e) of 1 + a number, that is

$$
\forall x > -1, \mathtt{\operatorname{Math.log1p}(x)} = \ln(1 + x)
$$$

## Syntax

```javascript
Math.log1p(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

For very small values of `x`, adding 1 can reduce or eliminate precision. The double floats used in
JS give you about 15 digits of precision. `1 + 1e-15 = 1.000000000000001`, but
`1 + 1e-16 = 1.000000000000000` and therefore exactly 1.0 in that arithmetic, because digits past
15 are rounded off.  

When you calculate `log(1 + x)`, you should get an answer very close to `x`, if `x` is small
(that's why these are called 'natural' logarithms).  If you calculate `Math.log(1 + 1.1111111111e-15)`
you should get an answer close to `1.1111111111e-15`.  Instead, you will end up taking the logarithm
of `1.00000000000000111022` (the roundoff is in binary so sometimes it gets ugly), so you get the
answer `1.11022...e-15`, with only  3 correct digits.  If, instead, you calculate
`Math.log1p(1.1111111111e-15)` you will get a much more accurate answer `1.1111111110999995e-15`
with 15 correct digits of precision (actually 16 in this case).

If the value of `x` is less than `-1`, the return value is always NaN.

Because `log1p()` is a static method of `Math`, you always use it as `Math.log1p()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.log1p()`

```javascript
Math.log1p(1);  // 0.6931471805599453
Math.log1p(0);  // 0
Math.log1p(-1); // -Infinity
Math.log1p(-2); // NaN
```

## Polyfill

This can be emulated with the following function:

```javascript
Math.log1p = Math.log1p || function(x) {
  return Math.log(1 + x);
};
```
