TOPICS: Date.getMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getMonth()`

The `getMonth()` method returns the month in the specified date according to local time, as a
zero-based value (where zero indicates the first month of the year).

## Syntax

```javascript
dateObj.getMonth()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `11`, representing the month in the given date
according to local time. `0` corresponds to January, `1` to February, and so on.

## Examples

### Using `getMonth()`

The second statement below assigns the value 11 to the variable `month`, based on the value of the
[`Date`](/en/webfrontend/Date) object `Xmas95`.

```javascript
var Xmas95 = new Date('December 25, 1995 23:15:30');
var month = Xmas95.getMonth();

console.log(month); // 11
```

!!! warn "Note"
    If needed, the full name of a month ("`January`" for example) can be obtained by using
    [`Intl.DateTimeFormat()`](/en/webfrontend/Intl.DateTimeFormat) with an `options` parameter.
    Using this method, internationalization is made easier:

```javascript
var options = { month: 'long'};
console.log(new Intl.DateTimeFormat('en-US', options).format(Xmas95));
// December
console.log(new Intl.DateTimeFormat('de-DE', options).format(Xmas95));
// Dezember
```
