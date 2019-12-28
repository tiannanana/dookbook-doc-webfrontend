TOPICS: Date.toLocaleDateString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toLocaleDateString()`

The **`toLocaleDateString()`** method returns a string with a language sensitive representation of
the date portion of this date. The new `locales` and `options` arguments let applications specify
the language whose formatting conventions should be used and allow to customize the behavior of the
function. In older implementations, which ignore the `locales` and `options` arguments, the locale
used and the form of the string returned are entirely implementation dependent.

## Syntax

```javascript
dateObj.toLocaleDateString([locales [, options]])
```

| parameter | Description |
| :-- | :-- |
| `locales` | A string with a BCP 47 language tag, or an array of such strings. To use the browser's default locale, omit this argument or pass `undefined`. Unicode extension are supported (for example "`en-US-u-ca-buddhist`"). For the general form and interpretation of the locales argument, see the Intl page. The following Unicode extension keys are allowed:<br><br>**`nu`**<br>Numbering system. Possible values include: "`arab`", "`arabext`", "`bali`", "`beng`", "`deva`", "`fullwide`", "`gujr`", "`guru`", "`hanidec`", "`khmr`", "`knda`", "`laoo`", "`latn`", "`limb`", "`mlym`", "`mong`", "`mymr`", "`orya`", "`tamldec`", "`telu`", "`thai`", "`tibt`".<br><br>**`ca`**<br>Calendar. Possible values include: "`buddhist`", "`chinese`", "`coptic`", "`ethiopia`", "`ethiopic`", "`gregory`", "`hebrew`", "`indian`", "`islamic`", "`iso8601`", "`japanese`", "`persian`", "`roc`".<br><br>**`hc`**<br>Hour cycle. Possible values include: "`h11`", "`h12`", "`h23`", "`h24`". |
| `options` Optional | An object with some or all of the following properties: <br><br>**`localeMatcher`**<br>The locale matching algorithm to use. Possible values are "`lookup`" and "`best fit`"; the default is "`best fit`". For information about this option, see the Intl page.<br><br>**`timeZone`**<br>The time zone to use. The only value implementations must recognize is "`UTC`"; the default is the runtime's default time zone. Implementations may also recognize the time zone names of the IANA time zone database, such as "`Asia/Shanghai`", "`Asia/Kolkata`", "`America/New_York`".<br><br>**`hour12`**<br>Whether to use 12-hour time (as opposed to 24-hour time). Possible values are `true` and `false`; the default is locale dependent. This option overrides the `hc` language tag and/or the `hourCycle` option in case both are present.<br><br>**`hourCycle`**<br>The hour cycle to use. Possible values are "`h11`", "`h12`", "`h23`", or "`h24`". This option overrides the `hc` language tag, if both are present, and the `hour12` option takes precedence in case both options have been specified.<br><br>**`formatMatcher`**<br>The format matching algorithm to use. Possible values are "`basic`" and "`best fit`"; the default is "`best fit`". See the following paragraphs for information about the use of this property.<br>The following properties describe the date-time components to use in formatted output, and their desired representations. Implementations are required to support at least the following subsets:<br>1、`weekday`, `year`, `month`, `day`, `hour`, `minute`, `second`<br>2、`weekday`, `year`, `month`, `day`<br>3、`year`, `month`, `day`<br>4、`year`, `month`<br>5、`month`, `day`<br>6、`hour`, `minute`, `second`<br>7、`hour`, `minute`<br><br>Implementations may support other subsets, and requests will be negotiated against all available subset-representation combinations to find the best match. Two algorithms are available for this negotiation and selected by the `formatMatcher` property: A fully specified "`basic`" algorithm and an implementation-dependent "`best fit"` algorithm.|
| `weekday` | The representation of the weekday. Possible values are: <br>"`long`"(e.g., `Thursday`)<br>"`short`"(e.g., `Thu`)<br>"`narrow`"(e.g., `T`). Two weekdays may have the same narrow style for some locales (e.g. `Tuesday`'s narrow style is also `T`).|
| `era` | The representation of the era. Possible values are: <br>"`long`" (e.g., `Anno Domini`)<br>"`short`"(e.g., `AD`)<br>"`narrow`" (e.g., `A`) |
| `year` | The representation of the year. Possible values are: <br>"`numeric`"(e.g., `2012`)<br>"`2-digit`"(e.g., `12`) |
| `month` | The representation of the month. Possible values are:<br>"`numeric`" (e.g., `2`)<br>"`2-digit`"(e.g., `02`)<br>"`long`"(e.g., `March`)<br>"`short`"(e.g., `Mar`)<br>"`narrow`"（(e.g., `M`). Two months may have the same narrow style for some locales (e.g. `May`'s narrow style is also `M`). |
| `day` | The representation of the day. Possible values are: <br>"`numeric`"（(e.g., `1`)<br>"`2-digit`"(e.g., `01`) |
| `hour` | The representation of the hour. Possible values are "`numeric`"，"`2-digit`" |
| `minute` | The representation of the minute. Possible values are "`numeric`"，"`2-digit`" |
| `second` | The representation of the second. Possible values are "`numeric`"，"`2-digit`"。 |
| `timeZoneName` | The representation of the time zone name. Possible values are: <br>"`long`" (e.g., `British Summer Time`)<br>"`short`"（(e.g., `GMT+1`) |

The default value for each date-time component property is [`undefined`](/en/webfrontend/undefined),
but if the `weekday`, `year`, `month`, `day` properties are all
[`undefined`](/en/webfrontend/undefined), then `year`, `month`, and `day` are assumed to be `"numeric"`.

**Return value**: String

## Examples

### Using `toLocaleDateString()`

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
function toLocaleDateStringSupportsLocales() {
  try {
    new Date().toLocaleDateString('i');
  } catch (e) {
    return e.name === 'RangeError';
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

// US English uses month-day-year order
console.log(date.toLocaleDateString('en-US'));
// → "12/19/2012"

// British English uses day-month-year order
console.log(date.toLocaleDateString('en-GB'));
// → "20/12/2012"

// Korean uses year-month-day order
console.log(date.toLocaleDateString('ko-KR'));
// → "2012. 12. 20."

// Event for Persian, It's hard to manually convert date to Solar Hijri
console.log(date.toLocaleDateString('fa-IR'));
// → "۱۳۹۱/۹/۳۰"

// Arabic in most Arabic speaking countries uses real Arabic digits
console.log(date.toLocaleDateString('ar-EG'));
// → "٢٠‏/١٢‏/٢٠١٢"

// for Japanese, applications may want to use the Japanese calendar,
// where 2012 was the year 24 of the Heisei era
console.log(date.toLocaleDateString('ja-JP-u-ca-japanese'));
// → "24/12/20"

// when requesting a language that may not be supported, such as
// Balinese, include a fallback language, in this case Indonesian
console.log(date.toLocaleDateString(['ban', 'id']));
// → "20/12/2012"
```

### Using options

The results provided by `toLocaleDateString()` can be customized using the `options` argument:

```javascript
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

// request a weekday along with a long date
var options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
console.log(date.toLocaleDateString('de-DE', options));
// → "Donnerstag, 20. Dezember 2012"

// an application may want to use UTC and make that visible
options.timeZone = 'UTC';
options.timeZoneName = 'short';
console.log(date.toLocaleDateString('en-US', options));
// → "Thursday, December 20, 2012, GMT"
```
