TOPICS: Date.getUTCMinutes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCMinutes()`

The **`getUTCMinutes()`** method returns the minutes in the specified date according to universal time.

## Syntax

```javascript
dateObj.getUTCMinutes()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `59`, representing the minutes in the
given date according to universal time.

## Examples

### Using `getUTCMinutes()`

The following example assigns the minutes portion of the current time to the variable `minutes`.

```javascript
var today = new Date();
var minutes = today.getUTCMinutes();
```
