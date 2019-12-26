TOPICS: Date.toDateString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toDateString()`

**`toDateString()`** 方法以美式英语和人类易读的形式返回一个日期对象日期部分的字符串。

## 语法

```javascript
dateObj.toDateString()
```

**参数**: 没有参数

**返回值**: String

## 描述

[`Date`] 对象实例引用一个具体的时间点。调用 [`toString`](/zh-hans/webfrontend/Date.toString) 方法会以美式英语和人类易读的形式返回日期对象的
格式化字符串。在 SpiderMonkey 里，该字符串由日期部分（年月日）和其后的时间部分（时分秒及时区）组成。有时需要获取日期部分的字符串，这可以由
[`toDateString`](/zh-hans/webfrontend/Date.toDateString) 方法完成。

[`toDateString`] 方法特别有用，因为实现ECMA-262的兼容引擎在从 [`toString`](/zh-hans/webfrontend/Date.toString) 获取
[`Date`](/zh-hans/webfrontend/Date) 对象的字符串中可能有所不同，因为格式取决于实现且简单的字符串切片方法可能无法在多个引擎上产生一致的结果。

## 示例

### `toDateString` 方法的简单使用

```javascript
var d = new Date(1993, 6, 28, 14, 39, 7);

println(d.toString());     // prints Wed Jul 28 1993 14:39:07 GMT-0600 (PDT)
println(d.toDateString()); // prints Wed Jul 28 1993
```
