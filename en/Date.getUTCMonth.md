TOPICS: Date.getUTCMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCMonth()`

The **`getUTCMonth()`** returns the month of the specified date according to universal time, as
a zero-based value (where zero indicates the first month of the year).

## Syntax

```javascript
dateObj.getUTCMonth()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `11`, corresponding to the month of the given
date according to universal time. `0` for January, `1` for February, `2` for March, and so on.

## Examples

### Using `getUTCMonth()`

The following example assigns the month portion of the current date to the variable `month`.

```javascript
var today = new Date();
var month = today.getUTCMonth();
```
