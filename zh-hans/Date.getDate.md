TOPICS: Date.getDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getDate()`

根据本地时间，返回一个指定的日期对象为一个月中的哪一日（从`1--31`）。

## 语法

```javascript
dateObj.getDate()
```

**参数**: 没有参数

## 描述

`getDate()` 返回一个 `1` 到 `31`的整数值。

## 示例

### 使用`getDate()`方法

下面第二条语句将值`25`赋给 `day` 变量，该值基于日期对象 `Xmax95`的值。

```javascript
var Xmas95 = new Date("December 25, 1995 23:15:00");
var day = Xmas95.getDate();

alert(day); // 25
```
