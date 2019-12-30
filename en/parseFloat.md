TOPICS: parseFloat
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `parseFloat()`

The **`parseFloat()`** function parses an argument (converting it to a string first if needed) and
returns a floating point number.

## Syntax

```javascript
parseFloat(string)
```

| parameter | Description |
| :-- | :-- |
| `string` | The value you want to parse |

**Return value**: A floating point number parsed from the given argument. If a number cannot be
parsed from the argument, instead returns `NaN`.

## Description

`parseFloat` is a top-level function and not a method of any object.

- If `parseFloat` encounters a character other than a plus sign (`+`), minus sign (`-` U+002D HYPHEN-MINUS),
numeral (`0`–`9`), decimal point (`.`), or exponent (`e` or `E`), it returns the value up to
that character, ignoring the invalid character and characters following it.
- A second decimal point also stops parsing (characters up to that point will still be parsed).
- Leading and trailing spaces in the argument are ignored.
- If the argument’s first character can’t be converted to a number (it’s not any of the above
characters), `parseFloat` returns `NaN`.
- `parseFloat` can also parse and return `Infinity`.
- `parseFloat` converts [`BigInt`](/en/webfrontend/BigInt) syntax to [`Numbers`](/en/webfrontend/Numbers),
losing precision. This happens because the trailing n character is discarded.

Consider [`Number(value)`](/en/webfrontend/Numbers) for stricter parsing, which converts to `NaN`
for arguments with invalid characters anywhere.

`parseFloat` will parse non-string objects if they have a [`toString`](/en/webfrontend/Numbers.toString)
or [`valueOf`](/en/webfrontend/Numbers.valueOf) method. The returned value is the same as if
`parseFloat` had been called on the result of those methods.

## Examples

### `parseFloat` returning a number

The following examples all return `3.14`:

```javascript
parseFloat(3.14);
parseFloat('3.14');
parseFloat('  3.14  ');
parseFloat('314e-2');
parseFloat('0.0314E+2');
parseFloat('3.14some non-digit characters');
parseFloat({ toString: function() { return "3.14" } });
```

### `parseFloat` returning `NaN`

The following example returns `NaN`:

```javascript
parseFloat('FF2');
```

### `parseFloat` and `BigInt`

The following examples both return `900719925474099300`, losing precision as the integer is too
large to be represented as a float:

```javascript
parseFloat(900719925474099267n);
parseFloat('900719925474099267n');
```
