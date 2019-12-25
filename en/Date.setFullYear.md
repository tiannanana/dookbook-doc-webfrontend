TOPICS: Date.setFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setFullYear()`

The **`setFullYear()`** method sets the full year for a specified date according to local time.
Returns new timestamp.

## Syntax

```javascript
dateObj.setFullYear(yearValue[, monthValue[, dateValue]])
```

| parameter | Description |
| :-- | :-- |
| `yearValue` | An integer specifying the numeric value of the year, for example, 1995. |
| `monthValue` | Optional. An integer between `0` and `11` representing the months January through December. |
| `dateValue` | Optional. An integer between `1` and `31` representing the day of the month. If you specify the `dateValue` parameter, you must also specify the `monthValue`. |

**Return value**: Number

## Description

If you do not specify the `monthValue` and `dateValue` parameters, the values returned from the
[`getMonth()`](/en/webfrontend/Date.getDate) and [`getDate()`](/en/webfrontend/Date.getDate)
methods are used.

If a parameter you specify is outside of the expected range, `setFullYear()` attempts to update the
other parameters and the date information in the [`Date`](/en/webfrontend/Date) object accordingly.
For example, if you specify 15 for `monthValue`, the year is incremented by 1 (`yearValue + 1`),
and `3` is used for the month.

## Examples

### Using `setFullYear()`

```javascript
var theBigDay = new Date();
theBigDay.setFullYear(1997);
```
