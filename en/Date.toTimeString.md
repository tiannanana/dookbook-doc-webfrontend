TOPICS: Date.toTimeString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toTimeString()`

The **`toTimeString()`** method returns the time portion of a [`Date`](/en/webfrontend/Date) object
in human readable form in American English.

## Syntax

```javascript
dateObj.toTimeString()
```

**parameter**: No parameters

**Return value**: String

## Description

[`Date`](/en/webfrontend/Date) instances refer to a specific point in time. Calling [`toString()`](/en/webfrontend/Date.toString)
will return the date formatted in a human readable form in American English. In SpiderMonkey,
this consists of the date portion (day, month, and year) followed by the time portion (hours,
minutes, seconds, and time zone). Sometimes it is desirable to obtain a string of the time portion;
such a thing can be accomplished with the `toTimeString()` method.

The `toTimeString()` method is especially useful because compliant engines implementing ECMA-262
may differ in the string obtained from [`toString()`](/en/webfrontend/Date.toString) for
[`Date`](/en/webfrontend/Date) objects, as the format is implementation-dependent; simple
string slicing approaches may not produce consistent results across multiple engines.

## Examples

### A basic usage of `toTimeString()`

```javascript
var d = new Date(1993, 6, 28, 14, 39, 7);

console.log(d.toString());     // Wed Jul 28 1993 14:39:07 GMT-0600 (PDT)
console.log(d.toTimeString()); // 14:39:07 GMT-0600 (PDT)
```
