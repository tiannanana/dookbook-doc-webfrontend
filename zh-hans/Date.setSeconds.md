TOPICS: Date.setSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setSeconds()`

**`setSeconds()`** 方法根据本地时间设置一个日期对象的秒数。

## 语法

```javascript
dateObj.setSeconds(secondsValue[, msValue])
```

| 参数 | 说明 |
| :-- | :-- |
| `secondsValue` | 一个 `0` 到 `59` 的整数。 |
| `msValue` | 一个 `0` 到 `999` 的数字，表示微秒数。 |

**返回值**: Number

## 描述

如果没有指定 `msValue` 参数，就会使用 [`getMilliseconds()`](/zh-hans/webfrontend/Date.getMilliseconds) 方法的返回值。

如果一个参数超出了合理范围， `setSeconds` 方法会相应地更新日期对象的时间信息。例如，为 `secondsValue` 指定 `100`，则日期对象的分钟数会相应地加 `1`，
秒数将会使用 `40`。

## 示例

### 使用`setSeconds`方法

```javascript
var theBigDay = new Date();
theBigDay.setSeconds(30)
```
