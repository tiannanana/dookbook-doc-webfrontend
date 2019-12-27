TOPICS: Date.setUTCHours
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCHours()`

**`setUTCHours()`** 方法根据世界时设置特定日期的小时，并返回自1970年1月1日UTC到更新的[`Date`](/zh-hans/webfrontend/Date)实例表示的时间为止的毫秒数。

## 语法

```javascript
dateObj.setUTCHours(hoursValue[, minutesValue[, secondsValue[, msValue]]])
```

| 参数 | 说明 |
| :-- | :-- |
| `hoursValue` | 表示小时的整数，取值`0`到`23`之间。 |
| `minutesValue` | 可选参数。表示分钟的整数，取值`0`到`59`之间。 |
| `secondsValue` | 可选参数。表示秒数的整数，取值`0`到`59`之间。如果指定了该参数，就要同时指定`minutesValue`这个参数。 |
| `msValue` | 可选参数。表示毫秒的整数，取值`0`到`999`之间。如果指定了该参数，就要指定`minutesValue`和`secondsValue`这两个参数。 |

**返回值**: Number

## 描述

如果未指定`minutesValue`，`secondsValue`和`msValue`参数，则使用从[`getUTCMinutes()`](/zh-hans/webfrontend/Date.getUTCMinutes)，[`getUTCSeconds()`](/zh-hans/webfrontend/Date.getUTCSeconds)和[`getUTCMilliseconds()`](/zh-hans/webfrontend/Date.getUTCMilliseconds)方法返回的值。

如果您指定的参数超出预期范围，则`setUTCHours()`尝试相应地更新[`Date`](/zh-hans/webfrontend/Date)对象中的日期信息。 例如，
如果您将`100`用作`secondsValue`，则分钟数将增加1（`minutesValue +1`），而将`40`用作秒数。

## 示例

### 使用 `setUTCHours()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCHours(8);
```
