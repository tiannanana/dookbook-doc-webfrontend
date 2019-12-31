TOPICS: String.endsWith
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.endsWith()`

**`endsWith()`** 方法用来判断当前字符串是否是以另外一个给定的子字符串“结尾”的，根据判断结果返回 `true` 或 `false`。

## 语法

```javascript
str.endsWith(searchString[, length])
```

| 参数 | 说明 |
| :-- | :-- |
| `searchString` | 要搜索的子字符串。|
| `length` | 可选。作为 `str` 的长度。默认值为 `str.length`。|

**返回值**: 如果传入的子字符串在搜索字符串的末尾则返回`true`；否则将返回 `false`。

## 描述

这个方法帮助你确定一个字符串是否在另一个字符串的末尾。这个方法是大小写敏感的。

## 示例

### 使用 `endsWith()`

```javascript
var str = "To be, or not to be, that is the question.";

alert( str.endsWith("question.") );  // true
alert( str.endsWith("to be") );      // false
alert( str.endsWith("to be", 19) );  // true
```

## Polyfill

这个方法已经加入到 ECMAScript 6 标准当中，但是可能还没有在所有的  JavaScript 实现中可用。然而，你可以通过如下的代码片段扩展
`String.prototype.endsWith()` 实现兼容：

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
