TOPICS: Date.setMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setMilliseconds()`

**`setMilliseconds()`** 方法会根据本地时间设置一个日期对象的豪秒数。

## 语法

```javascript
dateObj.setMilliseconds(millisecondsValue)
```

| 参数 | 说明 |
| :-- | :-- |
| `millisecondsValue` | 一个 `0` 到 `999` 的数字，表示豪秒数。 |

**返回值**: Number

## 描述

如果指定的数字超出了合理范围，则日期对象的时间信息会被相应地更新。例如，如果指定了 `1005`，则秒数加 `1`，豪秒数为 `5`。

## 示例

### 使用`setMilliseconds`

```javascript
var theBigDay = new Date();
theBigDay.setMilliseconds(100);
```
