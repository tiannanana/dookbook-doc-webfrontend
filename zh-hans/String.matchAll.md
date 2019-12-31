TOPICS: String.matchAll
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.matchAll()`

**`matchAll()`** 方法返回一个包含所有匹配正则表达式的结果及分组捕获组的迭代器。

## 语法

```javascript
str.matchAll(regexp)
```

| 参数 | 说明 |
| :-- | :-- |
| `regexp` | 正则表达式对象。如果所传参数不是一个正则表达式对象，则会隐式地使用 `new RegExp(obj)` 将其转换为一个 `RegExp` 。|

**返回值**: 一个迭代器（不可重用，结果耗尽需要再次调用方法，获取一个新的迭代器）。

## 示例

### `Regexp.exec()` 和 `matchAll()`

在 `matchAll` 出现之前，通过在循环中调用`regexp.exec`来获取所有匹配项信息（`regexp`需使用`/g`标志）：

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

如果使用`matchAll` ，就可以不必使用while循环加exec方式（且正则表达式需使用／g标志）。使用`matchAll` 会得到一个迭代器的返回值，配合 `for...of`, 数组传播,
或 [`Array.from()`](/zh-hans/webfrontend/Array.from) 可以更方便实现功能：

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

如果没有 `/g` 标志则 `matchAll` 只会返回首个匹配。

```javascript
const regexp = RegExp('[a-c]','');
const str = 'abc';
Array.from(str.matchAll(regexp), m => m[0]);
// Array [ "a" ]
```

`matchAll` 内部做了一个`regexp`的复制，所以不像 `regexp.exec`, `lastIndex` 在字符串扫描时不会改变。

```javascript
const regexp = RegExp('[a-c]','g');
regexp.lastIndex = 1;
const str = 'abc';
Array.from(str.matchAll(regexp), m => `${regexp.lastIndex} ${m[0]}`);
// Array [ "1 b", "1 c" ]
```

### 捕获组的更佳途径

`matchAll` 的另外一个亮点是更好地获取捕获组。因为当使用[`match()`](/zh-hans/webfrontend/String.match)和`/g`标志方式获取匹配信息时，捕获组会被忽略：

```javascript
var regexp = /t(e)(st(\d?))/g;
var str = 'test1test2';

str.match(regexp);
// Array ['test1', 'test2']
```

使用 `matchAll` 可以通过如下方式获取分组捕获:

```javascript
let array = [...str.matchAll(regexp)];

array[0];
// ['test1', 'e', 'st1', '1', index: 0, input: 'test1test2', length: 4]
array[1];
// ['test2', 'e', 'st2', '2', index: 5, input: 'test1test2', length: 4]
```
