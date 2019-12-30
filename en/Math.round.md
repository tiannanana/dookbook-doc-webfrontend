TOPICS: Math.round
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.round()`

The **`Math.round()`** function returns the value of a number rounded to the nearest integer.

## Syntax

```javascript
Math.round(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

If the fractional portion of the argument is greater than 0.5, the argument is rounded to the
integer with the next higher absolute value. If it is less than 0.5, the argument is rounded to
the integer with the lower absolute value.  If the fractional portion is exactly 0.5, the argument
is rounded to the next integer in the direction of `+∞`. **Note that this differs from many
languages' `round()` functions, which often round this case to the next integer away from zero**,
instead giving a different result in the case of negative numbers with a fractional part of exactly 0.5.

Because `round()` is a static method of `Math`, you always use it as `Math.round()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` has no constructor).

## Examples

```javascript
Math.round( 20.49); //  20
Math.round( 20.5 ); //  21
Math.round( 42   ); //  42
Math.round(-20.5 ); // -20
Math.round(-20.51); // -21
```

## Demonstrative Implementation

Below is a snippet of code that is functionally equivelent to `math.round` except that the snippet
of code below is slower than `Math.round`. The purpose of the snippet of code below is to
demonstrate how `Math.round` works.

```javascript
function vanilla_round(x) {
    var y = Math.abs(x) + 0.5; // so that less than 1/2 rounds down; greater rounds up
    return Math.floor(x+0.5)
}
```

The modulus operator above gets the decimal part of `x`. Further, the above code snippet could be
modified to round to a certain precision on a number:

```javascript
function round_to_precision(x, precision) {
    var y = +x + (precision === undefined ? 0.5 : precision/2);
    return y - (y % (precision === undefined ? 1 : +precision));
}
```

Examples:

```javascript
round_to_precision(11, 2); // outputs 12
round_to_precision(11, 3); // outputs 12
round_to_precision(11, 4); // outputs 12
round_to_precision(11, 5); // outputs 10
round_to_precision(11, 6); // outputs 12
round_to_precision(11, 7); // outputs 14
round_to_precision(11, 8); // outputs 8
round_to_precision(3.7, 0.5); // outputs 3.5
round_to_precision(3.75, 0.5); // outputs 4
round_to_precision(3.8, 0.5); // outputs 4
```
