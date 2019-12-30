TOPICS: Math.min
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.min()`

The static function **`Math.min()`** returns the lowest-valued number passed into it, or `NaN` if
any parameter isn't a number and can't be converted into one.

## Syntax

```javascript
Math.min([value1[, value2[, ...]]])
```

| parameter | Description |
| :-- | :-- |
| `value1, value2, ...` | Zero or more numbers among which the lowest value will be selected and returned. |

**Return value**: The smallest of the given numbers. If any one or more of the parameters cannot be
converted into a number, `NaN` is returned. The result is `Infinity` if no parameters are provided.

## Description

Because `min()` is a static method of `Math`, you always use it as `Math.min()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

If no arguments are given, the result is `Infinity`.

If at least one of arguments cannot be converted to a number, the result is `NaN`.

## Examples

### Using `Math.min()`

This finds the min of `x` and y and assigns it to `z`:

```javascript
var x = 10, y = -20;
var z = Math.min(x, y);
```

### Clipping a value with `Math.min()`

`Math.min()` is often used to clip a value so that it is always less than or equal to a boundary.
For instance, this

```javascript
var x = f(foo);

if (x > boundary) {
  x = boundary;
}
may be written as this

var x = Math.min(f(foo), boundary);
```

[`Math.max()`](/en/webfrontend/Math.max) can be used in a similar way to clip a value at the other end.
