TOPICS: Date.setUTCSeconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCSeconds()`

此 **`setUTCSeconds()`** 方法为一个依据国际通用时间的特定日期设置秒数。

## 语法

```javascript
dateObj.setUTCSeconds(secondsValue[, msValue])
```

| 参数 | 说明 |
| :-- | :-- |
| `secondsValue` | 一个在`0`到`59`之间的整数，表示秒数。 |
| `msValue` | 可选参数。一个`0`到`999`之间的数字，代表毫秒数。 |

**返回值**: Number

## 描述

如果你没有设置`msValue`参数的值， 那么返回的值来自 [`getUTCMilliseconds()`](/zh-hans/webfrontend/Date.getUTCMilliseconds)
方法。

如果你指定的值超出了范围, `setUTCSeconds()` 因此会更新 [`Date`](/zh-hans/webfrontend/Date) 对象中date的相关信息 . 举个例子, 如果你设置`secondsValue`为`100`,
[`Date`](/zh-hans/webfrontend/Date) 对象中的分钟数会增加`1`， 并且秒数会变成40.

## 示例

### 使用 `setUTCSeconds()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCSeconds(20);
```
