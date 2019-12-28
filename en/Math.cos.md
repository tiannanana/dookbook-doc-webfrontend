TOPICS: Math.cos
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.cos()`

The **Math.cos()** static function returns the cosine of the specified angle, which must be specified
in radians. This value is length adjacent/length hypotenuse .

## Syntax

```javascript
Math.cos(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

The `Math.cos()` method returns a numeric value between `-1` and `1`, which represents the
cosine of the angle.

Because `cos()` is a static method of `Math`, you always use it as `Math.cos()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.cos()`

```javascript
Math.cos(0);           // 1
Math.cos(1);           // 0.5403023058681398

Math.cos(Math.PI);     // -1
Math.cos(2 * Math.PI); // 1
```
