TOPICS: Date.getHours
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getHours()`

`getHours()` 方法根据本地时间，返回一个指定的日期对象的小时。

## 语法

```javascript
dateObj.getHours()
```

**参数**: 没有参数

**返回值**: `getHours`返回一个 `0` 到 `23`之间的整数值。

## 示例

### 使用`getHours`方法

下面第二条语句，基于日期对象 `Xmas95` 的值，把 `23` 赋值给了变量 `hours`。

```javascript
var Xmas95 = new Date("December 25, 1995 23:15:00");
var hours = Xmas95.getHours();

alert(hours); // 23
```
