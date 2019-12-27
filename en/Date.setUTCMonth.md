TOPICS: Date.setUTCMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCMonth()`

The **`setUTCMonth()`** method sets the month for a specified date according to universal time.

## Syntax

```javascript
dateObj.setUTCMonth(monthValue[, dayValue])
```

| parameter | Description |
| :-- | :-- |
| `monthValue` | An integer between `0` and `11`, representing the months January through December. |
| `dayValue` | Optional. An integer from `1` to `31`, representing the day of the month. |

**Return value**: Number

## Description

If you do not specify the `dayValue` parameter, the value returned from the
[`getUTCDate()`](/en/webfrontend/Date.getUTCDate) method is used.

If a parameter you specify is outside of the expected range, `setUTCMonth()` attempts to update
the date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example, if you
use `15` for `monthValue`, the year will be incremented by 1, and 3 will be used for month.

## Examples

### Using `setUTCMonth()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCMonth(11);
```
