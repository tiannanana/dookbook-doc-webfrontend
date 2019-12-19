TOPICS: Date.getFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getFullYear()`

The `getFullYear()` method returns the year of the specified date according to local time.

Use this method instead of the [`getYear()`](/en/webfrontend/Date.getYear) method.

## Syntax

```javascript
dateObj.getFullYear()
```

**parameter**: No parameters

**Return value**: A number corresponding to the year of the given date, according to local time.

## Description

The value returned by `getFullYear()` is an absolute number. For dates between the years `1000` and
`9999`, `getFullYear()` returns a four-digit number, for example, 1995. Use this function to make
sure a year is compliant with years after `2000`.

## Examples

### Using `getFullYear()`

The following example assigns the four-digit value of the current year to the variable `year`.

```javascript
var today = new Date();
var year = today.getFullYear();
```
