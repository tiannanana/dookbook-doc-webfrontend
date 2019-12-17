TOPICS: Array.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.toString()`

`toString()` 返回一个字符串，表示指定的数组及其元素。

## 语法

```javascript
arr.toString()
```

**参数**: 没有参数

**返回类型**: 一个表示指定的数组及其元素的字符串。

## 描述

[`Array`](/zh-hans/webfrontend/Array)对象覆盖了[`Object`](/zh-hans/webfrontend/Object)的 `toString`
方法。对于数组对象，`toString` 方法连接数组并返回一个字符串，其中包含用逗号分隔的每个数组元素。

当一个数组被作为文本值或者进行字符串连接操作时，将会自动调用其 `toString` 方法。

### ECMAScript 5 semantics

从 JavaScript 1.8.5 (Firefox 4) 开始，和 ECMAScript 第5版语义（semantics）一致，`toString()` 方法是通用的，可被用于任何对象。将调用[`Object.toString()`](/zh-hans/webfrontend/Object.toString)，并返回结果值。
