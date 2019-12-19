TOPICS: Date.getMinutes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getMinutes()`

`getMinutes()` 方法根据本地时间，返回一个指定的日期对象的分钟数。

## 语法

```javascript
dateObj.getMinutes()
```

**参数**: 没有参数

## 描述

`getMinutes` 返回一个 `0` 到 `59`的整数值。

## 示例

### 使用`getMinutes`方法

下例中，第二行语句运行过后，变量 `minutes` 的值为`15`，也就是说 `Xmas95` 这个日期对象的值为某时`15`分某秒。

```javascript
var Xmas95 = new Date("December 25, 1995 23:15:00");
var minutes = Xmas95.getMinutes();
```
