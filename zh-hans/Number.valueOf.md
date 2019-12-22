TOPICS: Number.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.valueOf()`

**`valueOf()`** 方法返回一个被 [`Number`](/zh-hans/webfrontend/Number) 对象包装的原始值。

## 语法

```javascript
numObj.valueOf()
```

**参数**: 没有参数

**返回值**: 表示指定 `Number` 对象的原始值的数字

## 描述

该方法通常是由 JavaScript 引擎在内部隐式调用的，而不是由用户在代码中显式调用的。

## 示例

```javascript
var numObj = new Number(10);
console.log(typeof numObj); // object

var num = numObj.valueOf();
console.log(num);           // 10
console.log(typeof num);    // number
```
