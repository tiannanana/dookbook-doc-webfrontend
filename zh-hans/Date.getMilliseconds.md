TOPICS: Date.getMilliseconds
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getMilliseconds()`

`getMilliseconds()` 方法，根据本地时间，返回一个指定的日期对象的毫秒数。

## 语法

```javascript
dateObj.getMilliseconds()
```

**参数**: 没有参数

## 描述

`getMilliseconds()` 方法返回一个 `0` 到 `999`的整数。

## 示例

### 使用`getMilliseconds`方法

下例中，将当前时间的毫秒数赋值给变量 `ms`。

```javascript
var ms;
Today = new Date();
ms = Today.getMilliseconds();
```
