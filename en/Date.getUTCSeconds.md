TOPICS: Date.getUTCSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCSeconds()`

The **`getUTCSeconds()`** method returns the seconds in the specified date according to universal time.

## Syntax

```javascript
dateObj.getUTCSeconds()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `59`, representing the seconds in the given
date according to universal time.

## Examples

### Using `getUTCSeconds()`

The following example assigns the seconds portion of the current time to the variable `seconds`.

```javascript
var today = new Date();
var seconds = today.getUTCSeconds();
```
