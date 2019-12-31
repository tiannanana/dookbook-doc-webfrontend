TOPICS: String.match
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.match()`

**`match()`** 方法检索返回一个字符串匹配正则表达式的的结果。

## 语法

```javascript
str.match(regexp)
```

| 参数 | 说明 |
| :-- | :-- |
| `regexp` | 一个正则表达式对象。如果传入一个非正则表达式对象，则会隐式地使用 `new RegExp(obj)` 将其转换为一个 `RegExp` 。如果你没有给出任何参数并直接使用`match()` 方法 ，你将会得到一 个包含空字符串的 [`Array`](/zh-hans/webfrontend/Array): `[""]` 。 |

### 返回值

如果使用`g`标志，则将返回与完整正则表达式匹配的所有结果，但不会返回捕获组。

如果未使用`g`标志，则仅返回第一个完整匹配及其相关的捕获组（`Array`）。 在这种情况下，返回的项目将具有如下所述的其他属性

### 附加属性

如上所述，匹配的结果包含如下所述的附加特性。

- `groups`: 一个捕获组数组 或 [`undefined`](/zh-hans/webfrontend/undefined)（如果没有定义命名捕获组）。
- `index`: 匹配的结果的开始位置
- `input`: 搜索的字符串.

一个[`Array`](/zh-hans/webfrontend/Array)，其内容取决于`global(g)`标志的存在与否，如果未找到匹配则为`null`。

## 描述

如果正则表达式不包含 `g` 标志，`str.match()` 将返回与 `RegExp.exec()`. 相同的结果。

### 参看：RegExp 方法

- 如果你需要知道一个字符串是否与一个正则表达式匹配 `RegExp` ，可使用 `test()` 。
- 如果你只是需要第一个匹配结果，你也可以使用 `RegExp.exec()` 。
- 如果你想要获得捕获组，并且设置了全局标志，你需要用 `RegExp.exec()` 。

## 示例

### 使用 `match()`

在下例中，使用 match 查找 "`Chapter`" 紧跟着 `1` 个或多个数值字符，再紧跟着一个小数点和数值字符 `0` 次或多次。正则表达式包含 `i` 标志，因此大小写会被忽略。

```javascript
var str = 'For more information, see Chapter 3.4.5.1';
var re = /see (chapter \d+(\.\d)*)/i;
var found = str.match(re);

console.log(found);

// logs [ 'see Chapter 3.4.5.1',
//        'Chapter 3.4.5.1',
//        '.1',
//        index: 22,
//        input: 'For more information, see Chapter 3.4.5.1' ]

// 'see Chapter 3.4.5.1' 是整个匹配。
// 'Chapter 3.4.5.1' 被'(chapter \d+(\.\d)*)'捕获。
// '.1' 是被'(\.\d)'捕获的最后一个值。
// 'index' 属性(22) 是整个匹配从零开始的索引。
// 'input' 属性是被解析的原始字符串。
```

### `match` 使用全局（`global`）和忽略大小写（`ignore case`）标志

下例展示了 `match` 使用 `global` 和 `ignore case` 标志。`A-E`、`a-e` 的所有字母将会作为一个数组的元素返回。

```javascript
var str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';
var regexp = /[A-E]/gi;
var matches_array = str.match(regexp);

console.log(matches_array);
// ['A', 'B', 'C', 'D', 'E', 'a', 'b', 'c', 'd', 'e']
```

### 使用`match()`，不传参数

```javascript
var str = "Nothing will come of nothing.";

str.match();   // returns [""]
```

### 一个非正则表达式对象作为参数

当参数是一个字符串或一个数字，它会使用`new RegExp(obj)`来隐式转换成一个 `RegExp`。如果它是一个有正号的正数，`RegExp()` 方法将忽略正号。

```javascript
var str1 = "NaN means not a number. Infinity contains -Infinity and +Infinity in JavaScript.",
    str2 = "My grandfather is 65 years old and My grandmother is 63 years old.",
    str3 = "The contract was declared null and void.";
str1.match("number");   // "number" 是字符串。返回["number"]
str1.match(NaN);        // NaN的类型是number。返回["NaN"]
str1.match(Infinity);   // Infinity的类型是number。返回["Infinity"]
str1.match(+Infinity);  // 返回["Infinity"]
str1.match(-Infinity);  // 返回["-Infinity"]
str2.match(65);         // 返回["65"]
str2.match(+65);        // 有正号的number。返回["65"]
str3.match(null);       // 返回["null"]
```
