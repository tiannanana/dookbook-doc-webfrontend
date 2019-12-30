TOPICS: Math.sqrt
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sqrt()`

**`Math.sqrt()`** 函数返回一个数的平方根，即：

$$
\forall x \geq 0, \mathtt{Math.sqrt(x)} = \sqrt{x} = \text{the unique} \; y \geq 0 \;
\text{such that} \; y^2 = x
$$

## 语法

```javascript
Math.sqrt(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

如果参数 `number` 为负值，则 `sqrt` 返回 `NaN`。

由于 `sqrt` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.sqrt()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法。

## 示例

### 使用 `Math.sqrt`

```javascript
Math.sqrt(9); // 3
Math.sqrt(2); // 1.414213562373095

Math.sqrt(1);  // 1
Math.sqrt(0);  // 0
Math.sqrt(-1); // NaN
```
