TOPICS: Math.trunc
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.trunc()`

The **`Math.trunc()`** function returns the integer part of a number by removing any fractional digits.

## Syntax

```javascript
Math.trunc(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Unlike the other three `Math` methods: [`Math.floor()`](/en/webfrontend/Math.floor), [`Math.ceil()`](/en/webfrontend/Math.ceil)
and [`Math.round()`](/en/webfrontend/Math.round), the way `Math.trunc()` works is very simple. It
truncates (cuts off) the dot and the digits to the right of it, no matter whether the argument
is a positive or negative number.

The argument passed to this method will be converted to number type implicitly.

Because `trunc()` is a static method of `Math`, you always use it as `Math.trunc()`, rather than as
a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.trunc()`

```javascript
Math.trunc(13.37);    // 13
Math.trunc(42.84);    // 42
Math.trunc(0.123);    //  0
Math.trunc(-0.123);   // -0
Math.trunc('-1.123'); // -1
Math.trunc(NaN);      // NaN
Math.trunc('foo');    // NaN
Math.trunc();         // NaN
```

## Polyfill

```javascript
if (!Math.trunc) {
  Math.trunc = function(v) {
    v = +v;
    if (!isFinite(v)) return v;

    return (v - v % 1)   ||   (v < 0 ? -0 : v === 0 ? v : 0);

    // returns:
    //  0        ->  0
    // -0        -> -0
    //  0.2      ->  0
    // -0.2      -> -0
    //  0.7      ->  0
    // -0.7      -> -0
    //  Infinity ->  Infinity
    // -Infinity -> -Infinity
    //  NaN      ->  NaN
    //  null     ->  0
  };
}
```

or:

```javascript
if (!Math.trunc) {
  Math.trunc = function (v) {
    return v < 0 ? Math.ceil(v) : Math.floor(v);
  };
}
```
