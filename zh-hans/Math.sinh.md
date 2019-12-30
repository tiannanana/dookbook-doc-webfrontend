TOPICS: Math.sinh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sinh()`

**`Math.sinh()`** 函数返回一个数字(单位为角度)的双曲正弦值.

$$
\mathtt{\operatorname{Math.sinh(x)}} = \frac{e^x - e^{-x}}{2}
$$

## 语法

```javascript
Math.sinh(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 任意数字 (单位为度). |

**返回值**: Number

## 描述

双曲正弦的图像如下:

![Sinh](/media/webfrontend__Sinh.png)

## 示例

```javascript
Math.sinh(0)      // 0
Math.sinh(1)      // 1.1752011936438014
Math.sinh("-1")   // -1.1752011936438014
Math.sinh("foo")  // NaN
```
