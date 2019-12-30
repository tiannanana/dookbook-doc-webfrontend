TOPICS: Date.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toString()`

**`toString()`** 方法返回一个字符串，表示该[`Date`](/zh-hans/webfrontend/Date)对象。

## 语法

```javascript
dateObj.toString()
```

**参数**: 没有参数

**返回值**: String

## 描述

[`Date`](/zh-hans/webfrontend/Date)对象覆盖了 [`Object`](/zh-hans/webfrontend/Object) 对象的 `toString()` 方法；
它不是继承自 `Object.toString()`。对于  [`Date`](/zh-hans/webfrontend/Date) 对象，`toString()` 方法返回一个表示该对象的字符串。

该 `toString` 方法总是返回一个美式英语日期格式的字符串。

当一个日期对象被用来作为文本值或用来进行字符串连接时，`toString` 方法会被自动调用。

`toString()` 是通用函数。如果不是[`Date`](/zh-hans/webfrontend/Date)实例，则 返回"Invalid Date"。

## 示例

### 使用 `toString` 方法

下例把一个[`Date`](/zh-hans/webfrontend/Date)对象的 `toString` 返回值赋给 `myVar`：

```javascript
var x = new Date();
myVar = x.toString(); // 把类似于下面格式的值赋给 myVar，
// Fri Apr 26 2019 11:46:17 GMT+0800 (中国标准时间)
```
