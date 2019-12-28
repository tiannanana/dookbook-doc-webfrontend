TOPICS: Date.setUTCSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCSeconds()`

The **`setUTCSeconds()`** method sets the seconds for a specified date according to universal time.

## Syntax

```javascript
dateObj.setUTCSeconds(secondsValue[, msValue])
```

| parameter | Description |
| :-- | :-- |
| `secondsValue` | An integer between `0` and `59`, representing the seconds. |
| `msValue` | Optional. A number between `0` and `999`, representing the milliseconds. |

**Return value**: Number

## Description

If you do not specify the `msValue` parameter, the value returned from the
[`getUTCMilliseconds()`](/en/webfrontend/Date.getUTCMilliseconds) method is used.

If a parameter you specify is outside of the expected range, `setUTCSeconds()` attempts to update
the date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example, if you
use `100` for `secondsValue`, the minutes stored in the [`Date`](/en/webfrontend/Date) object
will be incremented by `1`, and `40` will be used for seconds.

## Examples

### Using `setUTCSeconds()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCSeconds(20);
```
