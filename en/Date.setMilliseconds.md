TOPICS: Date.setMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setMilliseconds()`

The **`setMilliseconds()`** method sets the milliseconds for a specified date according to local time.

## Syntax

```javascript
dateObj.setMilliseconds(millisecondsValue)
```

| parameter | Description |
| :-- | :-- |
| `millisecondsValue` | A number between `0` and `999`, representing the milliseconds. |

**Return value**: Number

## Description

If you specify a number outside the expected range, the date information in the [`Date`](/en/webfrontend/Date)
object is updated accordingly. For example, if you specify 1005, the number of seconds is
incremented by 1, and 5 is used for the milliseconds.

## Examples

### Using `setMilliseconds()`

```javascript
var theBigDay = new Date();
theBigDay.setMilliseconds(100);
```
