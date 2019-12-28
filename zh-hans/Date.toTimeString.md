TOPICS: Date.toTimeString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toTimeString()`

**`toTimeString()`** 方法以人类易读形式返回一个日期对象时间部分的字符串，该字符串以美式英语格式化。

## 语法

```javascript
dateObj.toTimeString()
```

**参数**：没有参数

**返回值**: String

## 描述

[`Date`](/zh-hans/webfrontend/Date) 对象的实例引用一个具体的时间点。 调用 `toString` 方法以美式英语和人类易读的形式，返回日期对象的格式化字符串。
在 SpiderMonkey 里，该字符串由日期部分（年月日）和其后的时间部分（时分秒和时区）组成。有时会需要获取时间部分的字符串，这可以由 `toTimeString` 方法完成。

`toTimeString`方法特别有用，因为实现ECMA-262的兼容引擎在从`toDate`对象的[`Date`](/zh-hans/webfrontend/Date)
对象获得的字符串中可能有所不同，因为格式是与实现相关的。 简单的字符串切片方法可能无法在多个引擎上产生一致的结果。

## 示例

### `toTimeString` 方法的简单使用

```javascript
var d = new Date(1993, 6, 28, 14, 39, 7);

println(d.toString());     // prints Wed Jul 28 1993 14:39:07 GMT-0600 (PDT)
println(d.toTimeString()); // prints 14:39:07 GMT-0600 (PDT)
```
