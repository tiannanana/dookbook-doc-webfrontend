TOPICS: Math.asinh
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.asinh()`

**`Math.asinh()`** 函数返回给定数字的反双曲正弦值, 即：

$$
\mathtt{\operatorname{Math.asinh}(x)} = \operatorname{arsinh}(x) = \text{ the unique } \; y \;
\text{such that} \; \sinh(y) = x
$$

## 语法

```javascript
Math.asinh(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

由于`asinh()`是[`Math`](/zh-hans/webfrontend/Math)的静态方法, 用户应该直接通过`Math.asinh()`来使用, 而不是先创建出[`Math`](/zh-hans/webfrontend/Math)对象再调用该方法（`Math`不是一个构造器）。

## 示例

### 使用 `Math.asinh()`

```javascript
Math.asinh(1);  // 0.881373587019543
Math.asinh(0);  // 0
```

## 其他实现方式

由于\\(\operatorname {arsinh} (x) = \ln \left(x + \sqrt{x^{2} + 1} \right)\\) ，因此该函数可以被如下的函数所模拟：

```javascript
Math.asinh = Math.asinh || function(x) {
  if (x === -Infinity) {
    return x;
  } else {
    return Math.log(x + Math.sqrt(x * x + 1));
  }
};
```
