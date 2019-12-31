TOPICS: String.indexOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.indexOf()`

**`indexOf()`** 方法返回调用它的 [`String`](/zh-hans/webfrontend/String) 对象中第一次出现的指定值的索引，从 `fromIndex` 处进行搜索。
如果未找到该值，则返回 `-1`。

## 语法

```javascript
str.indexOf(searchValue)
str.indexOf(searchValue, fromIndex)
```

| 参数 | 说明 |
| :-- | :-- |
| `searchValue` | 一个字符串表示被查找的值。如果没有提供确切地提供字符串，`searchValue` 会被强制设置为 "`undefined`"， 然后在当前字符串中查找这个值。|
| `fromIndex` 可选 | 表示开始查找的位置。可以是任意整数，默认值为 `0`。如果 `fromIndex` 小于 `0`，则查找整个字符串（等价于传入了 `0`）。如果 `fromIndex` 大于等于 `str.length`，则必返回 `-1`。 |

### 返回值

指定值的第一次出现的索引；如果没有找到，则返回 `-1`。若被查找的字符串是一个空字符串，则返回值在`0`---`str.length` 之间，即：

- `fromIndex` 小于等于 `0` 时，返回 `0`；
- `fromIndex` 大于 `0` 且小于等于 `str.length` 时，返回 `fromIndex`；
- `fromIndex` 大于字符串长度 `str.length` 时，返回 `str.length`。

## 描述

字符串中的字符被从左向右索引。首字符的索引（`index`）为 `0`，字符串 `stringName` 的最后一个字符的索引是 `stringName.length - 1`。

```javascript
"Blue Whale".indexOf("Blue");     // 返回  0
"Blue Whale".indexOf("Blute");    // 返回 -1
"Blue Whale".indexOf("Whale", 0); // 返回  5
"Blue Whale".indexOf("Whale", 5); // 返回  5
"Blue Whale".indexOf("", -1); // 返回 0
"Blue Whale".indexOf("", 9);      // 返回  9
"Blue Whale".indexOf("", 10);     // 返回 10
"Blue Whale".indexOf("", 11);     // 返回 10
```

### 区分大小写

`indexOf` 方法区分大小写。例如，下面的表达式返回 `-1`：

```javascript
"Blue Whale".indexOf("blue") // 返回 -1
```

### 检测是否存在某字符串

当检测某个字符串是否存在于另一个字符串中时，可使用下面的方法：

```javascript
"Blue Whale".indexOf("Blue") !== -1; // true
"Blue Whale".indexOf("Bloe") !== -1; // false
```

## 示例

### 使用 `indexOf()` 和 `lastIndexOf()`

下例使用 `indexOf()` 和 `lastIndexOf()` 方法定位字符串中 "`Brave new world`" 的值。

```javascript
var anyString = "Brave new world";

console.log("The index of the first w from the beginning is " + anyString.indexOf("w"));
// logs 8
console.log("The index of the first w from the end is " + anyString.lastIndexOf("w"));
// logs 10

console.log("The index of 'new' from the beginning is " + anyString.indexOf("new"));
// logs 6
console.log("The index of 'new' from the end is " + anyString.lastIndexOf("new"));
// logs 6
```

## `indexOf` 和区分大小写

下例定义了两个字符串变量。两个变量包含相同的字符串，除了第二个字符串中的某些字符为大写。第一个 `log` 方法输出 `19`。但是由于 `indexOf` 方法区分大小写，因此不会在 `myCapString`
中发现字符串 `“cheddar`"，所以，第二个 `log` 方法会输出 `-1`。

```javascript
var myString    = "brie, pepper jack, cheddar";
var myCapString = "Brie, Pepper Jack, Cheddar";

console.log('myString.indexOf("cheddar") is ' + myString.indexOf("cheddar"));
// logs 19
console.log('myCapString.indexOf("cheddar") is ' + myCapString.indexOf("cheddar"));
// logs -1
```

### 使用 `indexOf` 统计一个字符串中某个字母出现的次数

在下例中，设置了 `count` 来记录字母 `e` 在字符串 `str` 中出现的次数：

```javascript
// 翻译：生存还是毁灭？这是个问题。（莎士比亚《哈姆雷特》）
var str = 'To be, or not to be, that is the question.';
var count = 0;
var pos = str.indexOf('e');

while (pos !== -1) {
  count++;
  pos = str.indexOf('e', pos + 1);
}

console.log(count); // displays 4
```
