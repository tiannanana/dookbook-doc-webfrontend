TOPICS: Date.setTime
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setTime()`

The **`setTime()`** method sets the Date object to the time represented by a number of
`milliseconds` since January 1, 1970, 00:00:00 UTC.

## Syntax

```javascript
dateObj.setTime(timeValue)
```

| parameter | Description |
| :-- | :-- |
| `timeValue` | An integer representing the number of milliseconds since `1` January 1970, 00:00:00 UTC. |

**Return value**: Number

## Description

Use the `setTime()` method to help assign a date and time to another [`Date`](/en/webfrontend/Date) object.

## Examples

### Using `setDate()`

```javascript
var theBigDay = new Date('July 1, 1999');
var sameAsBigDay = new Date();
sameAsBigDay.setTime(theBigDay.getTime());
```
