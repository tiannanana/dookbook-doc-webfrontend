TOPICS: Date.setMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setMonth()`

The **`setMonth()`** method sets the month for a specified date according to the currently set year.

## Syntax

```javascript
dateObj.setMonth(monthValue[, dayValue])
```

| parameter | Description |
| :-- | :-- |
| `monthValue` | An integer between `0` and `11`, representing the months January through December. |
| `dayValue` | Optional. An integer from `1` to `31`, representing the day of the month. |

**Return value**: Number

## Description

If you do not specify the `dayValue` parameter, the value returned from the
[`getDate()`](/en/webfrontend/Date.getDate) method is used.

If a parameter you specify is outside of the expected range, `setMonth()` attempts to update the
date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example,
if you use `15` for monthValue, the year will be incremented by `1`, and `3` will be used for month.

The current day of month will have an impact on the behaviour of this method. Conceptually it
will add the number of days given by the current day of the month to the 1st day of the new month
specified as the parameter, to return the new date. For example, if the current value is 31st
August 2016, calling setMonth with a value of 1 will return 2nd March 2016. This is because in
2016 February had 29 days.

## Examples

### Using `setMonth()`

```javascript
var theBigDay = new Date();
theBigDay.setMonth(6);

//Watch out for end of month transitions
var endOfMonth = new Date(2016, 7, 31);
endOfMonth.setMonth(1);
console.log(endOfMonth); //Wed Mar 02 2016 00:00:00
```
