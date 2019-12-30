TOPICS: Math.tanh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.tanh()`

**`Math.tanh()`** 函数将会返回一个数的双曲正切函数值，计算如下:

$$
\tanh x = \frac{\sinh x}{\cosh x} = \frac {e^x - e^{-x}} {e^x + e^{-x}} = \frac{e^{2x} - 1}{e^{2x}+1}
$$

## 语法

```javascript
Math.tanh(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 待计算的数字 |

**返回值**: Number

## 描述

因为 `tanh()` 是 [`Math`](/zh-hans/webfrontend/Math) 的一个静态方法, 所以应该直接通过 `Math.tanh()` 来使用,而不是由用户先创建出
[`Math`](/zh-hans/webfrontend/Math) 对象再调用该方法。(`Math`不是一个构造器)。

## 示例

### 使用 `Math.tanh`

```javascript
Math.tanh(0);        // 0
Math.tanh(Infinity); // 1
Math.tanh(1);        // 0.7615941559557649
```

## 多种实现方式

`tanh()`可以通过[`Math.exp()`](/zh-hans/webfrontend/Math.exp)函数来构拟:

```javascript
Math.tanh = Math.tanh || function(x) {
  if (x === Infinity) {
    return 1;
  } else if (x === -Infinity) {
    return -1;
  } else {
    return (Math.exp(x) - Math.exp(-x)) / (Math.exp(x) + Math.exp(-x));
  }
}
```

或者只调用一次[`Math.exp()`](/zh-hans/webfrontend/Math.exp):

```javascript
Math.tanh = Math.tanh || function(x) {
  if (x === Infinity) {
    return 1;
  } else if (x === -Infinity) {
    return -1;
  } else {
    var y = Math.exp(2 * x);
    return (y - 1) / (y + 1);
  }
}
```
