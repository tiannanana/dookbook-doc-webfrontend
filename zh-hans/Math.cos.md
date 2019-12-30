TOPICS: Math.cos
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.cos()`

**`Math.cos()`** 函数返回一个数值的余弦值。

## 语法

```javascript
Math.cos(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个以弧度为单位的数值。 |

**返回值**: Number

## 描述

`cos` 方法返回一个 `-1` 到 `1` 之间的数值，表示角度（单位：弧度）的余弦值。

由于 `cos` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.cos()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法。

## 示例

### 使用 `Math.cos()`

```javascript
Math.cos(0);           // 1
Math.cos(1);           // 0.5403023058681398

Math.cos(Math.PI);     // -1
Math.cos(2 * Math.PI); // 1
```
