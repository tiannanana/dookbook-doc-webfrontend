TOPICS: Date.setUTCFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCFullYear()`

The **`setUTCFullYear()`** method sets the full year for a specified date according to universal time.

## Syntax

```javascript
dateObj.setUTCFullYear(yearValue[, monthValue[, dayValue]])
```

| parameter | Description |
| :-- | :-- |
| `yearValue` | An integer specifying the numeric value of the year, for example, 1995. |
| `monthValue` | Optional. An integer between `0` and `11` representing the months January through December. |
| `dayValue` | Optional. An integer between `1` and `31` representing the day of the month. If you specify the `dayValue` parameter, you must also specify the `monthValue`. |

**Return value**: Number

## Description

If a parameter you specify is outside of the expected range, `setUTCDate()` attempts to update the
date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example, if you use
`40` for `dayValue`, and the month stored in the [`Date`](/en/webfrontend/Date) object is June, the
day will be changed to `10` and the month will be incremented to July.

If you do not specify the monthValue and dayValue parameters, the values returned from the
[`getUTCMonth()`](/en/webfrontend/Date.getUTCMonth) and
[`getUTCDate()`](/en/webfrontend/Date.getUTCDate) methods are used.

If a parameter you specify is outside of the expected range, `setUTCFullYear()` attempts to update
the other parameters and the date information in the [`Date`](/en/webfrontend/Date) object
accordingly. For example, if you specify 15 for `monthValue`, the year is incremented by 1
(`yearValue + 1`), and 3 is used for the month.

## Examples

### Using `setUTCFullYear()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCFullYear(1997);
```
