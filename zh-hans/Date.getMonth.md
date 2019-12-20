TOPICS: Date.getMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getMonth()`

根据本地时间，返回一个指定的日期对象的月份，为基于`0`的值（`0`表示一年中的第一月）。

## 语法

```javascript
dateObj.getMonth()
```

**参数**: 没有参数

**返回值**: `getMonth`返回一个 `0` 到 `11`的整数值： `0` 代表一月份，`1` 代表二月份， `2` 代表三月份，依次类推。

## 示例

### 使用 `getMonth()`

下面第二条语句，基于 [`Date`](/zh-hans/webfrontend/Date) 对象 `Xmas95` 的值，把`11`赋值给变量 `month`。

```javascript
var Xmas95 = new Date('December 25, 1995 23:15:30');
var month = Xmas95.getMonth();

console.log(month); // 11
```
