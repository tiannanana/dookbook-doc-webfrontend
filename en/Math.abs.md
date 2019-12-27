TOPICS: Math.abs
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.abs()`

The **`Math.abs()`** function returns the absolute value of a number, that is

$$
{\mathtt{\operatorname{Math.abs}(x)}} = {|x|}
= \begin{cases} x & \text{if} \quad x \geq 0 \\ -x & \text{if} \quad x < 0 \end{cases}
$$

## Syntax

```javascript
Math.abs(x);
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. |

**Return value**: Number

## Description

Because `abs()` is a static method of [`Math`](/en/webfrontend/Math), you always use it as
`Math.abs()`, rather than as a method of a [`Math`](/en/webfrontend/Math) object you created
(`Math` is not a constructor).

## Examples

### Behavior of `Math.abs()`

Passing an empty object, an array with more than one member, a non-numeric string or `undefined`/empty
variable returns `NaN`. Passing `null`, an empty string or an empty array returns 0.

```javascript
Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs('');       // 0
Math.abs([]);       // 0
Math.abs([2]);      // 2
Math.abs([1,2]);    // NaN
Math.abs({});       // NaN
Math.abs('string'); // NaN
Math.abs();         // NaN
```
