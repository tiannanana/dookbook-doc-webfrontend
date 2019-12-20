TOPICS: Date
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date`

Creates a JavaScript `Date` instance that represents a single moment in time in a
platform-independent format. `Date` objects contain a `Number` that represents milliseconds
since `1` January 1970 UTC.

## Syntax

```javascript
new Date();
new Date(value);
new Date(dateString);
new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);
```

!!! warn "Note"
    The only correct way to instantiate a new `Date` object is by using the new operator. If you
    simply call the `Date` object directly, such as `now = Date()`, the returned value is a
    string rather than a `Date` object.

## Parameters

There are four basic forms for the `Date()` constructor:

### No parameters

When no parameters are provided, the newly-created `Date` object represents the current `date` and
time as of the time of instantiation.

### Time value or timestamp number

| parameter | Description |
| :-- | :-- |
| `value` | An integer value representing the number of milliseconds since January `1`, `1970`, `00:00:00 UTC` (the ECMAScript epoch, equivalent to the UNIX epoch), with leap seconds ignored. Keep in mind that most UNIX Timestamp functions are only accurate to the nearest second. |

### Timestamp string

| parameter | Description |
| :-- | :-- |
| `dateString` | A string value representing a `date`, specified in a format recognized by the [`Date.parse()`](/en/webfrontend/Date.parse) method (these formats are IETF-compliant RFC 2822 timestamps and also strings in a version of ISO8601).

!!! warn "Note"
    Parsing of date strings with the `Date` constructor (and `Date.parse()`, which works the same way)
    is strongly discouraged due to browser differences and inconsistencies. Support for [RFC 2822](https://tools.ietf.org/html/rfc2822)
    format strings is by convention only. Support for ISO 8601 formats differs in that date-only
    strings (e.g. "1970-01-01") are treated as UTC, not local.

### Individual date and time component values

Given at least a year and month, this form of `Date()` returns a `Date` object whose component values
(year, month, day, hour, minute, second, and millisecond) all come from the following parameters.
Any missing fields are given the lowest possible value (1 for the `day` and 0 for every other component).

| parameter | Description |
| :-- | :-- |
| `year` | Integer value representing the year. Values from `0` to `99` map to the years `1900` to `1999`; all other values are the actual year. See the example below. |
| `monthIndex` | Integer value representing the month, beginning with `0` for January to `11` for December. |
| `day` Optional | Integer value representing the `day` of the month. If not specified, the default value of `1` is used. |
| `hours` Optional | Integer value representing the hour of the `day`. The default is `0` (midnight).
| `minutes` Optional | Integer value representing the minute segment of a time. The default is `0` minutes past the hour.  |
| `seconds` Optional | Integer value representing the second segment of a time. The default is zero seconds past the minute. |
| `milliseconds` Optional | Integer value representing the millisecond segment of a time. The default is `0` milliseconds past the second. |

## User notes

### The ECMAScript epoch and timestamps

A JavaScript date is fundamentally specified as the number of milliseconds that have elapsed since
midnight on January `1`, `1970`, `UTC`. This date and time is the same as the **UNIX epoch**,
which is the predominant base value for computer-recorded date and time values.

!!! warn "Note"
    It's important to keep in mind that while the time value at the heart of a `Date` object is
    `UTC`, the basic methods to fetch the `date` and time or its components all work in the local
    (i.e. host system) time zone and offset.

A day is made up of `86,400,000` milliseconds. Given that and the size of the underlying `number`
used to record the timestamp, and it can be calculated that the `Date` object can represent dates
within ±100,000,000 (one hundred million) days relative to January `1`, `1970` `UTC`. That means that
in the year 293,742, we'll have to think about fixing this.

### Date format and time zone conversions

There are a number of methods available to obtain the date in various formats, as well as to do
time zone conversions. Especially useful are the functions that output the date and time in
Coordinated Universal Time (UTC), the global standard time defined by the World Time Standard.
This time is historically known as Greenwich Mean Time, as UTC lies along the meridian that
includes London and nearby Greenwhich in the United Kingdom. The user's device provides the local time.

In addition to methods to read and alter individual components of the local date and time, such as
[`getDay()`](/en/webfrontend/getDay) and [`setHours()`](/en/webfrontend/setHours), there are also
versions of the same methods that read and manipulate the date and time using UTC, such as
[`getUTCDay()`](/en/webfrontend/getUTCDay) and [`setUTCHours()`](/en/webfrontend/setUTCHours).

## Examples

### Several ways to create a `Date` object

The following examples show several ways to create JavaScript dates:

!!! warn "Note"
    parsing of date strings with the `Date` constructor (and `Date.parse`, they are equivalent) is
    strongly discouraged due to browser differences and inconsistencies.

```javascript
var today = new Date();
var birthday = new Date('December 17, 1995 03:24:00');
var birthday = new Date('1995-12-17T03:24:00');
var birthday = new Date(1995, 11, 17);
var birthday = new Date(1995, 11, 17, 3, 24, 0);
```

### Two digit years map to 1900 - 1999

In order to create and get dates between the years 0 and 99 the [`Date.setFullYear()`](/en/webfrontend/Date.setFullYear)
and [`Date.getFullYear()`](/en/webfrontend/Date.getFullYear) methods should be used.

```javascript
var date = new Date(98, 1); // Sun Feb 01 1998 00:00:00 GMT+0000 (GMT)

// Deprecated method, 98 maps to 1998 here as well
date.setYear(98);           // Sun Feb 01 1998 00:00:00 GMT+0000 (GMT)

date.setFullYear(98);       // Sat Feb 01 0098 00:00:00 GMT+0000 (BST)
```

### Calculating elapsed time

The following examples show how to determine the elapsed time between two JavaScript dates in milliseconds.

Due to the differing lengths of days (due to daylight saving changeover), months and years,
expressing elapsed time in units greater than hours, minutes and seconds requires addressing a
number of issues and should be thoroughly researched before being attempted.

```javascript
// using Date objects
var start = Date.now();

// the event to time goes here:
doSomethingForALongTime();
var end = Date.now();
var elapsed = end - start; // elapsed time in milliseconds
```

```javascript
// using built-in methods
var start = new Date();

// the event to time goes here:
doSomethingForALongTime();
var end = new Date();
var elapsed = end.getTime() - start.getTime(); // elapsed time in milliseconds
```

```javascript
// to test a function and get back its return
function printElapsedTime(fTest) {
  var nStartTime = Date.now(),
      vReturn = fTest(),
      nEndTime = Date.now();

  console.log('Elapsed time: ' + String(nEndTime - nStartTime) + ' milliseconds');
  return vReturn;
}

var yourFunctionReturn = printElapsedTime(yourFunction);
```

!!! warn "Note"
    In browsers that support the Web Performance API's high-resolution time feature,
    [`Performance.now()`](/en/webfrontend/Performance.now) can provide more reliable and precise
    measurements of elapsed time than [`Date.now()`](/en/webfrontend/Date.now).

### Get the number of seconds since the ECMAScript Epoch

```javascript
var seconds = Math.floor(Date.now() / 1000);
```

In this case it's important to return only an integer (so a simple division won't do), and also to
only return actually elapsed seconds (that's why this code uses [`Math.floor()`](/en/webfrontend/Math.floor)
and not [`Math.round()`](/en/webfrontend/Math.round)).
