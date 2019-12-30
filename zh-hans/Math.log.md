TOPICS: Math.log
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.log()`

**`Math.log()`** 函数返回一个数的自然对数，即：

$$
\forall x > 0, \mathtt{\operatorname{Math.log}(x)} = \ln(x) = \text{the unique} \; y \;
\text{such that} \; e^y = x
$$

## 语法

```javascript
Math.log(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数字. |

**返回值**: Number

## 描述

如果指定的 `number` 为负数，则返回值为 `NaN`。

由于 `log` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.log()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 对象的方法。

## 示例

### 使用 `Math.log`

下面的函数返回指定变量的自然对数：

```javascript
Math.log(-1); // NaN, out of range
Math.log(0); // -Infinity
Math.log(1); // 0
Math.log(10); // 2.302585092994046
```

### 使用 `Math.log` 时基于不同的底数

下面的函数返回以 `x` 为底 `y` 的对数（即logx y）：

```javascript
function getBaseLog(x, y) {
  return Math.log(y) / Math.log(x);
}
```

如果你运行 `getBaseLog(10, 1000)`，则会返回`2.9999999999999996`，非常接近实际答案：`3`，原因是浮点数精度问题。
