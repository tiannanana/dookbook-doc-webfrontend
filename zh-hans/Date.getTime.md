TOPICS: Date.getTime
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getTime()`

**`getTime()`** 方法返回一个时间的格林威治时间数值。

你可以使用这个方法把一个日期时间赋值给另一个[`Date`](/zh-hans/webfrontend/Date) 对象。这个方法的功能和
[`valueOf()`](/zh-hans/webfrontend/Date.valueOf) 方法一样。

## 语法

```javascript
dateObj.getTime()
```

**参数**: 没有参数

**返回值**: `getTime` 方法的返回值一个数值，表示从1970年1月1日0时0分0秒（UTC，即协调世界时）距离该日期对象所代表时间的毫秒数。

## 示例

### 使用 `getTime()` 复制日期对象

创建一个拥有相同时间值的日期对象。

```javascript
var birthday = new Date(1991, 9, 17);
var copy = new Date();
copy.setTime(birthday.getTime());
```

### 测量代码执行时间

连续调用两个新生成的日期对象的 `getTime` 方法，根据两次调用的返回值求得时间差。这可以用于计算某些操作的执行时间。避免生成不必要的[`Date`](/zh-hans/webfrontend/Date)对象另见[`Date.now()`](/zh-hans/webfrontend/Date.now)

```javascript
var end, start, i;

start = new Date();
for (i = 0; i < 1000; i++) {
  Math.sqrt(i);
}
end = new Date();

console.log("Operation took " + (end.getTime() - start.getTime()) + " msec");
```
