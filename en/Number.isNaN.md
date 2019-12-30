TOPICS: Number.isNaN
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.isNaN()`

The **`Number.isNaN()`** method determines whether the passed value is `NaN` and its type is [`Number`](/en/webfrontend/Number).
It is a more robust version of the original, global [`isNaN()`](/en/webfrontend/isNaN).

## Syntax

```javascript
Number.isNaN(value)
```

| parameter | Description |
| :-- | :-- |
| `value` | The value to be tested for `NaN`. |

**Return value**: **`true`** if the given value is `NaN` and its type is `Number`; otherwise, **`false`**.

## Description

Due to both equality operators, `==` and `===`, evaluating to false when checking if `NaN` is `NaN`,
the function `Number.isNaN()` has become necessary. This situation is unlike all other possible
value comparisons in JavaScript.

In comparison to the global [`isNaN()`](/en/webfrontend/isNaN) function, `Number.isNaN()` doesn't
suffer the problem of forcefully converting the parameter to a number. This means it is now safe to
pass values that would normally convert to `NaN`, but aren't actually the same value as `NaN`.
This also means that only values of the type number, that are also `NaN`, return `true`.

## Examples

```javascript
Number.isNaN(NaN);        // true
Number.isNaN(Number.NaN); // true
Number.isNaN(0 / 0);      // true

// e.g. these would have been true with global isNaN()
Number.isNaN('NaN');      // false
Number.isNaN(undefined);  // false
Number.isNaN({});         // false
Number.isNaN('blabla');   // false

// These all return false
Number.isNaN(true);
Number.isNaN(null);
Number.isNaN(37);
Number.isNaN('37');
Number.isNaN('37.37');
Number.isNaN('');
Number.isNaN(' ');
```

## Polyfill

The following works because NaN is the only value in JavaScript which is not equal to itself.

```javascript
Number.isNaN = Number.isNaN || function isNaN(input) {
    return typeof input === 'number' && input !== input;
}
```
