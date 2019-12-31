TOPICS: String.fromCodePoint
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.fromCodePoint()`

**`String.fromCodePoint()`** 静态方法返回使用指定的代码点序列创建的字符串。

## 语法

```javascript
String.fromCodePoint(num1[, ...[, numN]])
```

| 参数 | 说明 |
| :-- | :-- |
| `num1, ..., numN` | 一串 Unicode 编码位置，即“代码点”。|

**返回值**: 使用指定的 Unicode 编码位置创建的字符串。

### 异常

|  |  |
| :-- | :-- |
| `RangeError` | 如果传入无效的 Unicode 编码，将会抛出一个 `RangeError` (例如： "RangeError: NaN is not a valid code point")。

## 描述

该方法返回一个字符串，而不是一个 [`String`](/zh-hans/webfrontend/String) 对象。

因为 `fromCodePoint()` 是 [`String`](/zh-hans/webfrontend/String) 的一个静态方法，所以只能通过 `String.fromCodePoint()`
这样的方式来使用，不能在你创建的 [`String`](/zh-hans/webfrontend/String) 对象实例上直接调用。

## 示例

### 使用 `fromCodePoint()`

```javascript
String.fromCodePoint(42);       // "*"
String.fromCodePoint(65, 90);   // "AZ"
String.fromCodePoint(0x404);    // "\u0404"
String.fromCodePoint(0x2F804);  // "\uD87E\uDC04"
String.fromCodePoint(194564);   // "\uD87E\uDC04"
String.fromCodePoint(0x1D306, 0x61, 0x1D307) // "\uD834\uDF06a\uD834\uDF07"

String.fromCodePoint('_');      // RangeError
String.fromCodePoint(Infinity); // RangeError
String.fromCodePoint(-1);       // RangeError
String.fromCodePoint(3.14);     // RangeError
String.fromCodePoint(3e-2);     // RangeError
String.fromCodePoint(NaN);      // RangeError
```

```javascript
// String.fromCharCode() 方法不能单独获取在高代码点位上的字符
// 另一方面，下列的示例中，可以返回 4 字节，也可以返回 2 字节的字符
// (也就是说，它可以返回单独的字符，使用长度 2 代替 1!）
console.log(String.fromCodePoint(0x2F804)); // or 194564 in decimal
```

## Polyfill

`String.fromCodePoint` 方法是 ECMAScript2015（ES6）新增加的特性，所以一些老的浏览器可能还不支持。可以通过使用下面的 polyfill 代码来保证浏览器的支持：

```javascript
if (!String.fromCodePoint) (function(stringFromCharCode) {
    var fromCodePoint = function(_) {
      var codeUnits = [], codeLen = 0, result = "";
      for (var index=0, len = arguments.length; index !== len; ++index) {
        var codePoint = +arguments[index];
        // correctly handles all cases including `NaN`, `-Infinity`, `+Infinity`
        // The surrounding `!(...)` is required to correctly handle `NaN` cases
        // The (codePoint>>>0) === codePoint clause handles decimals and negatives
        if (!(codePoint < 0x10FFFF && (codePoint>>>0) === codePoint))
          throw RangeError("Invalid code point: " + codePoint);
        if (codePoint <= 0xFFFF) { // BMP code point
          codeLen = codeUnits.push(codePoint);
        } else { // Astral code point; split in surrogate halves
          // https://mathiasbynens.be/notes/javascript-encoding#surrogate-formulae
          codePoint -= 0x10000;
          codeLen = codeUnits.push(
            (codePoint >> 10) + 0xD800,  // highSurrogate
            (codePoint % 0x400) + 0xDC00 // lowSurrogate
          );
        }
        if (codeLen >= 0x3fff) {
          result += stringFromCharCode.apply(null, codeUnits);
          codeUnits.length = 0;
        }
      }
      return result + stringFromCharCode.apply(null, codeUnits);
    };
    try { // IE 8 only supports `Object.defineProperty` on DOM elements
      Object.defineProperty(String, "fromCodePoint", {
        "value": fromCodePoint, "configurable": true, "writable": true
      });
    } catch(e) {
      String.fromCodePoint = fromCodePoint;
    }
}(String.fromCharCode));
```
