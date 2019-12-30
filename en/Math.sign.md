TOPICS: Math.sign
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sign()`

The **`Math.sign()`** function returns either a **positive** or **negative** `+`/`- 1`, indicating the
sign of a number passed into the argument. If the number passed into `Math.sign()` is `0`, it will
return a `+`/`- 0`. Note that if the number is positive, an explicit (`+`) will **not** be returned.

## Syntax

```javascript
Math.sign(x)
```

| parameter | Description |
| :-- | :-- |
| `x` | A number. If this argument is not a `number`, it is implicitly converted to one. |

**Return value**: A number representing the sign of the given argument:

- If the argument is positive, returns `1`.
- If the argument is negative, returns `-1`.
- If the argument is positive zero, returns `0`.
- If the argument is negative zero, returns `-0`.
- Otherwise, `NaN` is returned.

## Description

Because `sign()` is a static method of `Math`, you always use it as `Math.sign()`, rather than as a
method of a [`Math`](/en/webfrontend/Math) object you created (`Math` is not a constructor).

## Examples

### Using `Math.sign()`

```javascript
Math.sign(3);     //  1
Math.sign(-3);    // -1
Math.sign('-3');  // -1
Math.sign(0);     //  0
Math.sign(-0);    // -0
Math.sign(NaN);   // NaN
Math.sign('foo'); // NaN
Math.sign();      // NaN
```

## Polyfill

```javascript
if (!Math.sign) {
  Math.sign = function(x) {
    // If x is NaN, the result is NaN.
    // If x is -0, the result is -0.
    // If x is +0, the result is +0.
    // If x is negative and not -0, the result is -1.
    // If x is positive and not +0, the result is +1.
    return ((x > 0) - (x < 0)) || +x;
    // A more aesthetic pseudo-representation:
    //
    // ( (x > 0) ? 1 : 0 )  // if x is positive, then positive one
    //          +           // else (because you can't be both - and +)
    // ( (x < 0) ? -1 : 0 ) // if x is negative, then negative one
    //         ||           // if x is 0, -0, or NaN, or not a number,
    //         +x           // then the result will be x, (or) if x is
    //                      // not a number, then x converts to number
  };
}
```

In the above polyfill, no extra type-coercing is needed to make `(x > 0)` or `(x < 0)` numbers
because subtracting them from each other forces a type conversion from booleans to numbers.
