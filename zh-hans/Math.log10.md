TOPICS: Math.log10
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log10()`

**`Math.log10()`** 函数返回一个数字以 `10` 为底的对数.

## 语法

```javascript
Math.log10(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 任意数字. |

**返回值**: Number

## 描述

如果传入的参数小于 `0`, 则返回 `NaN`.

## 示例

```javascript
Math.log10(10)   // 1
Math.log10(100)  // 2
Math.log10("100")// 2
Math.log10(1)    // 0
Math.log10(0)    // -Infinity
Math.log10(-2)   // NaN
Math.log10("foo")// NaN
```
