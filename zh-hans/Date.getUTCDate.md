TOPICS: Date.getUTCDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCDate()`

**`getUTCDate()`** 方法以世界时为标准，返回一个指定的日期对象为一个月中的第几天

## 语法

```javascript
dateObj.getUTCDate()
```

**参数**: 没有参数

**返回值**: `getUTCDate()` 返回一个 `1` 到 `31` 的整数值

## 描述

该方法返回一个 `0` 到 `59` 的整数值。

## 示例

### 使用`getSeconds`方法

下面的例子是把当前日期的天数部分赋值给变量 `day`.

```javascript
var today = new Date();
var day = today.getUTCDate();
```
