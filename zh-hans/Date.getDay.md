TOPICS: Date.getDay
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getDay()`

`getDay()` 方法根据本地时间，返回一个具体日期中一周的第几天，`0` 表示星期天。对于某个月中的第几天，参考[`Date.getDate()`](/zh-hans/webfrontend/Date.getDate).

## 语法

```javascript
dateObj.getDay()
```

**参数**: 没有参数

**返回值**: 根据本地时间，返回一个`0`到`6`之间的整数值，代表星期几： `0` 代表星期日， `1` 代表星期一，`2` 代表星期二， 依次类推。

## 示例

### 使用`getDay()`

下面第二条语句，基于[`Date`](/zh-hans/webfrontend/Date)对象 `Xmas95` 的值，把 `1` 赋值给 `weekday`。也就是说1995年12月25日是星期一。

```javascript
var Xmas95 = new Date("December 25, 1995 23:15:30");
var weekday = Xmas95.getDay();

console.log(weekday); // 1
```

!!! warn "注意"
    如果需要，可以使用[`Intl.DateTimeFormat`](/zh-hans/webfrontend/Intl.DateTimeFormat)与一个额外的 `options` 参数，从而返回这天的全称（如"`Monday`"）.使用此方法，结果会更加国际化：

```javascript
var options = { weekday: 'long'};
console.log(new Intl.DateTimeFormat('en-US', options).format(Xmas95));
// Monday
console.log(new Intl.DateTimeFormat('de-DE', options).format(Xmas95));
// Montag
```
