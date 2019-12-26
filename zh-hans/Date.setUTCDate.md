TOPICS: Date.setUTCDate
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCDate()`

**`setUTCDate()`** 方法就是根据全球时间设置特定date对象的日期。

## 语法

```javascript
dateObj.setUTCDate(dayValue)
```

| 参数 | 说明 |
| :-- | :-- |
| `dayValue` | 一个`1`-`31`的整形数字，用来指定日期。 |

**返回值**: Number

## 描述

如果你指定的参数超出了范围，`setUTCDate()`会尝试更新对应的 [`Date`](/zh-hans/webfrontend/Date) 中的日期信息。例如，如果你使用了`40`来作为参数，
但是 [`Date`](/zh-hans/webfrontend/Date) 中存储的月份为6月，那么日期将被改写为10且月份被增到7月。

## 示例

### 使用 `setUTCDate()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCDate(20);
```
