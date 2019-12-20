TOPICS: Date.getMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getMilliseconds()`

The `getMilliseconds()` method returns the milliseconds in the specified date according to local time.

## Syntax

```javascript
dateObj.getMilliseconds()
```

**parameter**: No parameters

**Return value**: A number, between `0` and `999`, representing the milliseconds for the given date
according to local time.

## Examples

### Using `getMilliseconds()`

The following example assigns the milliseconds portion of the current time to the variable `milliseconds`:

```javascript
var today = new Date();
var milliseconds = today.getMilliseconds();
```
