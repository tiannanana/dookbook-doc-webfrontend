TOPICS: String.charCodeAt
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.charCodeAt()`

`charCodeAt()` 方法返回`0`到`65535`之间的整数，表示给定索引处的UTF-16代码单元 (在 Unicode 编码单元表示一个单一的 UTF-16 编码单元的情况下，UTF-16
编码单元匹配 Unicode 编码单元。但在——例如 Unicode 编码单元 `> 0x10000` 的这种——不能被一个 UTF-16 编码单元单独表示的情况下，只能匹配 Unicode
代理对的第一个编码单元) 。如果你想要整个代码点的值，使用 `codePointAt()`。

## 语法

```javascript
str.charCodeAt(index)
```

| 参数 | 说明 |
| :-- | :-- |
| `index` | 一个大于等于 `0`，小于字符串长度的整数。如果不是一个数值，则默认为 `0`。|

**返回值**: 返回值是一表示给定索引处（`String`中`index`索引处）字符的 UTF-16 代码单元值的数字；如果索引超出范围，则返回 `NaN`。

## 描述

Unicode 编码单元（code points）的范围从 `0` 到 `1,114,111`（`0x10FFFF`）。开头的 `128` 个 Unicode 编码单元和 ASCII 字符编码一样。
关于 Unicode 的更多信息，可查看 JavaScript Guide。

注意，`charCodeAt` 总是返回一个小于 `65,536` 的值。这是因为高位编码单元（higher code point）使用一对（低位编码 lower valued）
代理伪字符（"surrogate" pseudo-characters）来表示，从而构成一个真正的字符。因此，为了查看或复制（reproduce）`65536` 及以上编码字符的完整字符，
需要在获取 `charCodeAt(i)` 的值的同时获取 `charCodeAt(i+1)` 的值（如同查看/reproducing 拥有两个字符的字符串一样），
或者改为获取 `codePointAt(i)` 的值。参看下面例 2 和例 3。

如果指定的 `index` 小于 `0` 或不小于字符串的长度，则 `charCodeAt` 返回 `NaN`。

向后兼容：在历史版本中（如 JavaScript 1.2），`charCodeAt` 返回一个数字，表示给定 `index` 处字符的 ISO-Latin-1 编码值。ISO-Latin-1
编码集范围从 `0` 到 `255`。开头的 `0` 到 `127` 直接匹配 [[ASCII]] 字符集。

## 示例

### 使用 `charCodeAt()`

下例介绍了不同索引情况下返回的 Unicode 值：

```javascript
"ABC".charCodeAt(0) // returns 65:"A"

"ABC".charCodeAt(1) // returns 66:"B"

"ABC".charCodeAt(2) // returns 67:"C"

"ABC".charCodeAt(3) // returns NaN
```

## 使用 `charCodeAt()` 修复字符串中出现的未知的非基本多语言范围（非BMP，non-Basic-Multilingual-Plane）字符

这段代码可以被用在 `for` 循环和其他类似语句中，当在指定引索之前不确定是否有非BMP字符存在时。

```javascript
function fixedCharCodeAt (str, idx) {
    // ex. fixedCharCodeAt ('\uD800\uDC00', 0); // 65536
    // ex. fixedCharCodeAt ('\uD800\uDC00', 1); // false
    idx = idx || 0;
    var code = str.charCodeAt(idx);
    var hi, low;

    // High surrogate (could change last hex to 0xDB7F to treat high
    // private surrogates as single characters)
    if (0xD800 <= code && code <= 0xDBFF) {
        hi = code;
        low = str.charCodeAt(idx+1);
        if (isNaN(low)) {
            throw 'High surrogate not followed by low surrogate in fixedCharCodeAt()';
        }
        return ((hi - 0xD800) * 0x400) + (low - 0xDC00) + 0x10000;
    }
    if (0xDC00 <= code && code <= 0xDFFF) { // Low surrogate
        // We return false to allow loops to skip this iteration since should have
        // already handled high surrogate above in the previous iteration
        return false;
        /*hi = str.charCodeAt(idx-1);
        low = code;
        return ((hi - 0xD800) * 0x400) + (low - 0xDC00) + 0x10000;*/
    }
    return code;
}
```

### 使用 `charCodeAt()` 修复字符串中出现的已知的非BMP字符

```javascript
function knownCharCodeAt (str, idx) {
    str += '';
    var code,
        end = str.length;

    var surrogatePairs = /[\uD800-\uDBFF][\uDC00-\uDFFF]/g;
    while ((surrogatePairs.exec(str)) != null) {
        var li = surrogatePairs.lastIndex;
        if (li - 2 < idx) {
            idx++;
        }
        else {
            break;
        }
    }

    if (idx >= end || idx < 0) {
        return NaN;
    }

    code = str.charCodeAt(idx);

    var hi, low;
    if (0xD800 <= code && code <= 0xDBFF) {
        hi = code;
        low = str.charCodeAt(idx+1);
        // Go one further, since one of the "characters" is part of a surrogate pair
        return ((hi - 0xD800) * 0x400) + (low - 0xDC00) + 0x10000;
    }
    return code;
}
```
