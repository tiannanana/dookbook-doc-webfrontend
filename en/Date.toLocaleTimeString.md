TOPICS: Date.toLocaleTimeString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toLocaleTimeString()`

The **`toLocaleTimeString()`** method returns a string with a language sensitive representation of
the time portion of this date. The new `locales` and `options` arguments let applications specify
the language whose formatting conventions should be used and customize the behavior of the function.
In older implementations, which ignore the `locales` and `options` arguments, the locale used and the
form of the string returned are entirely implementation dependent.

## Syntax

```javascript
dateObj.toLocaleTimeString([locales[, options]])
```

**parameter**: No parameters

**Return value**: String

## Examples

### Using `toLocaleString()`

In basic use without specifying a locale, a formatted string in the default locale and with default
options is returned.

```javascript
var date = new Date(Date.UTC(2012, 11, 12, 3, 0, 0));

// toLocaleTimeString() without arguments depends on the implementation,
// the default locale, and the default time zone
console.log(date.toLocaleTimeString());
// → "7:00:00 PM" if run in en-US locale with time zone America/Los_Angeles
```

### Checking for support for `locales` and `options` arguments

The `locales` and `options` arguments are not supported in all browsers yet. To check whether an
implementation supports them already, you can use the requirement that illegal language tags are
rejected with a `RangeError` exception:

```javascript
function toLocaleTimeStringSupportsLocales() {
  try {
    new Date().toLocaleTimeString('i');
  } catch (e) {
    return e​.name === 'RangeError';
  }
  return false;
}
```

### Using `locales`

This example shows some of the variations in localized date formats. In order to get the
format of the language used in the user interface of your application, make sure to specify that
language (and possibly some fallback languages) using the `locales` argument:

```javascript
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

// formats below assume the local time zone of the locale;
// America/Los_Angeles for the US

// US English uses 12-hour time with AM/PM
console.log(date.toLocaleTimeString('en-US'));
// → "7:00:00 PM"

// British English uses 24-hour time without AM/PM
console.log(date.toLocaleTimeString('en-GB'));
// → "03:00:00"

// Korean uses 12-hour time with AM/PM
console.log(date.toLocaleTimeString('ko-KR'));
// → "오후 12:00:00"

// Arabic in most Arabic speaking countries uses real Arabic digits
console.log(date.toLocaleTimeString('ar-EG'));
// → "٧:٠٠:٠٠ م"

// when requesting a language that may not be supported, such as
// Balinese, include a fallback language, in this case Indonesian
console.log(date.toLocaleTimeString(['ban', 'id']));
// → "11.00.00"
```

### Using `options`

The results provided by `toLocaleTimeString()` can be customized using the `options` argument:

```javascript
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

// an application may want to use UTC and make that visible
var options = { timeZone: 'UTC', timeZoneName: 'short' };
console.log(date.toLocaleTimeString('en-US', options));
// → "3:00:00 AM GMT"

// sometimes even the US needs 24-hour time
console.log(date.toLocaleTimeString('en-US', { hour12: false }));
// → "19:00:00"

// show only hours and minutes, use options with the default locale - use an empty array
console.log(date.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }));
// → "20:01"
```
