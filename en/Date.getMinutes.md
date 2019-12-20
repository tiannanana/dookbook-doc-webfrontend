TOPICS: Date.getMinutes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getMinutes()`

The `getMinutes()` method returns the minutes in the specified date according to local time.

## Syntax

```javascript
dateObj.getMinutes()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `59`, representing the minutes in the given
date according to local time.

## Examples

### Using `getMinutes()`

The second statement below assigns the value 15 to the variable `minutes`, based on the value of the
[`Date`](/en/webfrontend/Date) object `Xmas95`.

```javascript
var Xmas95 = new Date('December 25, 1995 23:15:30');
var minutes = Xmas95.getMinutes();

console.log(minutes); // 15
```
