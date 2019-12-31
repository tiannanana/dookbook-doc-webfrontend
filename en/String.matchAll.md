TOPICS: String.matchAll
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.matchAll()`

The **`matchAll()`** method returns an iterator of all results matching a *string* against a
*regular expression*, including capturing groups.

## Syntax

```javascript
str.matchAll(regexp)
```

| parameter | Description |
| :-- | :-- |
| `regexp` | A regular expression object. If a non-RegExp object `obj` is passed, it is implicitly converted to a `RegExp` by using `new RegExp(obj)`. |

**Return value**: An iterator (which is not a restartable iterable).

## Examples

### `Regexp.exec()` and `matchAll()`

Prior to the addition of matchAll to JavaScript, it was possible to use calls to `regexp.exec` (and
regexes with the `/g` flag) in a loop to obtain all the matches:

```javascript
const regexp = RegExp('foo[a-z]*','g');
const str = 'table football, foosball';
let match;

while ((match = regexp.exec(str)) !== null) {
  console.log(`Found ${match[0]} start=${match.index} end=${regexp.lastIndex}.`);
  // expected output: "Found football start=6 end=14."
  // expected output: "Found foosball start=16 end=24."
}
```

With `matchAll` available, you can avoid the `while` loop and `exec` with `/g`.

Instead, by using `matchAll`, you get back an iterator which you can use with the more convenient
`for...of`, array spread, or [`Array.from()`](/en/webfrontend/Array.from) constructs:

```javascript
const regexp = RegExp('foo[a-z]*','g');
const str = 'table football, foosball';
const matches = str.matchAll(regexp);

for (const match of matches) {
  console.log(`Found ${match[0]} start=${match.index} end=${match.index + match[0].length}.`);
}
// expected output: "Found football start=6 end=14."
// expected output: "Found foosball start=16 end=24."

// matches iterator is exhausted after the for..of iteration
// Call matchAll again to create a new iterator
Array.from(str.matchAll(regexp), m => m[0]);
// Array [ "football", "foosball" ]
```

`matchAll` only returns the first match if the `/g` flag is missing.

```javascript
const regexp = RegExp('[a-c]','');
const str = 'abc';
Array.from(str.matchAll(regexp), m => m[0]);
// Array [ "a" ]
```

`matchAll` internally makes a clone of the regexp, so unlike regexp.exec, `lastIndex` does not
change as the string is scanned.

```javascript
const regexp = RegExp('[a-c]','g');
regexp.lastIndex = 1;
const str = 'abc';
Array.from(str.matchAll(regexp), m => `${regexp.lastIndex} ${m[0]}`);
// Array [ "1 b", "1 c" ]
```

### Better access to capturing groups

Another compelling reason for `matchAll` is the improved access to capture groups. Capture groups
are ignored when using `match()` with the global `/g` flag:

```javascript
var regexp = /t(e)(st(\d?))/g;
var str = 'test1test2';

str.match(regexp);
// Array ['test1', 'test2']
```

With matchAll you can access them:

```javascript
let array = [...str.matchAll(regexp)];

array[0];
// ['test1', 'e', 'st1', '1', index: 0, input: 'test1test2', length: 4]
array[1];
// ['test2', 'e', 'st2', '2', index: 5, input: 'test1test2', length: 4]
```
