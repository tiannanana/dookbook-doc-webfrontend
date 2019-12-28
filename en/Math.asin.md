TOPICS: Math.asin
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.asin()`

The **`Math.asin()`** function returns the arcsine (in radians) of a number, that is

$$
\forall x \in [{-1};1],\;\mathtt{\operatorname{Math.asin}(x)} = \arcsin(x) = \text{ the unique } \;
y \in \left[-\frac{\pi}{2}; \frac{\pi}{2}\right] \, \text{such that} \; \sin(y) = x
$$

## Syntax

```javascript
Math.asin(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

The `Math.asin()` method returns a numeric value between \\(-\frac{\pi}{2}\\)  and  \\(\frac{\pi}{2}\\)
radians for `x` between `-1` and `1`. If the value of x is outside this range, it returns `NaN`.

Because asin() is a static method of [`Math`](/en/webfrontend/Math), you always use it as `Math.asin()`,
rather than as a method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.asin()`

```javascript
Math.asin(-2);  // NaN
Math.asin(-1);  // -1.5707963267948966 (-pi/2)
Math.asin(0);   // 0
Math.asin(0.5); // 0.5235987755982989
Math.asin(1);   // 1.570796326794897 (pi/2)
Math.asin(2);   // NaN
```

For values less than `-1` or greater than `1`, `Math.asin()` returns `NaN`.
