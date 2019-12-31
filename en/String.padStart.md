TOPICS: String.padStart
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.padStart()`

The **`padStart()`** method pads the current string with another string (multiple times, if needed)
until the resulting string reaches the given length. The padding is applied from the start of the
current string.

## Syntax

```javascript
str.padStart(targetLength [, padString])
```

| parameter | Description |
| :-- | :-- |
| `targetLength` | The length of the resulting string once the current string has been padded. If the value is less than the current string's length, the current string is returned as is. |
| `padString` Optional | The string to pad the current string with. If this padding string is too long to stay within the *`targetLength`*, it will be truncated from the end. The default value is `" "` (U+0020 'SPACE').

**Return value**: A `String` of the specified length with the pad string applied from the start.

## Examples

```javascript
'abc'.padStart(10);         // "       abc"
'abc'.padStart(10, "foo");  // "foofoofabc"
'abc'.padStart(6,"123465"); // "123abc"
'abc'.padStart(8, "0");     // "00000abc"
'abc'.padStart(1);          // "abc"
```

```javascript
// Javascript version of: (unsigned)
//  printf "%0*d" width num
function leftFillNum(num, targetLength) {
    return num.toString().padStart(targetLength, 0);
}

const num = 123;
console.log(leftFillNum(num, 5));
// expected output: "00123"
```

## Polyfill

Running the following code before any other code will create `String.prototype.padStart()` if it's
not natively available.

```javascript
// https://github.com/uxitten/polyfill/blob/master/string.polyfill.js
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart
if (!String.prototype.padStart) {
    String.prototype.padStart = function padStart(targetLength, padString) {
        targetLength = targetLength >> 0; //truncate if number, or convert non-number to 0;
        padString = String(padString !== undefined ? padString : ' ');
        if (this.length >= targetLength) {
            return String(this);
        } else {
            targetLength = targetLength - this.length;
            if (targetLength > padString.length) {
                padString += padString.repeat(targetLength / padString.length); //append to original to ensure we are longer than needed
            }
            return padString.slice(0, targetLength) + String(this);
        }
    };
}
```
