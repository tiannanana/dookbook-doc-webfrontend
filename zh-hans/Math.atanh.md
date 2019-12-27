TOPICS: Math.atanh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.atanh()`

**`Math.atanh()`** 函数返回一个数值反双曲正切值, 即：

$$
\forall x \in \left( -1, 1 \right), \mathtt{\operatorname{Math.atanh}(x)} = \operatorname{arctanh}(x)
= \text{ the unique } \; y \; \text{such that} \; \tanh(y) = x
$$

## 语法

```javascript
Math.atanh(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

由于 `atanh()` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法,所以应该像这样使用：`Math.atanh()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法（`Math` 不是一个构造函数）。

## 示例

### 使用 `Math.atanh()`

```javascript
Math.atanh(-2);  // NaN
Math.atanh(-1);  // -Infinity
Math.atanh(0);   // 0
Math.atanh(0.5); // 0.5493061443340548
Math.atanh(1);   // Infinity
Math.atanh(2);   // NaN
```

对于大于`1`或是小于`－1`的值，函数返回 `NaN` 。
