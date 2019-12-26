TOPICS: Date.getUTCFullYear
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getUTCFullYear()`

**`getUTCFullYear()`** 以世界时为标准，返回一个指定的日期对象的年份。

## 语法

```javascript
dateObj.getUTCFullYear()
```

**参数**: 没有参数

**返回值**: `getUTCFullYear()` 返回一个绝对数值，符合 `Year-2000` 标准，例如 `1995`。

## 示例

### 使用 `getUTCFullYear()` 方法

下面的例子是把当前年份的四位数值复制给变量 `year`。

```javascript
var today = new Date();
var year = today.getUTCFullYear();
```
