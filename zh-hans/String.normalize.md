TOPICS: String.normalize
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.normalize()`

**`normalize()`** 方法会按照指定的一种 Unicode 正规形式将当前字符串正规化。（如果该值不是字符串，则首先将其转换为一个字符串）。

## 语法

```javascript
str.normalize([form]);
```

| 参数 | 说明 |
| :-- | :-- |
| `form` | 四种 Unicode 正规形式 "`NFC`", "`NFD`", "`NFKC`", 以及 "`NFKD`" 其中的一个, 默认值为 "`NFC`". <br>1. `NFC`-规范化表格规范组成。<br>2. `NFD`-规范化形式规范分解。<br>3. `NFKC`-规范化表格兼容性组成。<br>4. `NFKD`-规范化表格兼容性分解。|

**返回值**: 含有给定字符串的Unicode规范化形式的字符串。

### 可能出现的异常

|  |  |
| :-- | :-- |
| `RangeError` | 如果给 `form` 传入了非法的参数值, 则会抛出 `RangeError` 异常.

## 描述

`normalize()` 方法返回字符串的指定Unicode规范化形式。它不影响字符串本身的值。

## 示例

### 使用 `normalize()`

```javascript
// Initial string

// U+1E9B: LATIN SMALL LETTER LONG S WITH DOT ABOVE
// U+0323: COMBINING DOT BELOW
var str = "\u1E9B\u0323";


// Canonically-composed form (NFC)

// U+1E9B: LATIN SMALL LETTER LONG S WITH DOT ABOVE
// U+0323: COMBINING DOT BELOW
str.normalize("NFC"); // "\u1E9B\u0323"
str.normalize(); // same as above


// Canonically-decomposed form (NFD)

// U+017F: LATIN SMALL LETTER LONG S
// U+0323: COMBINING DOT BELOW
// U+0307: COMBINING DOT ABOVE
str.normalize("NFD"); // "\u017F\u0323\u0307"


// Compatibly-composed (NFKC)

// U+1E69: LATIN SMALL LETTER S WITH DOT BELOW AND DOT ABOVE
str.normalize("NFKC"); // "\u1E69"


// Compatibly-decomposed (NFKD)

// U+0073: LATIN SMALL LETTER S
// U+0323: COMBINING DOT BELOW
// U+0307: COMBINING DOT ABOVE
str.normalize("NFKD"); // "\u0073\u0323\u0307"
```
