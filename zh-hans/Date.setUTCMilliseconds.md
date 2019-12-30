TOPICS: Date.setUTCMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setUTCMilliseconds()`

**`setUTCMilliseconds()`** 方法会根据世界时来设置指定时间的毫秒数。

## 语法

```javascript
dateObj.setUTCMilliseconds(millisecondsValue)
```

| 参数 | 说明 |
| :-- | :-- |
| `millisecondsValue` | `0` - `999` 之间的数值，代表毫秒数。 |

**返回值**: Number

## 描述

如果传递的参数超出了指定的范围，`setUTCMilliseconds()` 方法会相应地尝试更新储存在 [`Date`](/zh-hans/webfrontend/Date) 的时间信息。例如，
假设你传递参数的值是 `1100`，存储在 [`Date`](/zh-hans/webfrontend/Date) 的秒数会加 `1`，然后使用 `100` 来作为毫秒数。

## 示例

### 使用 `setUTCMilliseconds()`

```javascript
var theBigDay = new Date();
theBigDay.setUTCMilliseconds(500);
```
