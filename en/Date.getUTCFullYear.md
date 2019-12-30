TOPICS: Date.getUTCFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCFullYear()`

The **`getUTCFullYear()`** method returns the year in the specified date according to universal time.

## Syntax

```javascript
dateObj.getUTCFullYear()
```

**parameter**: No parameters

**Return value**: A number representing the year in the given date according to universal time.

## Description

The value returned by `getUTCFullYear()` is an absolute number that is compliant with `year-2000`,
for example, `1995`.

## Examples

### Using `getUTCFullYear()`

The following example assigns the four-digit value of the current year to the variable `year`.

```javascript
var today = new Date();
var year = today.getUTCFullYear();
```
