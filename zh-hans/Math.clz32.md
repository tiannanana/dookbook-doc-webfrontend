TOPICS: Math.clz32
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.clz32()`

**`Math.clz32()`** 函数返回一个数字在转换成 `32` 无符号整形数字的二进制形式后, 开头的 `0` 的个数, 比如 `1000000` 转换成 `32`位无符号整形数字的二进制
形式后是 `00000000000011110100001001000000`, 开头的 `0` 的个数是 `12` 个, 则 `Math.clz32(1000000)` 返回 `12`.

## 语法

```javascript
Math.clz32 (x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

"`clz32`" 是 `CountLeadingZeroes32` 的缩写.

如果 `x` 不是数字类型, 则它首先会被转换成数字类型, 然后再转成 `32` 位无符号整形数字.

如果转换后的 `32` 位无符号整形数字是 `0`, 则返回 `32`, 因为此时所有位上都是 `0`.

`NaN`, `Infinity`, `-Infinity` 这三个数字转成 `32` 位无符号整形数字后都是 `0`.

这个函数主要用于那些编译目标为 JS 语言的系统中, 比如 Emscripten.

## 示例

```javascript
Math.clz32(1)                // 31
Math.clz32(1000)             // 22
Math.clz32()                 // 32
[NaN, Infinity, -Infinity, 0, -0, null, undefined, "foo", {}, []].filter(function (n) {
  return Math.clz32(n) !== 32
})                           // []
Math.clz32(true)             // 31
Math.clz32(3.5)              // 30
```
