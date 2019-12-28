TOPICS: Math.cbrt
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.cbrt()`

**`Math.cbrt()`** 函数返回任意数字的立方根.

$$
\mathtt{Math.cbrt(x)} = \sqrt[3]{x} = \text{the unique} \; y \; \text{such that} \; y^3 = x
$$

## 语法

```javascript
Math.cbrt(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

该方法为 [`Math`](/zh-hans/webfrontend/Math) 的静态方法,因此请直接通过`Math.cbrt()`方式调用.

而不是作为您创建的 [`Math`](/zh-hans/webfrontend/Math) 对象的方法(`Math`不是构造函数)。

`cbrt` 是 "cube root" 的缩写, 意思是立方根.

## 示例

### 使用 `Math.cbrt()`

```javascript
Math.cbrt(NaN); // NaN
Math.cbrt(-1); // -1
Math.cbrt(-0); // -0
Math.cbrt(-Infinity); // -Infinity
Math.cbrt(0); // 0
Math.cbrt(1); // 1
Math.cbrt(Infinity); // Infinity
Math.cbrt(null); // 0
Math.cbrt(2);  // 1.2599210498948734
```

## Polyfill

为了与旧版浏览器兼容, 可使用下方函数模拟`cbrt()`:

```javascript
if (!Math.cbrt) {
  Math.cbrt = function(x) {
    var y = Math.pow(Math.abs(x), 1/3);
    return x < 0 ? -y : y;
  };
}
```
