TOPICS: String
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript `String` Object

The **`String`** *global object* is a constructor for strings or a sequence of characters.

## Syntax

String literals take the forms:

```javascript
'string text'
"string text"
"中文 español Deutsch English देवनागरी العربية português বাংলা русский 日本語 norsk bokmål ਪੰਜਾਬੀ 한국어 தமிழ் עברית"
```

Strings can also be created using the String *global object* directly:

```javascript
String(thing)
```

## Parameters

| parameter | Description |
| :-- | :-- |
| `thing` | Anything to be converted to a string. |

## Template literals

Starting with ECMAScript 2015, string literals can also be so-called Template literals:

```javascript
`hello world`
`hello!
 world!`
`hello ${who}`
tag `<a>${who}</a>`
```

## Escape notation

Besides regular, printable characters, special characters can be encoded using escape notation:

| Code | Output |
| :--- | :----- |
| `\XXX` (where XXX is 1–3 octal digits; range of `0`–`377`) | ISO-8859-1 character / Unicode code point between `U+0000` and `U+00FF` |
| `\'` | single quote
| `\"` | double quote
| `\\` | backslash
| `\n` | new line
| `\r` | carriage return
| `\v` | vertical tab
| `\t` | tab
| `\b` | backspace
| `\f` | form feed
| `\uXXXX` (where `XXXX` is 4 hex digits; range of `0x0000`–`0xFFFF`) | UTF-16 code unit / Unicode code point between `U+0000` and U`+FFFF` |
| `\u{X}` ... `\u{XXXXXX}` (where `X…XXXXXX` is 1–6 hex digits; range of `0x0`–`0x10FFFF`) | UTF-32 code unit / Unicode code point between `U+0000` and `U+10FFFF` |
| `\xXX` (where `XX` is 2 hex digits; range of `0x00`–`0xFF`) | ISO-8859-1 character / Unicode code point between `U+0000` and `U+00FF` |

!!! warn "Note"
    Unlike some programming languages, JavaScript makes no distinction between single-quoted
    strings and double-quoted strings. Therefore, the escape sequences above work in strings
    created with either single or double quotes.

## Long literal strings

Sometimes, your code will include strings which are very long. Rather than having lines that go on
endlessly, or wrap at the whim of your editor, you may wish to specifically break the string into
multiple lines in the source code without affecting the actual string contents. There are
two ways you can do this.

Method 1

You can use the + operator to append multiple strings together, like this:

```javascript
let longString = "This is a very long string which needs " +
                 "to wrap across multiple lines because " +
                 "otherwise my code is unreadable."
```

Method 2

You can use the backslash character (`\`) at the end of each line to indicate that the string will
continue on the next line. Make sure there is no space or any other character after the backslash
(except for a line break), or as an indent; otherwise it will not work.

That form looks like this:

```javascript
let longString = "This is a very long string which needs \
to wrap across multiple lines because \
otherwise my code is unreadable."
```

Both of the above methods result in identical strings.

## Description

Strings are useful for holding data that can be represented in text form. Some of the most-used
operations on strings are to check their `length`, to build and concatenate them using the `+`
and `+=` string operators, checking for the existence or location of substrings with the [`indexOf()`](/en/webfrontend/String.indexOf)
method, or extracting substrings with the `substring()` method.

### Character access

There are two ways to access an individual character in a string. The first is the
[`charAt()`](/en/webfrontend/String.charAt)  method:

```javascript
return 'cat'.charAt(1) // returns "a"
```

The other way (introduced in ECMAScript 5) is to treat the string as an array-like object, where
individual characters correspond to a numerical index:

```javascript
return 'cat'[1] // returns "a"
```

When using bracket notation for character access, attempting to delete or assign a value to
these properties will not succeed. The properties involved are neither writable nor configurable.
(See [`Object.defineProperty()`](/en/webfrontend/Object.defineProperty) for more information.)

### Comparing strings

In C, the `strcmp()` function is used for comparing strings. In JavaScript, you just use the
less-than and greater-than operators:

```javascript
let a = 'a'
let b = 'b'
if (a < b) { // true
  console.log(a + ' is less than ' + b)
} else if (a > b) {
  console.log(a + ' is greater than ' + b)
} else {
  console.log(a + ' and ' + b + ' are equal.')
}
```

A similar result can be achieved using the [`localeCompare()`](/en/webfrontend/String.localeCompare)
method inherited by String instances.

!!! warn "Note"
    `a == b` compares the strings in `a` and `b` for being equal in the usual case-sensitive way.
    If you wish to compare without regard to upper or lower case characters, use a
    function similar to this:

```javascript
function isEqual(str1, str2)
{
    return str1.toUpperCase() === str2.toUpperCase()
} // isEqual
```

Upper case is used instead of lower case in this function, due to problems with certain UTF-8
character conversions.

### Distinction between string primitives and `String` objects

Note that JavaScript distinguishes between `String` objects and primitive string values.
(The same is true of [`Boolean`](/en/webfrontend/Boolean) and [`Numbers`](/en/webfrontend/Numbers).)

String literals (denoted by double or single quotes) and strings returned from `String` calls in a
non-constructor context (that is, called without using the `new` keyword) are primitive strings.
JavaScript automatically converts primitives to `String` objects, so that it's possible to use
`String` object methods for primitive strings. In contexts where a method is to be invoked on a
primitive string or a property lookup occurs, JavaScript will automatically wrap the string
primitive and call the method or perform the property lookup.

```javascript
let s_prim = 'foo'
let s_obj = new String(s_prim)

console.log(typeof s_prim) // Logs "string"
console.log(typeof s_obj)  // Logs "object"
```

String primitives and `String` objects also give different results when using [`eval()`](/en/webfrontend/eval).
Primitives passed to eval are treated as source code; `String` objects are treated as all other
objects are, by returning the object. For example:

```javascript
let s1 = '2 + 2'              // creates a string primitive
let s2 = new String('2 + 2')  // creates a String object
console.log(eval(s1))         // returns the number 4
console.log(eval(s2))         // returns the string "2 + 2"
```

For these reasons, the code may break when it encounters `String` objects when it expects a
primitive string instead, although generally, authors need not worry about the distinction.

A `String` object can always be converted to its primitive counterpart with the
[`valueOf()`](/en/webfrontend/String.valueOf) method.

```javascript
console.log(eval(s2.valueOf()))  // returns the number 4
```

## Properties

### `String.prototype`

The **`String.prototype`** property represents the `String` prototype object.

All `String` instances inherit from `String.prototype`. Changes to the `String` prototype object are
propagated to all `String` instances.

### `String.length`

The **`length`** property of a `String` object contains the `length` of the string, in UTF-16
code units. `length` is a read-only data property of string instances.

This property returns the number of code units in the string. UTF-16, the string
format used by JavaScript, uses a single 16-bit code unit to represent the most common characters,
but needs to use two code units for less commonly-used characters, so it's possible for the value
returned by `length` to not match the actual number of characters in the string.

ECMAScript 2016 (ed. 7) established a maximum `length` of 2^53 - 1 elements. Previously, no maximum
`length` was specified. In Firefox, strings have a maximum length of `2**30 - 2` (~1GB).
In versions prior to Firefox 65, the maximum length was `2**28 - 1` (~256MB).

For an empty string, `length` is `0`.

The static property `String.length` is unrelated to the length of strings, it's the arity of the
`String` function (loosely, the number of formal parameters it has), which is 1.

## Examples

### String conversion

It's possible to use String as a more reliable [`toString()`](/en/webfrontend/String.toString)
alternative, as it works when used on [`null`](/en/webfrontend/null), [`undefined`](/en/webfrontend/undefined),
and on [`symbols`](/en/webfrontend/symbols). For example:

```javascript
// equivalent to o = new Boolean(false)
let o = new Object(Boolean())
```

### Basic usage

```javascript
let x = 'Mozilla';
let empty = '';

console.log(x + ' is ' + x.length + ' code units long');
/* "Mozilla is 7 code units long" */

console.log('The empty string has a length of ' + empty.length);
// expected output: "The empty string has a length of 0"
```

### Assigning to length

```javascript
let myString = "bluebells";

// Attempting to assign a value to a string's .length property has no observable effect.
myString.length = 4;
console.log(myString);
// expected output: "bluebells"
console.log(myString.length);
// expected output: 9
```
