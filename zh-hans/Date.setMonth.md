TOPICS: Date.setMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setMonth()`

**`setMonth()`** 方法根据本地时间为一个设置年份的日期对象设置月份。

## 语法

```javascript
dateObj.setMonth(monthValue[, dayValue])
```

| 参数 | 说明 |
| :-- | :-- |
| `monthValue` | 介于 `0` 到 `11` 之间的整数（表示一月到十二月）。 |
| `dayValue` | 从 `1` 到 `31` 之间的整数，表示月份中的第几天。 |

**返回值**: Number

## 描述

如果不指定 `dayValue` 参数，就会使用 [`getDate`](/zh-hans/webfrontend/Date.getDate) 方法的返回值。

如果有一个指定的参数超出了合理范围，`setMonth` 会相应地更新日期对象中的日期信息。例如，为 `monthValue` 指定 `15`，则年份会加`1`，月份将会使用 `3`。

## 示例

### 使用`setMonth`方法

```javascript
var theBigDay = new Date();
theBigDay.setMonth(6);
```
