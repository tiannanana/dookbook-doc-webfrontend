TOPICS: Date.setDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setDate()`

**`setDate()`** 方法根据本地时间来指定一个日期对象的天数。

## 语法

```javascript
dateObj.setDate(dayValue)
```

| 参数 | 说明 |
| :-- | :-- |
| `dayValue` | 一个整数，表示该月的第几天。 |

**返回值**: Number

## 描述

如果 `dayValue` 超出了月份的合理范围，`setDate` 将会相应地更新 [`Date`](/zh-hans/webfrontend/Date) 对象。

例如，如果为 `dayValue` 指定`0`，那么日期就会被设置为上个月的最后一天。

如果`dayValue`被设置为负数，日期会设置为上个月最后一天往前数这个负数绝对值天数后的日期。`-1`会设置为上月最后一天的前一天（译者注：例如当前为4月，如果`setDate(-2)`,则为3月29日）

## 示例

### 使用`setDate`方法

```javascript
var theBigDay = new Date(1962, 6, 7); // 1962-07-07
theBigDay.setDate(24);  // 1962-07-24
theBigDay.setDate(32);  // 1962-08-01
```
