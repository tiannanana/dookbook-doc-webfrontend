TOPICS: Date.setDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setDate()`

The **`setDate()`** method sets the day of the [`Date`](/en/webfrontend/Date) object relative to
the beginning of the currently set month.

## Syntax

```javascript
dateObj.setDate(dayValue)
```

| parameter | Description |
| :-- | :-- |
| `dayValue` | An integer representing the day of the month. |

**Return value**: Number

## Description

If the `dayValue` is outside of the range of date values for the month, `setDate()` will update the
[`Date`](/en/webfrontend/Date) object accordingly.

For example if 0 is provided for `dayValue`, the date will be set to the last day of the previous month.

If a negative number is provided for `dayValue`, the date will be set counting backwards from the
last day of the previous month. `-1` would result in the date being set to `1` day before the last
day of the previous month.

## Examples

### Using `setDate()`

```javascript
var theBigDay = new Date(1962, 6, 7); // 1962-07-07 (7th of July 1962)
theBigDay.setDate(24);  // 1962-07-24 (24th of July 1962)
theBigDay.setDate(32);  // 1962-08-01 (1st of August 1962)
theBigDay.setDate(22);  // 1962-08-22 (22th of August 1962)
theBigDay.setDate(0);   // 1962-07-31 (31th of July 1962)
theBigDay.setDate(98);  // 1962-10-06 (6th of October 1962)
theBigDay.setDate(-50); // 1962-08-11 (11th of August 1962)
```
