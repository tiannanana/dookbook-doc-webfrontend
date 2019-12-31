TOPICS: String.fromCharCode
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.fromCharCode()`

静态 **`String.fromCharCode()`** 方法返回由指定的UTF-16代码单元序列创建的字符串。

## 语法

```javascript
String.fromCharCode(num1, ..., numN)
```

| 参数 | 说明 |
| :-- | :-- |
| `num1, ..., numN` | 一系列UTF-16代码单元的数字。 范围介于`0`到`65535`（`0xFFFF`）之间。 大于`0xFFFF`的数字将被截断。 不进行有效性检查。|

**返回值**: 一个长度为`N`的字符串，由`N`个指定的UTF-16代码单元组成.

## 描述

该方法返回一个字符串，而不是一个  [`String`](/zh-hans/webfrontend/String) 对象。

由于 `fromCharCode()` 是  [`String`](/zh-hans/webfrontend/String) 的静态方法，所以应该像这样使用：
`String.fromCharCode()`，而不是作为你创建的  [`String`](/zh-hans/webfrontend/String) 对象的方法。

## 示例

### 使用 `fromCharCode`

```javascript
String.fromCharCode(65, 66, 67);  // returns "ABC"
String.fromCharCode(0x2014)       // returns "—"
String.fromCharCode(0x12014)      // also returns "—"; the digit 1 is truncated and ignored
```

## 作用于高位编码（higher values）

尽管绝大部分常用的 Unicode 值可以用一个 16-bit 数字表示（正如JavaScript标准化早期所预期的那样），而`fromCharCode()`可用于返回最常见值的单个字符（即UCS-2值，
即 UTF-16的子集具有最常见的字符），但是为了处理所有的 Unicode 值（最多 21位），只用 `fromCharCode()` 是不够的。由于高位编码字符是用两个低位编码（lower value）
表示形成的一个字符，因此可以使用 [`String.fromCodePoint()`](/zh-hans/webfrontend/String.fromCodePoint) （ES2015标准的一部分）返回这样一对低位编码，从而可以完全表示这些高位编码字符。
