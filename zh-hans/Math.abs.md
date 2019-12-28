TOPICS: Math.abs
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.abs()`

**`Math.abs(x)`** 函数返回指定数字 “`x`“ 的绝对值。如下：

$$
{\mathtt{\operatorname{Math.abs}(x)}} = {|x|}
= \begin{cases} x & \text{if} \quad x \geq 0 \\ -x & \text{if} \quad x < 0 \end{cases}
$$

## 语法

```javascript
Math.abs(x);
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

由于 `Math.abs()` 是 [`Math`](/zh-hans/webfrontend/Math) 中的一个静态方法，你应该通过 `Math.abs()` 调用。（`Math` 不是构造器）

## 示例

### `Math.abs()` 函数的行为

传入一个非数字形式的字符串或者 `undefined`/`empty` 变量，将返回 `NaN`。传入 `null` 将返回 `0`。

```javascript
Math.abs('-1');     // 1
Math.abs(-2);       // 2
Math.abs(null);     // 0
Math.abs("string"); // NaN
Math.abs();         // NaN
```
