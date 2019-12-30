TOPICS: Math.log1p
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log1p()`

**`Math.log1p()`** 函数返回一个数字加1后的自然对数 (底为 `E`), 既`log(x+1)`.

## 语法

```javascript
Math.log1p(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 任意数字. |

**返回值**: Number

## 描述

如果参数的值小于 `-1`, 则返回 `NaN`.

函数 `y = log(x+1)` 的图形是这样的:

![logx1](/media/webfrontend__logx1.jpg)

## 示例

```javascript
Math.log1p(Math.E-1)  // 1
Math.log1p(0)         // 0
Math.log1p("0")       // 0
Math.log1p(-1)        // -Infinity
Math.log1p(-2)        // NaN
Math.log1p("foo")     // NaN
```
