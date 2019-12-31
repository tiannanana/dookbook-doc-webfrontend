TOPICS: String.endsWith
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.endsWith()`

The **`endsWith()`** method determines whether a string ends with the characters of a specified
string, returning `true` or `false` as appropriate.

## Syntax

```javascript
str.endsWith(searchString[, length])
```

| parameter | Description |
| :-- | :-- |
| `searchString` | The characters to be searched for at the end of `str`. |
| `length` Optional | If provided, it is used as the length of `str`. Defaults to `str.length`. |

**Return value**: `true` if the given characters are found at the end of the string; otherwise, `false`.

## Description

This method lets you determine whether or not a string ends with another string. This method is case-sensitive.

## Examples

### Using `endsWith()`

```javascript
let str = 'To be, or not to be, that is the question.'

console.log(str.endsWith('question.'))  // true
console.log(str.endsWith('to be'))      // false
console.log(str.endsWith('to be', 19))  // true
```

## Polyfill

This method has been added to the ECMAScript 6 specification and may not be available in all
JavaScript implementations yet. However, you can polyfill `String.prototype.endsWith()`
with the following snippet:

```javascript
if (!String.prototype.endsWith) {
  String.prototype.endsWith = function(search, this_len) {
    if (this_len === undefined || this_len > this.length) {
      this_len = this.length;
    }
    return this.substring(this_len - search.length, this_len) === search;
  };
}
```
