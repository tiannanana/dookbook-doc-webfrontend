TOPICS: Math.acosh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.acosh()`

**`Math.acosh()`** 返回一个数字的反双曲余弦值，即：

$$
\forall x \geq 1, \mathtt{\operatorname{Math.acosh}(x)} = \operatorname{arcosh}(x)
= \text{ the unique } \; y \geq 0 \; \text{such that} \; \cosh(y) = x
$$

## 语法

```javascript
Math.acosh(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: 返回指定参数的反双曲余弦值，如果指定的参数小于 `1` 则返回 `NaN`。

## 描述

因为`acosh()`是 [`Math`](/zh-hans/webfrontend/Math) 对象的静态方法，所以你应该像这样使用它：`Math.acosh()`, 而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的属性（`Math`不是构造函数）。

## 示例

### 使用 `Math.acosh()`

```javascript
Math.acosh(-1);  // NaN
Math.acosh(0);   // NaN
Math.acosh(0.5); // NaN
Math.acosh(1);   // 0
Math.acosh(2);   // 1.3169578969248166
```

当参数小于`1`时，`Math.acosh()`将返回 `NaN`。

## 替代方案

当 \\(x \geq 1\\) 时，都有 \\(\operatorname {arcosh} (x) = \ln \left(x + \sqrt{x^{2} - 1} \right)\\)，因此我们可以使用以下函数来模仿`Math.acosh()`：

```javascript
Math.acosh = Math.acosh || function(x) {
  return Math.log(x + Math.sqrt(x * x - 1));
};
```
