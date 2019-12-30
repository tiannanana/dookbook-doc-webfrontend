TOPICS: Math.sin
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.sin()`

**`Math.sin()`** 函数返回一个数值的正弦值。

## 语法

```javascript
Math.sin(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值（以弧度为单位）. |

**返回值**: Number

## 描述

`sin` 方法返回一个 `-1` 到 `1` 之间的数值，表示给定角度（单位：弧度）的正弦值。

由于 `sin` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.sin()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法。

## 示例

### 使用 `Math.sin`

```javascript
Math.sin(0);           // 0
Math.sin(1);           // 0.8414709848078965

Math.sin(Math.PI / 2); // 1
```
