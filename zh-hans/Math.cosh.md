TOPICS: Math.cosh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.cosh()`

**`Math.cosh()`** 函数返回数值的双曲余弦函数, 可用 constant e 表示:

$$
\mathtt{\operatorname{Math.cosh(x)}} = \frac{e^x + e^{-x}}{2}
$$

## 语法

```javascript
Math.cosh(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

由于 `cosh()` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态函数, 只需通过 `Math.cosh()` 调用,而不用通过创建
[`Math`](/zh-hans/webfrontend/Math) 对象来调用.

## 示例

### 使用 `Math.cosh()`

```javascript
Math.cosh(0);  // 1
Math.cosh(1);  // 1.5430806348152437
Math.cosh(-1); // 1.5430806348152437
```
