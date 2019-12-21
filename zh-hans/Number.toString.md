TOPICS: Number.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.toString()`

**`toString()`** 方法返回指定 [`Number`](/zh-hans/webfrontend/Number) 对象的字符串表示形式。

## 语法

```javascript
numObj.toString([radix])
```

| 参数 | 说明 |
| :-- | :-- |
| `radix` | 指定要用于数字到字符串的转换的基数(从`2`到`36`)。如果未指定 `radix` 参数，则默认值为 `10`。 |

**返回值**: String

## 异常信息

|  | |
| :-- | :-- |
| `RangeError` | 如果 `toString()` 的 `radix` 参数不在 `2` 到 `36` 之间，将会抛出一个 `RangeError。`

## 描述

[`Number`](/zh-hans/webfrontend/Number) 对象覆盖了 [`Object`](/zh-hans/webfrontend/Object) 对象上的 `toString()`
方法，它不是继承的 [`Object.toString()`](/zh-hans/webfrontend/Object.toString)。对于 Number 对象，`toString()` 方法以指定的基数返回该对象的字符串表示。

如果转换的基数大于`10`，则会使用字母来表示大于`9`的数字，比如基数为16的情况，则使用`a`到`f`的字母来表示`10`到`15`。

如果基数没有指定，则使用 `10`。

如果对象是负数，则会保留负号。即使`radix`是`2`时也是如此：返回的字符串包含一个负号（`-`）前缀和正数的二进制表示，不是数值的二进制补码。

进行数字到字符串的转换时，建议**用小括号将要转换的目标括起来**，防止出错。

## 示例

```javascript
var count = 10;

console.log(count.toString());    // 输出 '10'
console.log((17).toString());     // 输出 '17'
console.log((17.2).toString());   // 输出 '17.2'

var x = 6;

console.log(x.toString(2));       // 输出 '110'
console.log((254).toString(16));  // 输出 'fe'

console.log((-10).toString(2));   // 输出 '-1010'
console.log((-0xff).toString(2)); // 输出 '-11111111'
```
