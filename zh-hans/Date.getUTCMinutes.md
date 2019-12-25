TOPICS: Date.getUTCMinutes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCMinutes()`

**`getUTCMinutes()`** 方法以世界时为标准，返回一个指定的日期对象的分钟数。

## 语法

```javascript
dateObj.getUTCMinutes()
```

**参数**: 没有参数

**返回值**: `getUTCMinutes()` 返回一个 `0` 到 `59` 的整数。

## 示例

### 使用 `getUTCMinutes()` 方法

下例将当前时间的分钟部分赋值给变量 `minutes`。

```javascript
var today = new Date();
var minutes = today.getUTCMinutes();
```
