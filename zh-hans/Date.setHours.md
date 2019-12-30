TOPICS: Date.setHours
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setHours()`

**`setHours()`** 方法根据本地时间为一个日期对象设置小时数，返回从`1970-01-01 00:00:00 UTC` 到更新后的 [`日期`](/zh-hans/webfrontend/Date)
对象实例所表示时间的毫秒数。

## 语法

```javascript
dateObj.setHours(hoursValue[, minutesValue[, secondsValue[, msValue]]])
```

| 参数 | 说明 |
| :-- | :-- |
| `hoursValue` | 一个 `0` 到 `23` 的整数，表示小时。 |
| `minutesValue` | 一个 `0` 到 `59` 的整数，表示分钟。 |
| `secondsValue` | 一个 `0` 到 `59` 的整数，表示秒数。如果指定了 `secondsValue` 参数，则必须同时指定 `minutesValue` 参数。 |
| `msValue` | 一个 `0` 到 `999` 的数字，表示微秒数，如果指定了 `msValue` 参数，则必须同时指定 `minutesValue` 和 `secondsValue` 参数。 |

**返回值**: Number

## 描述

如果不指定 `minutesValue`，`secondsValue` 和 `msValue` 参数，则会使用
[`getMinutes()`](/zh-hans/webfrontend/Date.getMinutes)
[`getSeconds()`](/zh-hans/webfrontend/Date.getSeconds) 和 [`getMilliseconds()`](/zh-hans/webfrontend/Date.getMilliseconds)
方法的返回值。

如果有一个参数超出了合理范围，`setHours` 会相应地更新日期对象中的日期信息。例如，如果为 `secondsValue` 指定了 `100`，则分钟会加 `1`，然后秒数使用 `40`。

## 示例

### 使用`setHours`方法

```javascript
var theBigDay = new Date();
theBigDay.setHours(7);
```
