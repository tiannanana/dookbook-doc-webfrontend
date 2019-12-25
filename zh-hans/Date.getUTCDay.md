TOPICS: Date.getUTCDay
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCDay()`

**`getUTCDay()`** 方法以世界时为标准，返回一个指定的日期对象为一星期中的第几天，其中 `0` 代表星期天。

## 语法

```javascript
dateObj.getUTCDay()
```

**参数**: 没有参数

**返回值**: `getUTCDay()` 方法返回一个对应一星期中第几天的整数：`0` 代表星期天，`1` 代表星期一，`2` 代表星期二，依次类推。

## 示例

### 使用 `getUTCDay()` 方法

下面的例子是把当前日期的星期部分赋值给变量 `weekday`。

```javascript
var today = new Date();
var weekday = today.getUTCDay();
```
