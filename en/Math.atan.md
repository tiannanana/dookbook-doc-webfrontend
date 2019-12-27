TOPICS: Math.atan
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.atan()`

The **`Math.atan()`** function returns the arctangent (in radians) of a number, that is

$$
\mathtt{\operatorname{Math.atan}(x)} = \arctan(x) = \text{ the unique } \; y \in \left[-\frac{\pi}{2};
\frac{\pi}{2}\right] \, \text{such that} \; \tan(y) = x
$$

## Syntax

```javascript
Math.atan(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

The `Math.atan()` method returns a numeric value between \\(-\frac{\pi}{2}\\) and
\\(\frac{\pi}{2}\\) radians.

Because `atan()` is a static method of [`Math`](/en/webfrontend/Math), you always use it as
`Math.atan()`, rather than as a method of a [`Math`](/en/webfrontend/Math) object you created
(`Math` is not a constructor).

## Examples

### Using `Math.atan()`

```javascript
Math.atan(1);   // 0.7853981633974483
Math.atan(0);   // 0
Math.atan(-0);  // -0

Math.atan(Infinity);   //  1.5707963267948966
Math.atan(-Infinity);  // -1.5707963267948966

// The angle that the line [(0,0);(x,y)] forms with the x-axis in a Cartesian coordinate system
Math.atan(y / x);
```

Note that you may want to avoid using `±Infinity` for stylistic reasons. In this case,
[`Math.atan2()`](/en/webfrontend/Math.atan2) with `0` as the second argument may be a better solution.
