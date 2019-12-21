TOPICS: Number.isSafeInteger
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.isSafeInteger()`

The `Number.isSafeInteger()` method determines whether the provided value is a number that is a
safe integer.

A safe integer is an integer that

- can be exactly represented as an IEEE-754 double precision number, and
- whose IEEE-754 representation cannot be the result of rounding any other integer to fit the
IEEE-754 representation.

For example, `2^53^ - 1` is a safe integer: it can be exactly represented, and no other integer
rounds to it under any IEEE-754 rounding mode. In contrast, `2^53^` is not a safe integer: it can
be exactly represented in IEEE-754, but the integer `2^53^ + 1` can't be directly represented
in IEEE-754 but instead rounds to 253 under round-to-nearest and round-to-zero rounding.
The safe integers consist of all integers from `-(2^53^ - 1)` inclusive to `2^53^ - 1`
inclusive (± `9007199254740991` or ± 9,007,199,254,740,991).  

Handling values larger or smaller than ~9 quadrillion with full precision requires using an
arbitrary precision arithmetic library.  See What Every Programmer Needs to Know about Floating
Point Arithmetic for more information on floating point representations of numbers.

For larger integers, consider using the [`BigInt`](/en/webfrontend/BigInt) type.

## Syntax

```javascript
Number.isSafeInteger(testValue)
```

| parameter | Description |
| :-- | :-- |
| `testValue` | The value to be tested for being a safe integer. |

**Return value**: A `Boolean` indicating whether or not the given value is a number that is a safe integer.

## Description

In comparison to the global [`isFinite()`](/en/webfrontend/isFinite) function, this method doesn't
forcibly convert the parameter to a number. This means only values of the type number, that are also
finite, return `true`.

## Examples

```javascript
Number.isSafeInteger(3);                    // true
Number.isSafeInteger(Math.pow(2, 53));      // false
Number.isSafeInteger(Math.pow(2, 53) - 1);  // true
Number.isSafeInteger(NaN);                  // false
Number.isSafeInteger(Infinity);             // false
Number.isSafeInteger('3');                  // false
Number.isSafeInteger(3.1);                  // false
Number.isSafeInteger(3.0);                  // true
```

## Polyfill

```javascript
Number.isSafeInteger = Number.isSafeInteger || function (value) {
   return Number.isInteger(value) && Math.abs(value) <= Number.MAX_SAFE_INTEGER;
};
```
