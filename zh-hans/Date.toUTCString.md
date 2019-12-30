TOPICS: Date.toUTCString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toUTCString()`

**`toUTCString()`** 方法把一个日期转换为一个字符串，使用UTC时区。

## 语法

```javascript
dateObj.toUTCString()
```

**参数**：没有参数

**返回值**: String

## 描述

`toUTCString` 的返回值是一个使用UTC时区的易读格式字符串。返回值的格式可能随平台而变化。通常返回值是一个 RFC-1123 格式的时间戳，这是一个 RFC-822 时间戳的小幅更新版。

## 示例

### 使用 `toUTCString`

```javascript
var today = new Date();
var UTCstring = today.toUTCString();
// Mon, 03 Jul 2006 21:44:38 GMT
```
