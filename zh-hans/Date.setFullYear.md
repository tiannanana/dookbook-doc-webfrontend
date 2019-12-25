TOPICS: Date.setFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setFullYear()`

**`setFullYear()`** 方法根据本地时间为一个日期对象设置年份。

## 语法

```javascript
dateObj.setFullYear(yearValue[, monthValue[, dayValue]])
```

| 参数 | 说明 |
| :-- | :-- |
| `yearValue` | 指定年份的整数值，例如1995。 |
| `monthValue` | 一个`0`到`11`之间的整数值，表示从一月到十二月。 |
| `dayValue` | 一个`1`到`31`之间的整数值，表示月份中的第几天。如果你指定了 `dayValue` 参数，就必须同时指定 `monthValue`。 |

**返回值**: Number

## 描述

如果没有指定 `monthValue` 和 `dayValue` 参数，将会使用 [`getMonth`](/zh-hans/webfrontend/Date.getMonth) 和
[`getDate`](/zh-hans/webfrontend/Date.getDate) 方法的返回值。

如果有一个参数超出了合理的范围，`setFullYear` 方法会更新其他参数值，日期对象的日期值也会被相应更新。 例如，为 `monthValue` 指定 `15`， 则年份会加`1`，月份值会为`3`。

## 示例

### 使用`setFullYear`方法

```javascript
var theBigDay = new Date();
theBigDay.setFullYear(1997);
```
