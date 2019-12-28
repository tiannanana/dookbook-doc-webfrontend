TOPICS: Date.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.valueOf()`

**`valueOf()`** 方法返回一个 [`Date`](/zh-hans/webfrontend/Date) 对象的原始值。

## 语法

```javascript
dateObj.valueOf()
```

**参数**：没有参数

**返回值**: Number

## 描述

`valueOf` 方法返回以数值格式表示的一个 [`Date`](/zh-hans/webfrontend/Date) 对象的原始值，从1970年1月1日0时0分0秒（UTC，即协调世界时）到该日期对象所代表时间的毫秒数。

该方法的功能和 [`Date.getTime()`](/zh-hans/webfrontend/Date.getTime) 方法一样。

该方法通常在 JavaScript 内部被调用，而不是在代码中显式调用。

## 示例

### 使用 `valueOf()`

```javascript
var x = new Date(56, 6, 17);
var myVar = x.valueOf();      // assigns -424713600000 to myVar
```
