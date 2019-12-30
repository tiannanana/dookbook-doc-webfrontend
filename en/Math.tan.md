TOPICS: Math.tan
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.tan()`

The **`Math.tan()`** function returns the tangent of a number.

## Syntax

```javascript
Math.tan(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number representing an angle in radians.|

**Return value**: Number

## Description

The `Math.tan()` method returns a numeric value that represents the tangent of the angle.

Because `tan()` is a static method of `Math`, you always use it as `Math.tan()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.tan()`

```javascript
Math.tan(1); // 1.5574077246549023
```

Because the `Math.tan()` function accepts radians, but it is often easier to work with degrees,
the following function accepts a value in degrees, converts it to radians and returns the tangent.

```javascript
function getTanDeg(deg) {
  var rad = deg * Math.PI/180;
  return Math.tan(rad);
}
```
