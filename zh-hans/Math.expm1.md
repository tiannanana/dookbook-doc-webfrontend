TOPICS: Math.expm1
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.expm1()`

**`Math.expm1()`** 函数返回 E^^x - 1, 其中 `x` 是该函数的参数, `E` 是自然对数的底数 `2.718281828459045`.

## 语法

```javascript
Math.expm1(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 任意数字 |

**返回值**: Number

## 描述

参数 `x` 会被自动类型转换成 [`number`](/zh-hans/webfrontend/number) 类型.

`expm1` 是 "exponent minus 1" 的缩写.

## 示例

```javascript
Math.expm1(1)     // 1.7182818284590453
Math.expm1(-38)   // -1
Math.expm1("-38") // -1
Math.expm1("foo") // NaN
```

## Polyfill

因为我们已经有了 `Math.exp` 函数, 所以很容易 polyfill.

```javascript
Math.expm1 = Math.expm1 || function (x) {
    return Math.exp(x) - 1
}
```
