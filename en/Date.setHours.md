TOPICS: Date.setHours
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setHours()`

The **`setHours()`** method sets the hours for a specified date according to local time, and
returns the number of milliseconds since January 1, 1970 00:00:00 UTC until the time represented
by the updated [`Date`](/en/webfrontend/Date) instance.

## Syntax

```javascript
dateObj.setHours(hoursValue[, minutesValue[, secondsValue[, msValue]]])
```

| parameter | Description |
| :-- | :-- |
| `hoursValue` | Ideally, an integer between `0` and `23`, representing the hour. If a value greater than `23` is provided, the datetime will be incremented by the extra hours. |
| `minutesValue` | Optional. Ideally, an integer between `0` and `59`, representing the minutes. If a value greater than `59` is provided, the datetime will be incremented by the extra minutes. |
| `secondsValue` | Optional. Ideally, an integer between `0` and `59`, representing the seconds. If a value greater than `59` is provided, the datetime will be incremented by the extra seconds. If you specify the `secondsValue` parameter, you must also specify the `minutesValue`. |
| `msValue` | Optional. Ideally, a number between `0` and `999`, representing the milliseconds. If a value greater than 999 is provided, the datetime will be incremented by the extra milliseconds. If you specify the `msValue` parameter, you must also specify the `minutesValue` and `secondsValue`. |

**Return value**: Number

## Description

If you do not specify the `minutesValue`, `secondsValue`, and `msValue` parameters, the values
returned from the [`getMinutes()`](/en/webfrontend/Date.getMinutes),
[`getSeconds()`](/en/webfrontend/Date.getSeconds), and
[`getMilliseconds()`](/en/webfrontend/Date.getMilliseconds) methods are used.

If a parameter you specify is outside of the expected range, `setHours()` attempts to update the
date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example, if you use
`100` for secondsValue, the minutes will be incremented by 1 (`minutesValue + 1`), and `40`
will be used for seconds.

## Examples

### Using `setHours()`

```javascript
var theBigDay = new Date();
theBigDay.setHours(7);
```
