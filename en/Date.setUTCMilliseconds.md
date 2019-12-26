TOPICS: Date.setUTCMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCMilliseconds()`

The **`setUTCMilliseconds()`** method sets the milliseconds for a specified date
according to universal time.

## Syntax

```javascript
dateObj.setUTCMilliseconds(millisecondsValue)
```

| parameter | Description |
| :-- | :-- |
| `millisecondsValue` | A number between `0` and `999`, representing the milliseconds. |

**Return value**: Number

## Description

If a parameter you specify is outside of the expected range, `setUTCMilliseconds()` attempts to
update the date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example,
if you use `1100` for `millisecondsValue`, the seconds stored in the [`Date`](/en/webfrontend/Date)
object will be incremented by `1`, and `100` will be used for milliseconds.

## Examples

### Using `setUTCMilliseconds()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCMilliseconds(500);
```
