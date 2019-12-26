TOPICS: Date.setUTCDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCDate()`

The **`setUTCDate()`** method sets the day of the month for a specified date according to universal time.

## Syntax

```javascript
dateObj.setUTCDate(dayValue)
```

| parameter | Description |
| :-- | :-- |
| `dayValue` | An integer from `1` to `31`, representing the day of the month. |

**Return value**: An integer number, between `0` and `59`, representing the seconds in the given
date according to universal time.

## Description

If a parameter you specify is outside of the expected range, `setUTCDate()` attempts to update the
date information in the [`Date`](/en/webfrontend/Date) object accordingly. For example, if you use
`40` for `dayValue`, and the month stored in the [`Date`](/en/webfrontend/Date) object is June, the
day will be changed to `10` and the month will be incremented to July.

## Examples

### Using `setUTCDate()`

```javascript
const event = new Date('August 19, 1975 23:15:30 GMT-3:00');

console.log(event.getUTCDate());
// expected output: 20

event.setUTCDate(19);

console.log(event.getUTCDate());
// expected output: 19
```
