TOPICS: Math.acos
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.acos()`

The **`Math.acos()`** function returns the arccosine (in radians) of a number, that is

$$
\forall x \in [{-1};1],\;\mathtt{\operatorname{Math.acos}(x)} = \arccos(x) = \text{ the unique } \;
y \in [0; \pi] \, \text{such that} \; \cos(y) = x
$$

## Syntax

```javascript
Math.acos(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number representing a cosine, where `x` is between `-1` and `1`. |

**Return value**: Number

## Description

The `Math.acos()` method returns a numeric value between `0` and `π` radians for x between
`-1` and `1`. If the value of `x` is outside this range, it returns `NaN`.

Because `acos()` is a static method of [`Math`](/en/webfrontend/Math), you always use it as
`Math.acos()`, rather than as a method of a [`Math`](/en/webfrontend/Math) object you created
(`Math` is not a constructor).

## Examples

### Using `Math.acos()`

```javascript
Math.acos(-2);  // NaN
Math.acos(-1);  // 3.141592653589793
Math.acos(0);   // 1.5707963267948966
Math.acos(0.5); // 1.0471975511965979
Math.acos(1);   // 0
Math.acos(2);   // NaN
```

For values less than `-1` or greater than `1`, `Math.acos()` returns `NaN`.
