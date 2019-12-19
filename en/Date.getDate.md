TOPICS: Date.getDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getDate()`

The `getDate()` method returns the day of the month for the specified date according to local time.

## Syntax

```javascript
dateObj.getDate()
```

**parameter**: No parameters

## Examples

### Using `getDate()`

The second statement below assigns the value 25 to the variable day, based on the value of the
[`Date`](/en/webfrontend/Date) object `Xmas95`.

```javascript
var Xmas95 = new Date('December 25, 1995 23:15:30');
var day = Xmas95.getDate();

console.log(day); // 25
```
