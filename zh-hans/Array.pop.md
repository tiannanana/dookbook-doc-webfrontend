TOPICS: Array.pop
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.pop()`

`pop()`方法从数组中删除最后一个元素，并返回该元素的值。此方法更改数组的长度。

## 语法

```javascript
arr.pop()
```

**参数**: 没有参数

**返回类型**: 从数组中删除的元素(当数组为空时返回undefined)。

## 描述

`pop` 方法从一个数组中删除并返回最后一个元素。

`pop` 方法有意具有通用性。该方法和 [`call()`](/zh-hans/webfrontend/Function.call) 或
[`apply()`](/zh-hans/webfrontend/Function.apply) 一起使用时，可应用在类似数组的对象上。`pop`方法根据 `length`属性来确定最后一个元素的位置。如果不包含`length`属性或`length`属性不能被转成一个数值，会将`length`置为`0`，并返回[`undefined`](/zh-hans/webfrontend/undefined)。

如果你在一个空数组上调用 `pop()`，它返回[`undefined`](/zh-hans/webfrontend/undefined)。

## 示例

### 例子: 删除掉数组的最后一个元素

下面的代码首先创建了一个拥有四个元素的数组 myFish，然后删除掉它的最后一个元素。

```javascript
let myFish = ["angel", "clown", "mandarin", "surgeon"];

let popped = myFish.pop();

console.log(myFish);
// ["angel", "clown", "mandarin"]

console.log(popped);
// surgeon
```
