TOPICS: Math.tan
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.tan()`

**`Math.tan()`** 方法返回一个数值的正切值。

## 语法

```javascript
Math.tan(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值，表示一个角（单位：弧度）。 |

**返回值**: Number

## 描述

`tan` 方法返回一个数值，表示一个角的正切值。

由于 `tan` 是 [`Math`](/zh-hans/webfrontend/Math) 的静态方法，所以应该像这样使用 `Math.tan()`，而不是作为你创建的
[`Math`](/zh-hans/webfrontend/Math) 实例的方法。

## 示例

### 使用 `Math.tan`

下面的函数返回变量 `x` 的正切值：

```javascript
function getTan(x) {
   return Math.tan(x);
}
```

由于 `Math.tan()` 函数接受弧度数值，但是通常使用度更方便，下面的函数可以接受以度为单位的数值，将其转为弧度，然后返回其正切值。

```javascript
function getTanDeg(deg) {
   var rad = deg * Math.PI/180;
   return Math.tan(rad);
}
```
