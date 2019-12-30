TOPICS: Math.exp
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.exp()`

**`Math.exp()`** 函数返回 e^^x^^，`x` 表示参数，`e` 是欧拉常数（Euler's constant），自然对数的底数。

## 语法

```javascript
Math.exp(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

由于 `exp` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.exp()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法。

## 示例

### 使用 `Math.exp()`

```javascript
Math.exp(-1); // 0.36787944117144233
Math.exp(0);  // 1
Math.exp(1);  // 2.718281828459045
```
