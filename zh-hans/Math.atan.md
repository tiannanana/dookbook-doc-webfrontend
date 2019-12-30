TOPICS: Math.atan
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.atan()`

**`Math.atan()`** 函数返回一个数值的反正切（以弧度为单位），即：

$$
\mathtt{\operatorname{Math.atan}(x)} = \arctan(x) = \text{ the unique } \; y \in \left[-\frac{\pi}{2};
\frac{\pi}{2}\right] \, \text{such that} \; \tan(y) = x
$$

## 语法

```javascript
Math.atan(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

`atan` 返回一个 \\(-\frac{\pi}{2}\\)  到  \\(\frac{\pi}{2}\\)  弧度之间的数值。

由于 `atan` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用：`Math.atan()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法。

## 示例

### 使用 `Math.atan()`

```javascript
Math.atan(1);  // 0.7853981633974483
Math.atan(0);  // 0
```
