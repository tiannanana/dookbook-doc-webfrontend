TOPICS: Date.getUTCDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCDate()`

The **`getUTCDate()`** method returns the day (date) of the month in the specified date
according to universal time.

## Syntax

```javascript
dateObj.getUTCDate()
```

**parameter**: No parameters

**Return value**: An integer number, between `1` and `31`, representing the day of the month in
the given date according to universal time.

## Examples

### Using `getUTCDate()`

The following example assigns the day portion of the current date to the variable `day`.

```javascript
var today = new Date();
var day = today.getUTCDate();
```
