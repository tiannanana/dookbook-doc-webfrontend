TOPICS: Array.reverse
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.reverse()`

`reverse()` 方法将数组中元素的位置颠倒，并返回该数组。数组的第一个元素会变成最后一个，数组的最后一个元素变成第一个。该方法会改变原数组。

## 语法

```javascript
arr.reverse()
```

**参数**: 没有参数

**返回类型**: 颠倒后的数组。

## 描述

`reverse` 方法颠倒数组中元素的位置，改变了数组，并返回该数组的引用。

`reverse`方法是特意类化的；此方法可被 [`called`](/zh-hans/webfrontend/Function.call) 或 [`applied`](/zh-hans/webfrontend/Function.apply)于类似数组对象。对象如果不包含反映一系列连续的、基于零的数值属性中的最后一个长度的属性，则该对象可能不会以任何有意义的方式运行。

## 示例

### 颠倒数组中的元素

下例将会创建一个数组 `sourceArray`，其包含三个元素，然后颠倒该数组。

`reverse()` 的调用返回了一个颠倒后的数组 `a` 的引用。

```javascript
const a = [1, 2, 3];

console.log(a); // [1, 2, 3]

a.reverse();

console.log(a); // [3, 2, 1]
```

### 颠倒类数组中的元素

下例创造了一个类数组对象 `a`, 包含3个元素和一个 `length` 属性, 然后颠倒这个类数组对象。`reverse()` 的调用返回一个颠倒后的类数组对象`a`的引用。

```javascript
const a = {0: 1, 1: 2, 2: 3, length: 3};

console.log(a); // {0: 1, 1: 2, 2: 3, length: 3}

Array.reverse.call(a); //same syntax for using apply()

console.log(a); // {0: 3, 1: 2, 2: 1, length: 3}
```
