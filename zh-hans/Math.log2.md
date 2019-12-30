TOPICS: Math.log2
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log2()`

**`Math.log2()`** 函数返回一个数字以 `2` 为底的对数.

## 语法

```javascript
Math.log2(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 任意数字. |

**返回值**: Number

## 描述

如果传入的参数小于 `0`, 则返回 `NaN`.

## 示例

```javascript
Math.log2(2)     // 1
Math.log2(1024)  // 10
Math.log2(1)     // 0
Math.log2(0)     // -Infinity
Math.log2(-2)    // NaN
Math.log2("1024")// 10
Math.log2("foo") // NaN
```
