TOPICS: String.lastIndexOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.lastIndexOf()`

**`lastIndexOf()`** 方法返回调用 [`String`](/zh-hans/webfrontend/String) 对象的指定值最后一次出现的索引，在一个字符串中的指定位置
`fromIndex` 处从后向前搜索。如果没找到这个特定值则返回`-1`。

该方法将从尾到头地检索字符串 `str`，看它是否含有子串 `searchValue`。开始检索的位置在字符串的 `fromIndex` 处或字符串的结尾（没有指定 `fromIndex` 时）。
如果找到一个 `searchValue`，则返回 `searchValue` 的第一个字符在 `str` 中的位置。`str`中的字符位置是从 `0` 开始的。

## 语法

```javascript
str.lastIndexOf(searchValue[, fromIndex])
```

| 参数 | 说明 |
| :-- | :-- |
| `searchValue` | 一个字符串，表示被查找的值。如果`searchValue`是空字符串，则返回`fromIndex`。|
| `fromIndex` 可选 | 待匹配字符串`searchValue`的开头一位字符从 `str`的第`fromIndex`位开始向左回向查找。`fromIndex`默认值是 `+Infinity`。如果 `fromIndex >= str.length` ，则会搜索整个字符串。如果 `fromIndex < 0` ，则等同于 `fromIndex == 0`。|

**返回值**: 返回指定值最后一次出现的索引(该索引仍是以从左至右`0`开始记数的)，如果没找到则返回`-1`。

## 描述

字符串中的字符被从左向右索引。首字符的索引（`index`）是 `0`，最后一个字符的索引是 `stringName.length - 1`。

```javascript
'canal'.lastIndexOf('a');     // returns 3 （没有指明fromIndex则从末尾l处开始反向检索到的第一个a出现在l的后面，即index为3的位置）
'canal'.lastIndexOf('a', 2);  // returns 1（指明fromIndex为2则从n处反向向回检索到其后面就是a，即index为1的位置）
'canal'.lastIndexOf('a', 0);  // returns -1(指明fromIndex为0则从c处向左回向检索a发现没有，故返回-1)
'canal'.lastIndexOf('x');     // returns -1
'canal'.lastIndexOf('c', -5); // returns 0（指明fromIndex为-5则视同0，从c处向左回向查找发现自己就是，故返回0）
'canal'.lastIndexOf('c', 0);  // returns 0（指明fromIndex为0则从c处向左回向查找c发现自己就是，故返回自己的索引0）
'canal'.lastIndexOf('');      // returns 5
'canal'.lastIndexOf('', 2);   // returns 2
```

!!! warn "Note"
    `'abab'.lastIndexOf('ab', 2)` 将返回 `2` 而不是 `0`, 因为`fromIndex`只限制待匹配字符串的开头。

(例如`'abadefgabm'.lastIndexOf('ab', 7)` 返回`7`，虽然查找的`'ab'`中的b已经在 `index=8`的位置了从`index=7`的`a`处向左查找仍是能找到自身`a`加上其后连成`ab`，因为`fromIndex`指的是待匹配字符串的开头那一个)

### 区分大小写

`lastIndexOf` 方法区分大小写。例如，下面的表达式返回 `-1`：

```javascript
"Blue Whale, Killer Whale".lastIndexOf("blue"); // returns -1
```

## 示例

### 使用 `indexOf` 和 `lastIndexOf`

下例使用 `indexOf` 和 `lastIndexOf` 方法来定位字符串 "`Brave new world`" 中的值。

```javascript
var anyString = "Brave new world";

console.log("The index of the first w from the beginning is " + anyString.indexOf("w"));
// Displays 8
console.log("The index of the first w from the end is " + anyString.lastIndexOf("w"));
// Displays 10

console.log("The index of 'new' from the beginning is " + anyString.indexOf("new"));
// Displays 6
console.log("The index of 'new' from the end is " + anyString.lastIndexOf("new"));
// Displays 6
```
