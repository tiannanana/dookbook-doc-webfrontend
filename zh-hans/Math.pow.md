TOPICS: Math.pow
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.pow()`

**`Math.pow()`** 函数返回基数（`base`）的指数（`exponent`）次幂，即 base^^exponent。

## 语法

```javascript
Math.pow(base, exponent)
```

| 参数 | 说明 |
| :-- | :-- |
| `base` | 基数. |
| `exponent` | 指数. |

**返回值**: Number

## 描述

由于 `pow` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.pow()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 对象的方法。

## 示例

### 使用 `Math.pow`

```javascript
function raisePower(x,y) {
   return Math.pow(x,y)
}
```

如果 `x` 是 `2` ，且 `y` 是 `7`，则 `raisePower` 函数返回 `128` （`2` 的 `7` 次幂）。
