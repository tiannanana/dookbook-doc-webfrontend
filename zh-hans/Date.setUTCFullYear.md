TOPICS: Date.setUTCFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCFullYear()`

**`setUTCFullYear()`** 方法根据世界标准时间为一个具体日期设置年份。

## 语法

```javascript
dateObj.setUTCFullYear(yearValue[, monthValue[, dayValue]])
```

| 参数 | 说明 |
| :-- | :-- |
| `yearValue` | 指定年份整数值，例如，1995 |
| `monthValue` | 可选。指定一个`0`-`11`之间的整数值，代表从一月到十二月。 |
| `dayValue` | 可选。指定一个`1`-`31`之间的整数值，代表月份中的第几天。如果你指定了`dayValue`参数，那么你必须指定`monthValue`参数。 |

**返回值**: Number

## 描述

如果你没有指定具体的`monthValue`和`dayValue`，将会使用 [`getUTCMonth`](/zh-hans/webfrontend/Date.getUTCMonth) 和
[`getUTCDate`](/zh-hans/webfrontend/Date.getUTCDate) 方法的返回值。

如果你指定的参数超出了期待范围，`setUTCFullYear()`方法将会根据[`Date`](/zh-hans/webfrontend/Date)对象，更新其他参数和日期信息。例如，如果你将`monthValue`设定为`15`，年份会增加`1`，月份值则为为`3`。

## 示例

### 使用 `setUTCFullYear()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCFullYear(1997);
```
