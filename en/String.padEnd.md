TOPICS: String.padEnd
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.padEnd()`

The **`padEnd()`** method pads the current string with a given string (repeated, if needed) so that
the resulting string reaches a given length. The padding is applied from the end of the current string.

## Syntax

```javascript
str.padEnd(targetLength [, padString])
```

| parameter | Description |
| :-- | :-- |
| `targetLength` | The length of the resulting string once the current string has been padded. If the value is lower than the current string's length, the current string will be returned as is. |
| `padString` Optional | The string to pad the current string with. If this string is too long to stay within the target length, it will be truncated: for left-to-right languages the left-most part and for right-to-left languages the right-most will be applied. The default value for this parameter is `" "` (U+0020).|

**Return value**: A `String` of the specified length with the pad string applied at the end of the
current string.

## Examples

```javascript
'abc'.padEnd(10);          // "abc       "
'abc'.padEnd(10, "foo");   // "abcfoofoof"
'abc'.padEnd(6, "123456"); // "abc123"
'abc'.padEnd(1);           // "abc"
```

## Polyfill

Running the following code before any other code will create `String.prototype.padEnd()` if it's not
natively available.

```javascript
// https://github.com/uxitten/polyfill/blob/master/string.polyfill.js
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd
if (!String.prototype.padEnd) {
    String.prototype.padEnd = function padEnd(targetLength,padString) {
        targetLength = targetLength>>0; //floor if number or convert non-number to 0;
        padString = String((typeof padString !== 'undefined' ? padString : ' '));
        if (this.length > targetLength) {
            return String(this);
        }
        else {
            targetLength = targetLength-this.length;
            if (targetLength > padString.length) {
                padString += padString.repeat(targetLength/padString.length); //append to original to ensure we are longer than needed
            }
            return String(this) + padString.slice(0,targetLength);
        }
    };
}
```
