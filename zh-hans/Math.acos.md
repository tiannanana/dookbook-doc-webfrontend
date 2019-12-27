TOPICS: Math.acos
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.acos()`

**`Math.acos()`** 返回一个数的反余弦值（单位为弧度），即：

$$
\forall x \in [{-1};1],\;\mathtt{\operatorname{Math.acos}(x)} = \arccos(x) = \text{ the unique } \;
y \in [0; \pi] \, \text{such that} \; \cos(y) = x
$$

## 语法

```javascript
Math.acos(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

`acos` 方法以 `-1` 到 `1` 的一个数为参数，返回一个 `0` 到 `pi` （弧度）的数值。如果传入的参数值超出了限定的范围，将返回 NaN。

由于 `acos` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.acos()`，而不是作为你创建的 [`Math`](/zh-hans/webfrontend/Math)
实例的属性（`Math` 不是一个构造函数）。

## 示例

### 使用 `Math.acos`

```javascript
Math.acos(-2);  // NaN
Math.acos(-1);  // 3.141592653589793
Math.acos(0);   // 1.5707963267948966
Math.acos(0.5); // 1.0471975511965979
Math.acos(1);   // 0
Math.acos(2);   // NaN
```

对于小于 `-1` 或大于 `1` 的值，`Math.acos` 返回 `NaN`。
