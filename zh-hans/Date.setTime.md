TOPICS: Date.setTime
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.setTime()`

**`setTime()`** 方法以一个表示从1970-1-1 00:00:00 UTC计时的毫秒数为来为 [`Date`](/zh-hans/webfrontend/Date) 对象设置时间。

## 语法

```javascript
dateObj.setTime(timeValue)
```

| 参数 | 说明 |
| :-- | :-- |
| `timeValue` | 一个整数，表示从1970-1-1 00:00:00 UTC开始计时的毫秒数。 |

**返回值**: Number

## 描述

使用 `setTime` 方法用来把一个日期时间赋值给另一个 [`Date`](/zh-hans/webfrontend/Date) 对象。

## 示例

### 使用`setTime`

```javascript
theBigDay = new Date("July 1, 1999");
sameAsBigDay = new Date();
sameAsBigDay.setTime(theBigDay.getTime());
```
