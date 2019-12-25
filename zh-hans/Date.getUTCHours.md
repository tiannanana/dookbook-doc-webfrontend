TOPICS: Date.getUTCHours
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCHours()`

**`getUTCHours()`** 方法以世界时为标准，返回一个指定的日期对象的小时数。

## 语法

```javascript
dateObj.getUTCHours()
```

**参数**: 没有参数

**返回值**: `getUTCHours()` 返回一个 `0` 到 `23` 的整数。

## 示例

### 使用 `getUTCHours()` 方法

下例将当前时间的小时部分赋值给变量 `hours`。

```javascript
var today = new Date();
var hours = today.getUTCHours();
```
