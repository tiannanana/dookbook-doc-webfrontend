TOPICS: Math.hypot
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.hypot()`

The **`Math.hypot()`** function returns the square root of the sum of squares of its arguments,
that is:

$$
\mathtt{\operatorname{Math.hypot}(v_1, v_2, \dots, v_n)} = \sqrt{\sum_{i=1}^n v_i^2}
= \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}
$$

## Syntax

```javascript
Math.hypot([value1[, value2[, ...]]])
```

| parameter | Description |
| :-- | :-- |
| `value1, value2, ...` | Numbers. |

**Return value**: The square root of the sum of squares of the given arguments. If at least one
of the arguments cannot be converted to a number, `NaN` is returned.

## Description

Calculating the hypotenuse of a right triangle, or the magnitude of a complex number, uses the
formula `Math.sqrt(v1*v1 + v2*v2)` where v1 and v2 are either the sides of the triangle, or the
real and complex values. For calculating distance in 2 or more dimensions, simply add in more
squares inside the square root sign, like `Math.sqrt(v1*v1 + v2*v2 + v3*v3 + v4*v4)`.  

This function makes it a little easier and faster, you just call `Math.hypot(v1, v2)` ,
or `Math.hypot(v1, v2, v3, v4, ...)` .  

It also avoids a problem if the magnitude of your numbers is huge. The largest number you can
represent in JS's double floats is `Number.MAX_VALUE = 1.797...e+308` . If your numbers are larger
than about 1e154, taking the square of them will result in `Infinity`, demolishing your results.
For example, `Math.sqrt(1e200*1e200 + 1e200*1e200) = Infinity` .  If you use `hypot()` instead,
you get a good answer `Math.hypot(1e200, 1e200) = 1.4142...e+200` . This is also true with very
small numbers. `Math.sqrt(1e-200*1e-200 + 1e-200*1e-200) = 0`, but
`Math.hypot(1e-200, 1e-200) =1.4142...e-20`0, a good answer.

Because `hypot()` is a static method of `Math`, you always use it as `Math.hypot()`, rather than
as a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

If no arguments are given, the result is `+0`.

If at least one of the arguments cannot be converted to a number, the result is `NaN`.

With one argument, `Math.hypot()` returns the same as `Math.abs()`.

## Examples

### Using `Math.hypot()`

```javascript
Math.hypot(3, 4);        // 5
Math.hypot(3, 4, 5);     // 7.0710678118654755
Math.hypot();            // 0
Math.hypot(NaN);         // NaN
Math.hypot(3, 4, 'foo'); // NaN, +'foo' => NaN
Math.hypot(3, 4, '5');   // 7.0710678118654755, +'5' => 5
Math.hypot(-3);          // 3, the same as Math.abs(-3)
```

## Polyfill

This can be emulated using the following function:

```javascript
if (!Math.hypot) Math.hypot = function() {
  var y = 0, i = arguments.length;
  while (i--) y += arguments[i] * arguments[i];
  return Math.sqrt(y);
};
```

A polyfill that avoids underflows and overflows:

```javascript
if (!Math.hypot) Math.hypot = function (x, y) {
  // https://bugzilla.mozilla.org/show_bug.cgi?id=896264#c28
  var max = 0;
  var s = 0;
  for (var i = 0; i < arguments.length; i += 1) {
    var arg = Math.abs(Number(arguments[i]));
    if (arg > max) {
      s *= (max / arg) * (max / arg);
      max = arg;
    }
    s += arg === 0 && max === 0 ? 0 : (arg / max) * (arg / max);
  }
  return max === 1 / 0 ? 1 / 0 : max * Math.sqrt(s);
};
```
