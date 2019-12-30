TOPICS: Date.getSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getSeconds()`

The **`getSeconds()`** method returns the seconds in the specified date according to local time.

## Syntax

```javascript
dateObj.getSeconds()
```

**parameter**: No parameters

**Return value**: An integer number, between `0` and `59`, representing the seconds in
the given date according to local time.

## Examples

### Using `getSeconds()`

The second statement below assigns the value 30 to the variable `seconds`, based on the value of the
[`Date`](/en/webfrontend/Date) object `Xmas95`.

```javascript
var Xmas95 = new Date('December 25, 1995 23:15:30');
var seconds = Xmas95.getSeconds();

console.log(seconds); // 30
```
