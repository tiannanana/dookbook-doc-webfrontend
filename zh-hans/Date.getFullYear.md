TOPICS: Date.getFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getFullYear()`

`getFullYear()` 方法根据本地时间返回指定日期的年份。

此方法替代 [`getYear()`](/zh-hans/webfrontend/Date.getYear) 。

## 语法

```javascript
dateObj.getFullYear()
```

**参数**: 没有参数

**返回值**: 根据当地时间，返回一个对应于给定日期的年份数字。

## 描述

`getFullYear()`返回的值是绝对数。 对于`1000`到`9999`之间的日期，`getFullYear()`返回一个四位数字，如1995。使用此函数确保在2000年后兼容。

## 示例

### 使用`getFullYear()`

下面的例子将当前年份的四位数值分配给变量`year`。

```javascript
var today = new Date();
var year = today.getFullYear();
```
