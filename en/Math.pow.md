TOPICS: Math.pow
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.pow()`

The **`Math.pow()`** function returns the `base` to the `exponent` power, that is, base^^exponent^^.

## Syntax

```javascript
Math.pow(base, exponent)
```

| parameter | Description |
| :-- | :-- |
| `base` | The base number. |
| `exponent` | The exponent used to raise the base. |

**Return value**: Number

## Description

The `Math.pow()` function returns the base to the exponent power, that is, baseexponent, the base
and the exponent are in decimal numeral system.

Because `pow()` is a static method of `Math`, you always use it as `Math.pow()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` has no constructor).

## Examples

### Using `Math.pow()`

```javascript
// simple
Math.pow(7, 2);    // 49
Math.pow(7, 3);    // 343
Math.pow(2, 10);   // 1024
// fractional exponents
Math.pow(4, 0.5);  // 2 (square root of 4)
Math.pow(8, 1/3);  // 2 (cube root of 8)
Math.pow(2, 0.5);  // 1.4142135623730951 (square root of 2)
Math.pow(2, 1/3);  // 1.2599210498948732 (cube root of 2)
// signed exponents
Math.pow(7, -2);   // 0.02040816326530612 (1/49)
Math.pow(8, -1/3); // 0.5
// signed bases
Math.pow(-7, 2);   // 49 (squares are positive)
Math.pow(-7, 3);   // -343 (cubes can be negative)
Math.pow(-7, 0.5); // NaN (negative numbers don't have a real square root)
// due to "even" and "odd" roots laying close to each other,
// and limits in the floating number precision,
// negative bases with fractional exponents always return NaN
Math.pow(-7, 1/3); // NaN
```

## Demonstrative Implementation

For those who desire to understand how `Math.pow` might work internally, please view the following
code. The below code recursively does multiplication by the `pow` of two. Do not use the following
code to replace `Math.pow` because the following code will always be slower than `Math.pow` because
`Math.pow` is implemented natively by the browser. Thus, although the intention of the code below is
to demonstate the efficient binary algorithim likely in use under the hood, the code below itself
is intented to be educational but not efficient.

```javascript
function toThePowerOf(number, power) {
    if (power != power || (power != 0 && power == power/2)) {
        // the power is infinity or NaN, so return it
        return power;
    }

    if (power == 1) {
        // base case for numbers without decimals (|n| > 1)
        return number;
    }

    if (power == 0) {
        // base case for decimal-only numbers  (1 > |n| > 0)
        return 1;
    }

    if (power < 0) {
        // negative exponents indicate reciprocal
        return 1 / toThePowerOf(number, -power);
    }

    if (0 < power && power < 2) {
        // The `0 < power` is not really needed because of prior
        //    checked cases
        var hasLeadingOne = false;
        if (Math.floor(power) == 1) {
            // the power is 1.decimal, but not 1
            power = power - 1;
            hasLeadingOne = true;
        } else {
            // the power is only a decimal
            hasLeadingOne = false;
        }

        var doublePower = toThePowerOf(number, power * 2);
        var fullPower = Math.sqrt(doublePower);

        if (hasLeadingOne) {
            // insert the number via multiplication here
            fullPower = fullPower * number;
        }

        return fullPower;
    } else if (getDecimal(power) != 0) {
        // the power is greater than two, but has a decimal
        var wholePower = Math.floor(power);
        var decimalPower = getDecimal(power);
        return toThePowerOf(number, wholePower) * toThePowerOf(number, decimalPower);
    } else {
        var hasTrailingOne = (power % 2) == 1;

        if (hasTrailingOne) {
            power = power - 1;
        }

        // the number is greater than one
        // x^n --> x^floor(n/2)
        var halfPower = toThePowerOf(number, Math.floor(power / 2));

        // x^floor(n/2) -> x^n
        var fullPower = halfPower * halfPower;

        if (hasTrailingOne) {
            // multiply it against the number
            fullPower = fullPower * number;
        }

        return fullPower;
    }
}
function getDecimal(number) {
    if (number < 0) {
        // ensure absolute value
        number = -number;
    }
    return number % 1;
}
```
