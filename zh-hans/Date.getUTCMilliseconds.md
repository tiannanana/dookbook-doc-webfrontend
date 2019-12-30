TOPICS: Date.getUTCMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCMilliseconds()`

**`getUTCMilliseconds()`** 方法以世界时为标准，返回一个指定的日期对象的毫秒数。

## 语法

```javascript
dateObj.getUTCMilliseconds()
```

**参数**: 没有参数

**返回值**: `getUTCMilliseconds()` 返回一个 `0` 到 `999` 的整数。

## 描述

该方法返回一个 `0` 到 `59` 的整数值。

## 示例

### 使用 `getUTCMilliseconds()` 方法

下例将当前时间的毫秒部分赋值给变量 `milliseconds`。

```javascript
var today = new Date();
var milliseconds = today.getUTCMilliseconds();
```
