TOPICS: Math.imul
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.imul()`

**`Math.imul`** 函数返回两个参数的类`C`的`32`位整数乘法运算的运算结果.

## 语法

```javascript
Math.imul(a, b)
```

| 参数 | 说明 |
| :-- | :-- |
| `a` | 被乘数. |
| `b` | 乘数. |

**返回值**: Number

## 描述

`Math.imul`可以进行快速的,类`C`语义的32位整数乘法.该特性对于一些项目比如Emscripten很有用.

## 示例

```javascript
Math.imul(2, 4) // 8
Math.imul(-1, 8) // -8
Math.imul(-2, -2) // 4
Math.imul(0xffffffff, 5) //-5
Math.imul(0xfffffffe, 5) //-10
```

## Polyfill

下面的JavaScript代码可以实现该函数:

```javascript
function imul(a, b) {
  var ah  = (a >>> 16) & 0xffff;
  var al = a & 0xffff;
  var bh  = (b >>> 16) & 0xffff;
  var bl = b & 0xffff;
  // 右移0位可以修复高位的符号位
  return (al * bl) + (((ah*bl+al*bh)<<16)>>>0);
}
```
