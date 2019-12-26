TOPICS: Date.getUTCMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCMilliseconds()`

The **`getUTCMilliseconds()`** method returns the milliseconds portion of the time object's value.

## Syntax

```javascript
dateObj.getUTCMilliseconds()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `999`, representing the `milliseconds` portion
of the given date object.  This method is a companion to the other UTC based methods that give hour
portion, minute portion, etc.; this method gives `milliseconds` portion.  

Not to be confused with Unix epoch time.  To get total `milliseconds` since 1970/01/01,
use the method "`.getTime()`".

## Examples

### Using `getUTCMilliseconds()`

The following example assigns the milliseconds portion of the current time to the variable `milliseconds`.

```javascript
var today = new Date();
var milliseconds = today.getUTCMilliseconds();
```
