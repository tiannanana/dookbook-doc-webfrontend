TOPICS: Date.toDateString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toDateString()`

The **`toDateString()`** method returns the date portion of a [`Date`](/en/webfrontend/Date) object
in English in the following format separated by spaces:

1. First three letters of the week day name
1. First three letters of the month name
1. Two digit day of the month, padded on the left a zero if necessary
1. Four digit year (at least), padded on the left with zeros if necessary

E.g. "Thu Jan 01 1970"

## Syntax

```javascript
dateObj.toDateString()
```

**parameter**: No parameters

**Return value**: String

## Description

[`Date`](/en/webfrontend/Date) instances refer to a specific point in time. Calling [`toString()`](/en/webfrontend/Date.toString)
will return the date formatted in a human readable form in English. In SpiderMonkey,
this consists of the date portion (day, month, and year) followed by the time portion
(hours, minutes, seconds, and time zone). Sometimes it is desirable to obtain a string of the
time portion; such a thing can be accomplished with the
[`toTimeString()`](/en/webfrontend/Date.toTimeString) method.

The `toDateString()` method is especially useful because compliant engines implementing ECMA-262 may
differ in the string obtained from [`toString()`](/en/webfrontend/Date.toString) for
[`Date`](/en/webfrontend/Date) objects, as the format is implementation-dependent and
simple string slicing approaches may not produce consistent results across multiple engines.

## Examples

### A basic usage of `toDateString()`

```javascript
var d = new Date(1993, 5, 28, 14, 39, 7);

console.log(d.toString());     // logs Mon Jun 28 1993 14:39:07 GMT-0600 (PDT)
console.log(d.toDateString()); // logs Mon Jun 28 1993
```

!!! warn "Note"
    Month are 0-indexed when used as an argument of [`Date`](/en/webfrontend/Date) (thus `0`
    corresponds to January and `11` to December).
