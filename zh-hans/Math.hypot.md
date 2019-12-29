TOPICS: Math.hypot
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.hypot()`

**`Math.hypot()`** 函数返回它的所有参数的平方和的平方根，即：

$$
\mathtt{\operatorname{Math.hypot}(v_1, v_2, \dots, v_n)} = \sqrt{\sum_{i=1}^n v_i^2}
= \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}
$$

## 语法

```javascript
Math.hypot([value1[,value2, ...]])
```

| 参数 | 说明 |
| :-- | :-- |
| `value1, value2, ...` | 任意多个数字 |

**返回值**: 将所提供的参数求平方和后开平方根的结果。如果有参数不能转换为数字，则返回 `NaN`。

## 描述

计算直角三角形的斜边或复数的幅值时可以使用函数 `Math.sqrt(v1*v1 + v2*v2)` ，其中 `v1` 和 `v2` 是三角形的两个直角边或复数的实部和虚部。如果想计算更多维度，
那么只需要在后面添加更多的数的平方就可以了，比如 `Math.sqrt(v1*v1 + v2*v2 + v3*v3 + v4*v4)`。

本函数比 [`Math.sqrt()`](/zh-hans/webfrontend/Math.sqrt) 更简单也更快，你只需要调用 `Math.hypot(v1, v2)` 或
`Math.hypot(v1, v2, v3, v4, ...)`。

它还避免了幅值过大的问题。在 JS 的双精度浮点数中最大的数字是 `Number.MAX_VALUE = 1.797...e+308`。如果你的数字比约 `1e154` 还大的时候，计算其平方值会返回
`Infinity`，使你的结果出现问题。比如，`Math.sqrt(1e200*1e200 + 1e200*1e200) = Infinity`。如果你改用 `hypot()` 函数，
你可以得到正确的答案：`Math.hypot(1e200, 1e200) = 1.4142...e+200`。在数字非常小的时候同样如此：
`Math.sqrt(1e-200*1e-200 + 1e-200*1e-200) = 0`，但 `Math.hypot(1e-200, 1e-200) =1.4142...e-200`，正确的结果。

由于 `hypot` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该以 `Math.hypot()`的方式使用，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 对象的属性（`Math` 不是一个构造函数）。

如果不传入任何参数, 则返回 `+0` .

如果参数列表中有至少一个参数不能被转换为数字，则返回 [`NaN`](/zh-hans/webfrontend/NaN).

如果只传入一个参数, 则 `Math.hypot(x)` 的效果等同于 `Math.abs(x)`.

## 示例

```javascript
Math.hypot(3, 4)        // 5
Math.hypot(3, 4, 5)     // 7.0710678118654755
Math.hypot()            // 0
Math.hypot(NaN)         // NaN
Math.hypot(3, 4, "foo") // NaN, +"foo" => NaN
Math.hypot(3, 4, "5")   // 7.0710678118654755, +"5" => 5
Math.hypot(-3)          // 3, the same as Math.abs(-3)
```

## Polyfill

此函数可以使用如下代码模拟：

```javascript
if (!Math.hypot) {
  Math.hypot = function hypot() {
    var y = 0;
    var length = arguments.length;

    for (var i = 0; i < length; i++) {
      if(arguments[i] === Infinity || arguments[i] === -Infinity) {
        return Infinity;
      }
      y += arguments[i] * arguments[i];
    }
    return Math.sqrt(y);
  };
}
```
