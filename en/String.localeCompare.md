TOPICS: String.localeCompare
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.localeCompare()`

The **`localeCompare()`** method returns a number indicating whether a reference string comes
before or after or is the same as the given string in sort order.

The new `locales` and `options` arguments let applications specify the language whose sort order
should be used and customize the behavior of the function. In older implementations, which ignore
the `locales` and `options` arguments, the locale and sort order used are entirely implementation dependent.

## Syntax

```javascript
referenceStr.localeCompare(compareString[, locales[, options]])
```

| parameter | Description |
| :-- | :-- |
| `compareString` | The string against which the referring string is compared |
| `locales` | Optional. A string with a BCP 47 language tag, or an array of such strings. For the general form and interpretation of the locales argument, The following Unicode extension keys are allowed:<br><br>**`co`**<br>Variant collations for certain locales. Possible values include: "`big5han`", "`dict`", "`direct`", "`ducet`", "`gb2312`", "`phonebk`", "`phonetic`", "`pinyin`", "`reformed`", "`searchjl`", "`stroke`", "`trad`", "`unihan`". The "`standard`" and "`search`" values<br><br>are ignored; they are replaced by the `options` property usage (see below).<br><br>**`kn`**<br>Whether numeric collation should be used, such that `"1" < "2" < "10"`. Possible values are "`true`" and "`false`". This option can be set through an `options` property or through a Unicode extension key; if both are provided, the `options` property takes precedence.<br><br>**`kf`**<br>Whether upper case or lower case should sort first. Possible values are "`upper`", "`lower`", or "`false`" (use the locale's default). This option can be set through an `options` property or through a Unicode extension key; if both are provided, the `options` property takes precedence. |
| `options` | Optional. An object with some or all of the following properties:<br><br>**`localeMatcher`**<br>The locale matching algorithm to use. Possible values are "`lookup`" and "`best fit`"; the default is "`best fit`". For information about this option<br><br>**`usage`**<br>Whether the comparison is for sorting or for searching for matching strings. Possible values are "`sort`" and "`search`"; the default is "`sort`".<br><br>**`sensitivity`**<br>Which differences in the strings should lead to non-zero result values. Possible values are:<br>1. "`base`": Only strings that differ in base letters compare as unequal. Examples: `a ≠ b, a = á, a = A`.<br>2. "`accent`": Only strings that differ in base letters or accents and other diacritic marks compare as unequal. Examples: `a ≠ b, a ≠ á, a` = A.<br>3."`case`": Only strings that differ in base letters or case compare as unequal. Examples: `a ≠ b, a = á, a ≠ A`.<br>4. "`variant`": Strings that differ in base letters, accents and other diacritic marks, or case compare as unequal. Other differences may also be taken into consideration. Examples: `a ≠ b, a ≠ á, a ≠ A`.<br><br>The default is "`variant`" for usage "`sort`"; it's locale dependent for usage "`search`". |
| `ignorePunctuation` | Whether punctuation should be ignored. Possible values are `true` and `false`; the default is `false`. |
| `numeric` | Whether numeric collation should be used, such that `"1" < "2" < "10"`. Possible values are `true` and `false`; the default is `false`. This option can be set through an `options` property or through a Unicode extension key; if both are provided, the `options` property takes precedence. Implementations are not required to support this property.|
| `caseFirst` | Whether upper case or lower case should sort first. Possible values are "`upper`", "`lower`", or "`false`" (use the locale's default); the default is "`false`". This option can be set through an `options` property or through a Unicode extension key; if both are provided, the `options` property takes precedence. Implementations are not required to support this property. |

**Return value**: A **negative** number if the reference string occurs before the compare string;
**positive** if the reference string occurs after the compare string; **`0`** if they are equivalent.

Description

## Description

Returns an integer indicating whether the **referenceStr** comes before, after or is equivalent
to the **compareStr**.

- Negative when the **referenceStr** occurs before **compareStr**
- Positive when the **referenceStr** occurs after **compareStr**
- Returns 0 if they are equivalent

**DO NOT rely on exact return values of `-1` or `1`**. Negative and positive integer results vary
between browsers (as well as between browser versions) because the W3C specification only mandates
negative and positive values. Some browsers may return `-2` or `2` or even some other negative or
positive value.

## Examples

### Using `localeCompare()`

```javascript
// The letter "a" is before "c" yielding a negative value
'a'.localeCompare('c'); // -2 or -1 (or some other negative value)

// Alphabetically the word "check" comes after "against" yielding a positive value
'check'.localeCompare('against'); // 2 or 1 (or some other positive value)

// "a" and "a" are equivalent yielding a neutral value of zero
'a'.localeCompare('a'); // 0
```

### Sort an array

`localeCompare` enables a case-insensitive sort of an array.

```javascript
var items = ['réservé', 'Premier', 'Cliché', 'communiqué', 'café', 'Adieu'];
items.sort((a, b) => a.localeCompare(b, 'fr', {ignorePunctuation: true})); // ['Adieu', 'café', 'Cliché', 'communiqué', 'Premier', 'réservé']
```

### Check browser support for extended arguments

The `locales` and `options` arguments are not supported in all browsers yet. To check whether an
implementation supports them, use the "i" argument (a requirement that illegal language tags are
rejected) and look for a `RangeError` exception:

```javascript
function localeCompareSupportsLocales() {
  try {
    'foo'.localeCompare('bar', 'i');
  } catch (e) {
    return e.name === 'RangeError';
  }
  return false;
}
```

### Using `locales`

The results provided by `localeCompare()` vary between languages. In order to get the sort order of
the language used in the user interface of your application, make sure to specify that language
(and possibly some fallback languages) using the `locales` argument:

```javascript
console.log('ä'.localeCompare('z', 'de')); // a negative value: in German, ä sorts before z
console.log('ä'.localeCompare('z', 'sv')); // a positive value: in Swedish, ä sorts after z
```

### Using `options`

The results provided by `localeCompare()` can be customized using the `options` argument:

```javascript
// in German, ä has a as the base letter
console.log('ä'.localeCompare('a', 'de', { sensitivity: 'base' })); // 0

// in Swedish, ä and a are separate base letters
console.log('ä'.localeCompare('a', 'sv', { sensitivity: 'base' })); // a positive value
```

### Numeric sorting

```javascript
// by default, "2" > "10"
console.log("2".localeCompare("10")); // 1

// numeric using options:
console.log("2".localeCompare("10", undefined, {numeric: true})); // -1

// numeric using locales tag:
console.log("2".localeCompare("10", "en-u-kn-true")); // -1
```

## Performance

When comparing large numbers of strings, such as in sorting large arrays, it is better to create an
`Intl.Collator` object and use the function provided by its `compare` property.
