TOPICS: Date.setSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setSeconds()`

The **`setSeconds()`** method sets the seconds for a specified date according to local time.

## Syntax

```javascript
dateObj.setSeconds(secondsValue[, msValue])
```

| parameter | Description |
| :-- | :-- |
| `secondsValue` | An integer between `0` and `59`, representing the seconds. |
| `msValue` | Optional. A number between `0` and `999`, representing the milliseconds. |

**Return value**: Number

## Description

If you do not specify the `msValue` parameter, the value returned from the
[`getMilliseconds()`](/en/webfrontend/Date.getMilliseconds) method is used.

If a parameter you specify is outside of the expected range, `setSeconds()` attempts to update
the date information in the [`Date`](/en/webfrontend/Date) object accordingly.
For example, if you use `100` for `secondsValue`, the minutes stored in the
[`Date`](/en/webfrontend/Date) object will be incremented by 1, and 40 will be used for seconds.

## Examples

### Using `setSeconds()`

```javascript
const event = new Date('August 19, 1975 23:15:30');

event.setSeconds(42);

console.log(event.getSeconds());
// expected output: 42

console.log(event);
// Sat Apr 19 1975 23:15:42 GMT+0100 (CET)
// (note: your timezone may vary)
```
