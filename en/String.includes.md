TOPICS: String.includes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.includes()`

The **`includes()`** method determines whether one string may be found within another string,
returning true or false as appropriate.

## Syntax

```javascript
str.includes(searchString[, position])
```

| parameter | Description |
| :-- | :-- |
| `searchString` | A string to be searched for within `str`. |
| `position` Optional | The position within the string at which to begin searching for `searchString`. (Defaults to `0`.) |

**Return value**: `true` if the search string is found anywhere within the given string; otherwise,
`false` if not.

## Description

This method lets you determine whether or not a string includes another string.

### Case-sensitivity

The `includes()` method is case sensitive. For example, the following expression returns `false`:

```javascript
'Blue Whale'.includes('blue')  // returns false
```

## Examples

### Using `includes()`

```javascript
const str = 'To be, or not to be, that is the question.'

console.log(str.includes('To be'))        // true
console.log(str.includes('question'))     // true
console.log(str.includes('nonexistent'))  // false
console.log(str.includes('To be', 1))     // false
console.log(str.includes('TO BE'))        // false
console.log(str.includes(''))             // true
```

## Polyfill

This method has been added to the ECMAScript 2015 specification and may not be available in all
JavaScript implementations yet.

However, you can easily polyfill this method:

```javascript
if (!String.prototype.includes) {
  String.prototype.includes = function(search, start) {
    'use strict';

    if (search instanceof RegExp) {
      throw TypeError('first argument must not be a RegExp');
    }
    if (start === undefined) { start = 0; }
    return this.indexOf(search, start) !== -1;
  };
}
```
