TOPICS: Array.of
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.of()`

`Array.of()` 方法创建一个具有可变数量参数的新数组实例，而不考虑参数的数量或类型。

**`Array.of()`** 和 **`Array`** 构造函数之间的区别在于处理整数参数：**`Array.of(7)`** 创建一个具有单个元素 7 的数组，而 `Array(7)` 创建一个长度为7的空数组（**注意：**这是指一个有7个空位(empty)的数组，而不是由7个`undefined`组成的数组）。

```javascript
Array.of(7);       // [7]
Array.of(1, 2, 3); // [1, 2, 3]

Array(7);          // [ , , , , , , ]
Array(1, 2, 3);    // [1, 2, 3]
```

## 语法

```javascript
Array.of(element0[, element1[, ...[, elementN]]])
```

| 参数 | 说明 |
| :-- | :-- |
| `elementN` | 任意个参数，将按顺序成为返回数组中的元素。 |

**返回类型**: 新的 `Array` 实例。

## 描述

此函数是ECMAScript 2015标准的一部分。详见 `Array.of` 和 [`Array.from`](/zh-hans/webfrontend/Array.from)
proposal 和 `Array.of` polyfill。

## 示例

```javascript
Array.of(1);         // [1]
Array.of(1, 2, 3);   // [1, 2, 3]
Array.of(undefined); // [undefined]
```

## 兼容旧环境

如果原生不支持的话，在其他代码之前执行以下代码会创建 `Array.of()` 。

```javascript
if (!Array.of) {
  Array.of = function() {
    return Array.prototype.slice.call(arguments);
  };
}
```
