TOPICS: Date.getTimezoneOffset
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getTimezoneOffset()`

The **`getTimezoneOffset()`** method returns the time zone difference, in minutes, from current
locale (host system settings) to UTC.

## Syntax

```javascript
dateObj.getTimezoneOffset()
```

**parameter**: No parameters

**Return value**: A number representing the time-zone offset, in minutes, from the date based on
current host system settings to UTC.

## Description

The time-zone offset is the difference, in minutes, from local time to UTC. Note that this means
that the offset is positive if the local timezone is behind UTC and negative if it is ahead.
For example, for time zone `UTC+10:00` (Australian Eastern Standard Time, Vladivostok Time,
Chamorro Standard Time), `-600` will be returned.

| Current Locale | UTC-8 | UTC | UTC+3 |
| :---- | :---- | :---- | :---- |
| Return Value | 480 | 0 | -180 |

The time zone offset returned is the one that applies for the Date that it's called on. Where
the host system is configured for daylight saving, the offset will change depending on the
date and time that the Date represents and that daylight saving applies.

## Examples

### Using `getTimezoneOffset()`

```javascript
// Get current timezone offset for host device
var x = new Date();
var currentTimeZoneOffsetInHours = x.getTimezoneOffset() / 60;
// 1

// Get timezone offset for International Labour Day (May 1) in 2016
// Be careful, the Date() constructor uses 0-indexed month so May is
// represented with 4 (and not 5)
var labourDay = new Date(2016, 4, 1)
var labourDayOffset = labourDay.getTimezoneOffset() / 60;
```
