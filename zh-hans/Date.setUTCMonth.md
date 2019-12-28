TOPICS: Date.setUTCMonth
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCMonth()`

**`setUTCMonth()`** 方法根据通用的时间来设置一个准确的月份

## 语法

```javascript
dateObj.setUTCMonth(monthValue[, dayValue])
```

| 参数 | 说明 |
| :-- | :-- |
| `monthValue` | 一个`0`-`11`的整数，代表1月到12月。 |
| `dayValue` | 可选参数：一个`1`-`31`的整数，代表一个月的天数。 |

**返回值**: Number

## 描述

如果你没有明确书写 `dayValue` 这个参数，那么就会从 [`getUTCDate()`](/zh-hans/webfrontend/Date.getUTCDate) 方法返回对应的数值.

如果你写了一个超过在规定的范围内的参数. `setUTCMonth()`就会试图相应的更新时间信息在 [`Data`](/zh-hans/webfrontend/Date) 对象中。例如，如果你用`15`作为`monthValue`的值，那么年份就会加`1`，并且月份会变成`3`.（`15=12+3`）

## 示例

### 使用 `setUTCMonth()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCMonth(11);
```
