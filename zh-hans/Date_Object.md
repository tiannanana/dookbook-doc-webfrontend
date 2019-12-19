TOPICS: Date
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date`

创建一个 JavaScript `Date` 实例，该实例呈现时间中的某个时刻。`Date` 对象则基于 Unix Time Stamp，即自1970年1月1日（UTC）起经过的毫秒数。

## 语法

```javascript
new Date();
new Date(value);
new Date(dateString);
new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);
```

## 参数

!!! warn "注意"
    参数`monthIndex` 是从“`0`”开始计算的，这就意味着一月份为“`0`”，十二月份为“`11`”。

!!! warn "注意"
    当`Date`作为构造函数调用并传入多个参数时，如果数值大于合理范围时（如月份为 `13` 或者分钟数为 `70`），相邻的数值会被调整。
    比如 `new Date(2013, 13, 1)`等于`new Date(2014, 1, 1)`，它们都表示日期2014-02-01（注意月份是从`0`开始的）。其他数值也是类似，
    `new Date(2013, 2, 1, 0, 70)`等于`new Date(2013, 2, 1, 1, 10)`，都表示同一个时间：`2013-03-01T01:10:00`。

!!! warn "注意"
    当`Date`作为构造函数调用并传入多个参数时，所定义参数代表的是当地时间。如果需要使用世界协调时 `UTC`，使用 `new Date(Date.UTC(...)`) 和相同参数。

`Date()`构造函数有四种基本形式

### 没有参数

如果没有提供参数，那么新创建的`Date`对象表示实例化时刻的日期和时间。

### Unix时间戳

| 参数 | 说明 |
| :-- | :-- |
| `value` | 一个 Unix 时间戳（Unix Time Stamp），它是一个整数值，表示自1970年1月1日`00:00:00 UTC`（the Unix epoch）以来的毫秒数，忽略了闰秒。请注意大多数 Unix 时间戳功能仅精确到最接近的秒。|

### 时间戳字符串

| 参数 | 说明 |
| :-- | :-- |
| `dateString` | 表示日期的字符串值。该字符串应该能被 [`Date.parse()`](/zh-hans/webfrontend/Date.parse) 正确方法识别（即符合 IETF-compliant RFC 2822 timestamps 或 version of ISO8601）。

!!! warn "注意"
    由于浏览器之间的差异与不一致性，强烈不推荐使用Date构造函数来解析日期字符串 (或使用与其等价的`Date.parse`)。对 RFC 2822 格式的日期仅有约定俗称的支持。
    对 ISO 8601 格式的支持中，仅有日期的串 (例如 "1970-01-01") 会被处理为 UTC 而不是本地时间，与其他格式的串的处理不同。

### 分别提供日期与时间的每一个成员

当至少提供了年份与月份时，这一形式的 `Date()` 返回的 `Date` 对象中的每一个成员都来自下列参数。没有提供的成员将使用最小可能值（对日期为`1`，其他为`0`）。

| 参数 | 说明 |
| :-- | :-- |
| `year` | 表示年份的整数值。 `0`到`99`会被映射至1900年至1999年，其它值代表实际年份。|
| `monthIndex` | 表示月份的整数值，从 `0`（1月）到 `11`（12月）。|
| `day` 可选 | 表示一个月中的第几天的整数值，从`1`开始。默认值为`1`。|
| `hours` 可选 | 表示一天中的小时数的整数值 (24小时制)。默认值为`0`（午夜）。|
| `minutes` 可选 | 表示一个完整时间（如 `01:10:00`）中的分钟部分的整数值。默认值为`0`。|
| `seconds` 可选 | 表示一个完整时间（如 `01:10:00`）中的秒部分的整数值。默认值为`0`。|
| `milliseconds` 可选 |表示一个完整时间的毫秒部分的整数值。默认值为`0`。|

## 简介

- 如果没有输入任何参数，则`Date`的构造器会依据系统设置的当前时间来创建一个`Date`对象。
- 如果提供了至少两个参数，其余的参数均会默认设置为 `1`（如果没有指定 `day` 参数）或者 `0`（如果没有指定 `day` 以外的参数）。
- JavaScript的时间由世界标准时间（`UTC`）1970年1月1日开始，用毫秒计时，一天由 `86,400,000` 毫秒组成。`Date`
对象的范围是 `-100,000,000` 天至 `100,000,000` 天（等效的毫秒值）。
- `Date` 对象为跨平台提供了统一的行为。时间属性可以在不同的系统中表示相同的时刻，而如果使用了本地时间对象，则反映当地的时间。
- `Date` 对象支持多个处理 `UTC` 时间的方法，也相应地提供了应对当地时间的方法。`UTC`，也就是我们所说的格林威治时间，指的是`time`中的世界时间标准。而当地时间则是指执行JavaScript的客户端电脑所设置的时间。
- 以一个函数的形式来调用 `Date` 对象（即不使用 `new` 操作符）会返回一个代表当前日期和时间的字符串。

## 示例

### 创建一个日期对象的几种方法

下例展示了用来创建一个日期对象的多种方法。

!!! warn "注意"
    由于浏览器差异和不一致性，强烈建议不要使用`Date`构造函数（和`Date.parse`，它们是等效的）解析日期字符串。

```javascript
var today = new Date();
var birthday = new Date('December 17, 1995 03:24:00');
var birthday = new Date('1995-12-17T03:24:00');
var birthday = new Date(1995, 11, 17);
var birthday = new Date(1995, 11, 17, 3, 24, 0);
```

### 将两位数年份映射为 1900 - 1999 年

为了创建和获取 `0` 到 `99` 之间的年份，应使用 [`Date.setFullYear()`](/zh-hans/webfrontend/Date.setFullYear) 和
[`Date.getFullYear()`](/zh-hans/webfrontend/Date.getFullYear) 方法。

```javascript
var date = new Date(98, 1); // Sun Feb 01 1998 00:00:00 GMT+0000 (GMT)

// 已弃用的方法, 同样将 98 映射为 1998
date.setYear(98);           // Sun Feb 01 1998 00:00:00 GMT+0000 (GMT)

date.setFullYear(98);       // Sat Feb 01 0098 00:00:00 GMT+0000 (BST)
```

### 计算经过的时间

下例展示了如何以毫秒精度计算两个日期对象的时间差：

由于不同日期、月份、年份长度的不同（日期长度不同来自夏令时的切换），使用大于秒、分钟、小时的单位表示经过的时间会遇到很多问题，在使用前需要经过详尽的调研。

```javascript
// 使用 Date 对象
var start = Date.now();

// 调用一个消耗一定时间的方法：
doSomethingForALongTime();
var end = Date.now();
var elapsed = end - start; // 以毫秒计的运行时长
// 使用内建的创建方法
var start = new Date();
```

```javascript
// 调用一个消耗一定时间的方法：
doSomethingForALongTime();
var end = new Date();
var elapsed = end.getTime() - start.getTime(); // 运行时间的毫秒值
```

```javascript
// to test a function and get back its return
function printElapsedTime (fTest) {
    var nStartTime = Date.now(),
        vReturn = fTest(),
        nEndTime = Date.now();
    alert("Elapsed time: " + String(nEndTime - nStartTime) + " milliseconds");
    return vReturn;
}
yourFunctionReturn = printElapsedTime(yourFunction);
```

!!! warn "注意"
    在支持 Web Performance API 的高精细度（high-resolution）时间功能的浏览器中，[`Performance.now()`](/zh-hans/webfrontend/Performance.now)
    提供的所经过的时间比 [Date.now()](/zh-hans/webfrontend/Date.now) 更加可靠、精确

### 获取自 Unix 起始时间以来经过的秒数

```javascript
var seconds = Math.floor(Date.now() / 1000);
```

!!! warn "注意"
    此处需要返回一个整数 （仅做除法得到的不是整数），并且需要返回实际已经经过的秒数（所以这里使用了[`Math.floor()`](/zh-hans/webfrontend/Math.floor)而不是[`Math.round()`](/zh-hans/webfrontend/Math.round)).
