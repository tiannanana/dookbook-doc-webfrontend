TOPICS: Date.toLocaleDateString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toLocaleDateString()`

The **`toLocaleString()`** method returns a string with a language sensitive representation of this
date. The new `locales` and `options` arguments let applications specify the language whose
formatting conventions should be used and customize the behavior of the function. In older
implementations, which ignore the `locales` and `options` arguments, the locale used
and the form of the string returned are entirely implementation dependent.

## Syntax

```javascript
dateObj.toLocaleDateString([locales [, options]])
```

**parameter**: No parameters

**Return value**: String

## Examples

### Using `toLocaleString()`

In basic use without specifying a locale, a formatted string in the default locale and with
default options is returned.

```javascript
var date = new Date(Date.UTC(2012, 11, 12, 3, 0, 0));

// toLocaleDateString() without arguments depends on the implementation,
// the default locale, and the default time zone
console.log(date.toLocaleDateString());
// → "12/11/2012" if run in en-US locale with time zone America/Los_Angeles
```

### Checking for support for `locales` and `options` arguments

The `locales` and `options` arguments are not supported in all browsers yet. To check whether an
implementation supports them already, you can use the requirement that illegal language tags are
rejected with a `RangeError` exception:

```javascript
function toLocaleStringSupportsLocales() {
  try {
    new Date().toLocaleString('i');
  } catch (e) {
    return e instanceof RangeError;
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

// US English uses month-day-year order and 12-hour time with AM/PM
console.log(date.toLocaleString('en-US'));
// → "12/19/2012, 7:00:00 PM"

// British English uses day-month-year order and 24-hour time without AM/PM
console.log(date.toLocaleString('en-GB'));
// → "20/12/2012 03:00:00"

// Korean uses year-month-day order and 12-hour time with AM/PM
console.log(date.toLocaleString('ko-KR'));
// → "2012. 12. 20. 오후 12:00:00"

// Arabic in most Arabic speaking countries uses real Arabic digits
console.log(date.toLocaleString('ar-EG'));
// → "٢٠‏/١٢‏/٢٠١٢ ٥:٠٠:٠٠ ص"

// for Japanese, applications may want to use the Japanese calendar,
// where 2012 was the year 24 of the Heisei era
console.log(date.toLocaleString('ja-JP-u-ca-japanese'));
// → "24/12/20 12:00:00"

// when requesting a language that may not be supported, such as
// Balinese, include a fallback language, in this case Indonesian
console.log(date.toLocaleString(['ban', 'id']));
// → "20/12/2012 11.00.00"
```

### Using `options`

The results provided by `toLocaleDateString()` can be customized using the `options` argument:

```javascript
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

// request a weekday along with a long date
var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
console.log(date.toLocaleString('de-DE', options));
// → "Donnerstag, 20. Dezember 2012"

// an application may want to use UTC and make that visible
options.timeZone = 'UTC';
options.timeZoneName = 'short';
console.log(date.toLocaleString('en-US', options));
// → "Thursday, December 20, 2012, GMT"

// sometimes even the US needs 24-hour time
console.log(date.toLocaleString('en-US', { hour12: false }));
// → "12/19/2012, 19:00:00"
```
