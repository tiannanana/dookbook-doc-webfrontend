TOPICS: Date.toISOString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toISOString()`

The **`toISOString()`** method returns a string in simplified extended ISO format (ISO 8601),
which is always 24 or 27 characters long (**`YYYY-MM-DDTHH:mm:ss.sssZ`** or
**`±YYYYYY-MM-DDTHH:mm:ss.sssZ`**, respectively). The timezone is always zero UTC offset,
as denoted by the suffix "**`Z`**".

## Syntax

```javascript
dateObj.toISOString()
```

**parameter**: No parameters

**Return value**: String

## Examples

### Using `toISOString()`

```javascript
var today = new Date('05 October 2011 14:48 UTC');

console.log(today.toISOString()); // Returns 2011-10-05T14:48:00.000Z
```

The above example uses parsing of a non–standard string value that may not be correctly
parsed in non–Mozilla browsers.

## Polyfill

This method was standardized in ECMA-262 5th edition. Engines which have not been updated to
support this method can work around the absence of this method using the following shim:

```javascript
if (!Date.prototype.toISOString) {
  (function() {

    function pad(number) {
      if (number < 10) {
        return '0' + number;
      }
      return number;
    }

    Date.prototype.toISOString = function() {
      return this.getUTCFullYear() +
        '-' + pad(this.getUTCMonth() + 1) +
        '-' + pad(this.getUTCDate()) +
        'T' + pad(this.getUTCHours()) +
        ':' + pad(this.getUTCMinutes()) +
        ':' + pad(this.getUTCSeconds()) +
        '.' + (this.getUTCMilliseconds() / 1000).toFixed(3).slice(2, 5) +
        'Z';
    };

  }());
}
```
