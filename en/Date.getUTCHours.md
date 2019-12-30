TOPICS: Date.getUTCHours
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCHours()`

The **`getUTCHours()`** method returns the hours in the specified date according to universal time.

## Syntax

```javascript
dateObj.getUTCHours()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `23`, representing the hours in the given
date according to universal time.

## Examples

### Using `getUTCHours()`

The following example assigns the hours portion of the current time to the variable `hours`.

```javascript
var today = new Date();
var hours = today.getUTCHours();
```
