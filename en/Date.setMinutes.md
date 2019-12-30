TOPICS: Date.setMinutes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setMinutes()`

The **`setMinutes()`** method sets the minutes for a specified date according to local time.

## Syntax

```javascript
dateObj.setMinutes(minutesValue[, secondsValue[, msValue]])
```

| parameter | Description |
| :-- | :-- |
| `minutesValue` | An integer between `0` and `59`, representing the minutes. |
| `secondsValue` | Optional. An integer between `0` and `59`, representing the seconds. If you specify the `secondsValue` parameter, you must also specify the `minutesValue`. |
| `msValue` | Optional. A number between `0` and `999`, representing the milliseconds. If you specify the `msValue` parameter, you must also specify the `minutesValue` and `secondsValue`. |

**Return value**: Number

## Description

If you do not specify the `secondsValue` and `msValue` parameters, the values returned from
[`getSeconds()`](/en/webfrontend/Date.getSeconds) and
[`getMilliseconds()`](/en/webfrontend/Date.getSeconds) methods are used.

If a parameter you specify is outside of the expected range, `setMinutes()` attempts to update the
date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example,
if you use `100` for `secondsValue`, the minutes will be incremented by 1 (`minutesValue + 1`),
and `40` will be used for seconds.

## Examples

### Using `setMinutes()`

```javascript
var theBigDay = new Date();
theBigDay.setMinutes(45);
```
