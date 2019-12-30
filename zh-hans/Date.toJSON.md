TOPICS: Date.toJSON
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toJSON()`

**`toJSON()`** 方法返回 [`Date`](/zh-hans/webfrontend/Date) 对象的字符串形式。

## 语法

```javascript
dateObj.toJSON()
```

**参数**: 没有参数

**返回值**: String

## 描述

[`Date`](/zh-hans/webfrontend/Date) 实例引用一个具体的时间点。 调用 `toJSON()` 返回一个 JSON 格式字符串(使用 [`toISOString()`](/zh-hans/webfrontend/Date.toISOString))，
表示该日期对象的值。默认情况下，这个方法常用于 JSON序列化[`Date`](/zh-hans/webfrontend/Date)对象。

## 示例

### `toJSON()` 样例

```javascript
var date = new Date();
console.log(date); //Thu Nov 09 2017 18:54:04 GMT+0800 (中国标准时间)

var jsonDate = (date).toJSON();
console.log(jsonDate); //"2017-11-09T10:51:11.395Z"

var backToDate = new Date(jsonDate);
console.log(backToDate); //Thu Nov 09 2017 18:54:04 GMT+0800 (中国标准时间)
```
