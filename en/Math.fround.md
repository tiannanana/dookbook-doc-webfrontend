TOPICS: Math.fround
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.fround()`

The **`Math.fround()`** function returns the nearest 32-bit single precision
float representation of a [`Number`](/en/webfrontend/Number).

## Syntax

```javascript
var singleFloat = Math.fround(doubleFloat);
```

| parameter | Description |
| :-- | :-- |
| `doubleFloat` | A `Number`. If the parameter is of a different type, it will get converted to a number or to `NaN` if it cannot be converted. |

**Return value**: Number

## Description

JavaScript uses 64-bit double floating-point numbers internally, which offer a very high precision.
However, sometimes you may be working with 32-bit floating-point numbers, for example if you are
reading values from a `Float32Array`. This can create confusion: Checking a 64-bit float and a 32-bit
float for equality may fail even though the numbers are seemingly identical.

To solve this, `Math.fround()` can be used to cast the 64-bit float to a 32-bit float. Internally,
JavaScript continues to treat the number as a 64-bit float, it just performs a "round to even" on
the 23rd bit of the mantissa, and sets all following mantissa bits to 0. If the number is outside
the range of a 32-bit float, `Infinity` or `-Infinity` is returned.

Because `fround()` is a static method of `Math`, you always use it as `Math.fround()`, rather than
as a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.fround()`

The number 1.5 can be precisely represented in the binary numeral system, and is identical in
32-bit and 64-bit:

```javascript
Math.fround(1.5); // 1.5
Math.fround(1.5) === 1.5; // true
```

However, the number 1.337 cannot be precisely represented in the binary numeral system,
so it differs in 32-bit and 64-bit:

```javascript
Math.fround(1.337); // 1.3370000123977661
Math.fround(1.337) === 1.337; // false
```

2^^150 is too big for a 32-bit float, so `Infinity` is returned:

```javascript
2 ** 150; // 1.42724769270596e+45
Math.fround(2 ** 150); // Infinity
```

If the parameter cannot be converted to a number, or it is not-a-number
(`NaN`), `Math.fround()` will return `NaN`:

```javascript
Math.fround('abc'); // NaN
Math.fround(NaN); // NaN
```

## Polyfill

This can be emulated with the following function, if `Float32Array` are supported:

```javascript
Math.fround = Math.fround || (function (array) {
  return function(x) {
    return array[0] = x, array[0];
  };
})(new Float32Array(1));
```

Supporting older browsers is slower, but also possible:

```javascript
if (!Math.fround) Math.fround = function(arg) {
  arg = Number(arg);
  // Return early for ±0 and NaN.
  if (!arg) return arg;
  var sign = arg < 0 ? -1 : 1;
  if (sign < 0) arg = -arg;
  // Compute the exponent (8 bits, signed).
  var exp = Math.floor(Math.log(arg) / Math.LN2);
  var powexp = Math.pow(2, Math.max(-126, Math.min(exp, 127)));
  // Handle subnormals: leading digit is zero if exponent bits are all zero.
  var leading = exp < -127 ? 0 : 1;
  // Compute 23 bits of mantissa, inverted to round toward zero.
  var mantissa = Math.round((leading - arg / powexp) * 0x800000);
  if (mantissa <= -0x800000) return sign * Infinity;
  return sign * powexp * (leading - mantissa / 0x800000);
};
```

## Faster Alternative Polyfill (Work In Progress)

The below polyfill is much faster and uses double-precision rounding errors to emulate the
rounding errors caused by floating point narrowing. Although the polyfill higher on the
page is good for comprehension, all of the complex `Math` function that it uses make it terrible
slow. Although this polyfill is much faster, it is off by a bit in about 1 out of 2048 of the tests
due to the tendency to round upwards like `Math.ceil` instead of like `Math.round` in the division of
the subnormal-handling section of the code. Because single precision floating points have 23 bits
of precision, the mean error deviation from the correct value is roughly `2**-28` or `0.0000000058%`.
This deviation from the correct value should be insignifigant in most circumstances, however please
edit this polyfill if you have some tweaks to increase correctness without bloating the code size
too much. `NaN` is not optimized for because it is most likely (almost certain) that you will not
be calling `Math.fround` with `NaN` exclusively in a tight loop. Moreover, an additional check just
for `NaN` instead of letting `NaN` naturally arise would induce a performance penalty for this
function in older browsers when not called with `NaN`. Thus, the code below handles `NaN` correctly,
but inefficiently for good reason.

```javascript
const Math_round = Math.round;
if (!Math.fround) Math.fround = function(x) {
    if (x > 3.402823669209385e+38) return Infinity; // maximum float is 2**128
    if (x < -3.402823669209385e+38) return -Infinity; // minimum is -2**128
    if (-1.1754943508222875e-38 < x && x < 1.1754943508222875e-38) {
        if (-1.401298464324817e-45 < x && x < 1.401298464324817e-45) return 0;
        // else, it is a subnormal
        var mul = Math_round(x/1.4012984643e-45)*1e-323;
        return mul * 1.418129833677085e+278;
    }

    var hi = x * 9007199254740992; // 9007199254740992 is 2**53 which is the maximum of double precision
    var exp = (x + hi) - hi; // adding this number chops off all lower bits, rounding the number.
    exp /= 16777216; // 8388608 = 2**23 * 2, so preserve 23 bits in x because there are 23 bits in a float
                     //            The "* 2" compensates for the addition shifting up the bits unwantedly
    return Math_round(x / exp) * exp;
}
```

Below is code used to test for deviations from the correct value. The code below is meant for
testing the merit of the function, not for polyfilling older browsers (as evidenced by the fact
that the native Math.fround function is used).

```javascript
requestIdleCallback(function(){"use strict";
    const Math_fround = Math.fround;
    const Math_round = Math.round;
    function my_fround(x) {
        if (x > 3.402823669209385e+38) return Infinity; // maximum float is 2**128
        if (x < -3.402823669209385e+38) return -Infinity; // minimum is -2**128
        if (-1.1754943508222875e-38 < x && x < 1.1754943508222875e-38) {
            if (-1.401298464324817e-45 < x && x < 1.401298464324817e-45) return 0;
            // else, it is a subnormal
            var mul = Math_round(x/1.4012984643e-45)*1e-323;
            return mul * 1.418129833677085e+278;
        }

        var hi = x * 9007199254740992; // 9007199254740992 is 2**53 which is the maximum of double precision
        var exp = (x + hi) - hi; // adding this number chops off all lower bits, rounding the number.
        exp /= 16777216; // 8388608 = 2**23 * 2, so preserve 23 bits in x because there are 23 bits in a float
                         //            The "* 2" compensates for the addition shifting up the bits unwantedly
        return Math_round(x / exp) * exp;
    }

    const doublesArray = new Float64Array(8192);
    const int32s = new Uint32Array(doublesArray.buffer);

    const crypto = window.crypto;

    var hasWarned = false, warnings=0;
    for (var i=0; i<4; i=i+1|0) {
        crypto.getRandomValues(int32s);
        for (var k=0; k<8192; k=k+1|0) {
            const myValue = my_fround(doublesArray[k]);
            const froundVal = Math_fround(doublesArray[k]);
            // quicker version of Object.is because of no function call overhead:
            if (myValue === myValue ? myValue !== froundVal : froundVal === froundVal) {
                if (!hasWarned) console.error(doublesArray[k]); // only show the first incorrect number
                hasWarned = true;
                warnings = warnings + 1|0;
            }
        }
    }
    console[warnings > 0 ? "warn" : "log"]( "Total number of mishandled floats: " + warnings );
});
```
