TOPICS: Date.getUTCSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCSeconds()`

**`getUTCSeconds()`** 方法以世界时为标准，返回一个指定的日期对象的秒数。

## 语法

```javascript
dateObj.getUTCSeconds()
```

**参数**: 没有参数

**返回值**: `getUTCSeconds()` 返回一个 `0` 到 `59` 的整数。

## 示例

### 使用 `getUTCSeconds()` 方法

下例将当前时间的秒数部分赋值给变量 `seconds`。

```javascript
var today = new Date();
var seconds = today.getUTCSeconds();
```
