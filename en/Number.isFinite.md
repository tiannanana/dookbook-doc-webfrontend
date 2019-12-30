TOPICS: Number.isFinite
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.isFinite()`

The **`Number.isFinite()`** method determines whether the passed value is a finite number.

## Syntax

```javascript
Number.isFinite(value)
```

| parameter | Description |
| :-- | :-- |
| `value` | The value to be tested for finiteness. |

**Return value**: A `Boolean` indicating whether or not the given value is a finite number.

## Description

In comparison to the global [`isFinite()`](/en/webfrontend/isFinite) function, this method doesn't
forcibly convert the parameter to a number. This means only values of the type number, that are also
finite, return `true`.

## Examples

```javascript
Number.isFinite(Infinity);  // false
Number.isFinite(NaN);       // false
Number.isFinite(-Infinity); // false

Number.isFinite(0);         // true
Number.isFinite(2e64);      // true

Number.isFinite('0');       // false, would've been true with
                            // global isFinite('0')
Number.isFinite(null);      // false, would've been true with
                            // global isFinite(null)
```

## Polyfill

```javascript
if (Number.isFinite === undefined) Number.isFinite = function(value) {
    return typeof value === 'number' && isFinite(value);
}
```
