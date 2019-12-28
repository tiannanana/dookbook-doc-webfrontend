TOPICS: Date.getUTCDay
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCDay()`

The **`getUTCDay()`** method returns the day of the week in the specified date according to universal
time, where `0` represents Sunday.

## Syntax

```javascript
dateObj.getUTCDay()
```

**parameter**: No parameters

**Return value**: An integer number corresponding to the day of the week for the given date,
according to universal time: `0` for Sunday, `1` for Monday, `2` for Tuesday, and so on.

## Examples

### Using `getUTCDay()`

The following example assigns the weekday portion of the current date to the variable `weekday`.

```javascript
var today = new Date();
var weekday = today.getUTCDay();
```
