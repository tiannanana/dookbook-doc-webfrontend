TOPICS: Array.prototype.reduceRight
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.reduceRight()`

`reduceRight()` 方法接受一个函数作为累加器（accumulator）和数组的每个值（从右到左）将其减少为单个值。

对于从左至右遍历的相似方法请参阅 [`Array.prototype.reduce()`](/zh-hans/webfrontend/Array.prototype.reduce).

## 语法

```javascript
arr.reduceRight(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

| 参数 | 说明 |
| :-- | :-- |
| `callback` | 一个回调函数，用来操作数组中的每个元素，可接受四个参数：<br>**`accumulator`**<br>上一次调用回调的返回值，或提供的 `initialValue`。<br><br>**`currentValue`**<br>当前被处理的元素。<br><br>**`index`** 可选<br>
数组中当前被处理的元素的索引。<br><br>**`array`** 可选<br>调用 `reduceRight()` 的数组 |
| `initialValue` | 值用作回调的第一次调用的累加器。如果未提供初始值，则将使用并跳过数组中的最后一个元素。在没有初始值的空数组上调用`reduce`或`reduceRight`就会创建一个`TypeError`。 |

**返回类型**: 执行之后的返回值。

## 描述

`reduceRight` 为数组中每个元素调用一次 `callback` 回调函数，但是数组中被删除的索引或从未被赋值的索引会跳过。回调函数接受四个参数：初始值（或上次调用回调的返回值）、当前元素值、当前索引，以及调用迭代的当前数组。

可以像下面这样调用 `reduceRight` 的回调函数 `callback`：

```javascript
array.reduceRight(function(accumulator, currentValue, index, array) {
  // ...
});
```

首次调用回调函数时，`accumulator` 和 `currentValue` 可以是两个值之一。如果调用 `reduceRight` 时提供了 `initialValue` 参数，则
`accumulator`等于 `initialValue`，`currentValue` 等于数组中的最后一个值。如果没有提供 `initialValue` 参数，则 `accumulator`
等于数组最后一个值， `currentValue` 等于数组中倒数第二个值。

如果数组为空，且没有提供 `initialValue` 参数，将会抛出一个 `TypeError` 错误。如果数组只有一个元素且没有提供 `initialValue` 参数，或者提供了
`initialValue` 参数，但是数组为空将会直接返回数组中的那一个元素或 `initialValue` 参数，而不会调用 `callback`。

该函数的完整执行过程见下例：

```javascript
[0, 1, 2, 3, 4].reduceRight(function(previousValue, currentValue, index, array) {
    return previousValue + currentValue;
});
```

回调将会被调用四次，每次调用的参数及返回值如下：

| callback | accumulator | currentValue | currentIndex | array | return value |
| :------- | :---------- | :----------- | :----------- | :---- | :----------- |
| first call | 4 | 3 | 3 | [0, 1, 2, 3, 4] | 7 |
| second call | 7 | 2 | 2 | [0, 1, 2, 3, 4] | 9 |
| third call | 9 | 1 | 1 | [0, 1, 2, 3, 4] | 10 |
| fourth call | 10 | 0 | 0 | [0, 1, 2, 3, 4] | 10 |

`reduceRight` 返回值是最后一次调用回调的返回值（`10`）。

如果提供了一个 `initialValue` 参数，则结果如下：

```javascript
[0, 1, 2, 3, 4].reduceRight(function(previousValue, currentValue, index, array) {
    return previousValue + currentValue;
}, 10);
```

| callback | accumulator | currentValue | currentIndex | array | return value |
| :------- | :---------- | :----------- | :----------- | :---- | :----------- |
| first call | 10 | 4 | 4 | [0, 1, 2, 3, 4] | 14 |
| second call | 14 | 3 | 3 | [0, 1, 2, 3, 4] | 17 |
| third call | 17 | 2 | 2 | [0, 1, 2, 3, 4] | 19 |
| fourth call | 19 | 1 | 1 | [0, 1, 2, 3, 4] | 20 |
| fifth call | 20 | 0 | 0 | [0, 1, 2, 3, 4] | 20 |

`reduceRight` 返回值为 `20`。

## 示例

### 求一个数组中所有值的和

```javascript
var sum = [0, 1, 2, 3].reduceRight(function(a, b) {
  return a + b;
});
// sum is 6
```

### 扁平化（flatten）一个元素为数组的数组

```javascript
var flattened = [[0, 1], [2, 3], [4, 5]].reduceRight(function(a, b) {
    return a.concat(b);
}, []);
// flattened is [4, 5, 2, 3, 0, 1]
```

### 运行一个带有回调每个函数将其结果传给下一个的异步函数列表

```javascript
const waterfall = (...functions) => (callback, ...args) =>
  functions.reduceRight(
    (composition, fn) => (...results) => fn(composition, ...results),
    callback
  )(...args);

const randInt = max => Math.floor(Math.random() * max)

const add5 = (callback, x) => {
  setTimeout(callback, randInt(1000), x + 5);
};
const mult3 = (callback, x) => {
  setTimeout(callback, randInt(1000), x * 3);
};
const sub2 = (callback, x) => {
  setTimeout(callback, randInt(1000), x - 2);
};
const split = (callback, x) => {
  setTimeout(callback, randInt(1000), x, x);
};
const add = (callback, x, y) => {
  setTimeout(callback, randInt(1000), x + y);
};
const div4 = (callback, x) => {
  setTimeout(callback, randInt(1000), x / 4);
};

const computation = waterfall(add5, mult3, sub2, split, add, div4);
computation(console.log, 5) // -> 14

// same as:

const computation2 = (input, callback) => {
  const f6 = x=> div4(callback, x);
  const f5 = (x, y) => add(f6, x, y);
  const f4 = x => split(f5, x);
  const f3 = x => sub2(f4, x);
  const f2 = x => mult3(f3, x);
  add5(f2, input);
}
```

### reduce 与 reduceRight 之间的区别

```javascript
var a = ['1', '2', '3', '4', '5'];
var left  = a.reduce(function(prev, cur)      { return prev + cur; });
var right = a.reduceRight(function(prev, cur) { return prev + cur; });

console.log(left);  // "12345"
console.log(right); // "54321"
```

### 定义可组合函数

组合函数的概念简单，它结合了n个函数。它是一个从右向左流动的函数，用上一个函数的输出调用每个函数。

```javascript
/**
 * Function Composition is way in which result of one function can
 * be passed to another and so on.
 *
 * h(x) = f(g(x))
 *
 * Function execution happens right to left
 *
 * https://en.wikipedia.org/wiki/Function_composition
 */

const compose = (...args) => (value) => args.reduceRight((acc, fn) => fn(acc), value)

// Increament passed number
const inc = (n) => n + 1

// Doubles the passed value
const double = (n) => n * 2

// using composition function
console.log(compose(double, inc)(2)); // 6

// using composition function
console.log(compose(inc, double)(2)); // 5
```

## Polyfill

`reduceRight` 被添加到 ECMA-262 标准第 5 版，因此它在某些实现环境中可能不被支持。把下面的代码添加到脚本开头可以解决此问题，从而允许在那些没有原生支持
`reduceRight` 的实现环境中使用它。

```javascript
// Production steps of ECMA-262, Edition 5, 15.4.4.22
// Reference: http://es5.github.io/#x15.4.4.22
if ('function' !== typeof Array.prototype.reduceRight) {
  Array.prototype.reduceRight = function(callback /*, initialValue*/) {
    'use strict';
    if (null === this || 'undefined' === typeof this) {
      throw new TypeError('Array.prototype.reduceRight called on null or undefined');
    }
    if ('function' !== typeof callback) {
      throw new TypeError(callback + ' is not a function');
    }
    var t = Object(this), len = t.length >>> 0, k = len - 1, value;
    if (arguments.length >= 2) {
      value = arguments[1];
    } else {
      while (k >= 0 && !(k in t)) {
        k--;
      }
      if (k < 0) {
        throw new TypeError('reduceRight of empty array with no initial value');
      }
      value = t[k--];
    }
    for (; k >= 0; k--) {
      if (k in t) {
        value = callback(value, t[k], k, t);
      }
    }
    return value;
  };
}
```
