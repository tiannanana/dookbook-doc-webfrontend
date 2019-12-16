TOPICS: Array.prototype.unshift
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.unshift()`

`unshift()` 方法将一个或多个元素添加到数组的开头，并返回该数组的新长度(该方法修改原有数组)。

## 语法

```javascript
arr.unshift(element1, ..., elementN)
```

| 参数 | 说明 |
| :-- | :-- |
| `elementN` | 要添加到数组开头的元素或多个元素。 |

**返回类型**: 当一个对象调用该方法时，返回其 `length` 属性值。

## 描述

`unshift` 方法会在调用它的类数组对象的开始位置插入给定的参数。

`unshift` 特意被设计成具有通用性；这个方法能够通过 [`call`](/zh-hans/webfrontend/Function.prototype.call) 或 [`apply`](/zh-hans/webfrontend/Function.prototype.apply)
方法作用于类数组对象上。不过对于没有 `length` 属性（代表从`0`开始的一系列连续的数字属性的最后一个）的对象，调用该方法可能没有任何意义。

!!! warn "注意"
    如果传入多个参数，它们会被以块的形式插入到对象的开始位置，它们的顺序和被作为参数传入时的顺序一致。 于是，传入多个参数调用一次 `unshift` ，和传入一个参数调用多次 `unshift`
    (例如，循环调用)，它们将得到不同的结果。例如:

```javascript
let arr = [4,5,6];
arr.unshift(1,2,3);
console.log(arr); // [1, 2, 3, 4, 5, 6]

arr = [4,5,6]; // 重置数组
arr.unshift(1);
arr.unshift(2);
arr.unshift(3);
console.log(arr); // [3, 2, 1, 4, 5, 6]
```

## 示例

```javascript
let arr = [1, 2];

arr.unshift(0); // result of the call is 3, which is the new array length
// arr is [0, 1, 2]

arr.unshift(-2, -1); // the new array length is 5
// arr is [-2, -1, 0, 1, 2]

arr.unshift([-4, -3]); // the new array length is 6
// arr is [[-4, -3], -2, -1, 0, 1, 2]

arr.unshift([-7, -6], [-5]); // the new array length is 8
// arr is [ [-7, -6], [-5], [-4, -3], -2, -1, 0, 1, 2 ]
```
