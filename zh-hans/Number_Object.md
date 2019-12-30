TOPICS: Number

# JavaScript 数值对象：`Number`

JavaScript的 **`Number`** 对象是经过封装的能让你处理数字值的对象。`Number` 对象由 `Number()` 构造器创建。

JavaScript的`Number`类型为**[64位双精度浮点类型 (IEEE 754)](http://en.wikipedia.org/wiki/Double_precision_floating-point_format)**。

最新的JavaScript开始支持[`BigInt`](/zh-hans/webfrontend/BigInt) 任意精度整数类型。

## 语法

```javascript
new Number(value);
var a = new Number('123'); // a === 123 is false
var b = Number('123'); // b === 123 is true
a instanceof Number; // is true
b instanceof Number; // is false
```

| 参数 | 说明 |
| :-- | :-- |
| `value` | 被创建对象的数字值。

## 描述

`Number` 对象主要用于：

- 如果参数无法被转换为数字，则返回[`NaN`](/zh-hans/webfrontend/NaN)。
- 在非构造器上下文中 (如：没有 [`new`](/zh-hans/webfrontend/new) 操作符)，`Number` 能被用来执行类型转换。

`Number.prototype` 属性表示 `Number` 构造函数的原型。

## 属性

### `Number.EPSILON`

`Number.EPSILON` 属性表示 `1` 与`Number`可表示的大于 `1` 的最小的浮点数之间的差值。

你不必创建一个 `Number` 对象来访问这个静态属性（直接使用 `Number.EPSILON`）。

`EPSILON` 属性的值接近于 `2.2204460492503130808472633361816E-16`，或者 \\(2-^{52}\\)。

### `Number.MAX_SAFE_INTEGER`

`Number.MAX_SAFE_INTEGER` **常量**表示在 JavaScript 中最大的安全整数（maximum safe integer)（\\(2^{53} - 1\\)）。

`MAX_SAFE_INTEGER` 是一个值为`9007199254740991`的常量。因为JavaScript的数字存储使用了IEEE 754中规定的双精度浮点数数据类型，而这一数据类型能够安
全存储\((-(2^{53} - 1)\\)到\((2^{53} - 1\\)之间的数值（包含边界值）。

这里安全存储的意思是指能够准确区分两个不相同的值，例如 `Number.MAX_SAFE_INTEGER + 1 === Number.MAX_SAFE_INTEGER + 2` 将得到 `true`的结果，而这在数学上是错误的，参考[`Number.isSafeInteger()`](/zh-hans/webfrontend/Number.isSafeInteger)获取更多信息.

由于 `MAX_SAFE_INTEGER` 是`Number`的一个静态属性，所以你不用自己动手为`Number`对象创建`Number.MAX_SAFE_INTEGER`这一属性，就可以直接使用它。

### `Number.MAX_VALUE`

`Number.MAX_VALUE` 属性表示在 JavaScript 里所能表示的最大数值。

`MAX_VALUE` 属性值接近于 `1.79E+308`。大于 `MAX_VALUE` 的值代表 "`Infinity`"。

因为 `MAX_VALUE` 是 `Number` 对象的一个静态属性，所以你应该直接使用`Number.MAX_VALUE` ，
而不是作为一个创建的 `Number` 实例的属性。

### `Number.MIN_SAFE_INTEGER`

`Number.MIN_SAFE_INTEGER` 代表在 JavaScript中最小的安全的`integer`型数字 (\((-(2^{53} - 1)\\)).

`MIN_SAFE_INTEGER` 的值是`-9007199254740991`. 形成这个数字的原因是 JavaScript 在 IEEE 754中使用
double-precision floating-point format numbers 作为规定。在这个规定中能安全的表示数字的范围在
\((-(2^{53} - 1)\\)到\\(2^{53} - 1\\)之间。

由于`MIN_SAFE_INTEGER` 是`Number`的一个静态属性,你可以直接使用`Number.MIN_SAFE_INTEGER`,
而不是自己去创建一个`Number`的属性。

### `Number.MIN_VALUE`

`Number.MIN_VALUE` 属性表示在 JavaScript 中所能表示的最小的正值。

`MIN_VALUE` 属性是 JavaScript 里最接近 `0` 的正值，而不是最小的负值。

`MIN_VALUE` 的值约为`5e-324`。小于 `MIN_VALUE` ("`underflow values`") 的值将会转换为 `0`。

因为 `MIN_VALUE` 是 `Number` 的一个静态属性，因此应该直接使用： `Number.MIN_VALUE`，
而不是作为一个创建的 `Number` 实例的属性。

### `Number.NaN`

`Number.NaN` 表示“非数字”（Not-A-Number），和[`NaN`](/zh-hans/webfrontend/NaN) 相同。

不必创建一个`Number`实例来访问该属性，使用`Number.NaN`来访问该静态属性。

`EPSILON`属性的值接近于 `2.2204460492503130808472633361816E-16`，或者\\(2-^{52}\\)。

### `Number.NEGATIVE_INFINITY`

`Number.NEGATIVE_INFINITY` 属性表示负无穷大。

不用创建一个 `Number` 实例，使用 `Number.NEGATIVE_INFINITY` 来访问该静态属性。

`Number.NEGATIVE_INFINITY` 的值和全局对象的 `Infinity` 属性的负值相同。

该值的行为同数学上的无穷大（`infinity`）有一点儿不同：

- 任何正值，包括 `POSITIVE_INFINITY`，乘以 `NEGATIVE_INFINITY` 为 `NEGATIVE_INFINITY`。
- 任何负值，包括 `NEGATIVE_INFINITY`，乘以 `NEGATIVE_INFINITY` 为 `POSITIVE_INFINITY`。
- `0` 乘以 `NEGATIVE_INFINITY` 为 `NaN`.
- NaN 乘以 `NEGATIVE_INFINITY` 为 `NaN`.
- `NEGATIVE_INFINITY` 除以任何负值（除了 `NEGATIVE_INFINITY`）为 `POSITIVE_INFINITY`。
- `NEGATIVE_INFINITY` 除以任何正值（除了 `POSITIVE_INFINITY`）为 `NEGATIVE_INFINITY`。
- `NEGATIVE_INFINITY` 除以 `NEGATIVE_INFINITY` 或 `POSITIVE_INFINITY` 是 `NaN`。
- 任何数除以 `NEGATIVE_INFINITY` 为 `0`。

为了成功返回一个有限值，你可能会使用 `Number.NEGATIVE_INFINITY` 属性来判断是否显示一个条件错误 。然而
[`isFinite`](/zh-hans/webfrontend/Number.isFinite) 方法更适合这种情况。

### `Number.POSITIVE_INFINITY`

`Number.POSITIVE_INFINITY` 属性表示正无穷大。

不必创建一个 `Number` 实例，可使用 `Number.POSITIVE_INFINITY` 来访问该静态属性。

`Number.POSITIVE_INFINITY` 的值同全局对象 `Infinity` 属性的值相同。

该值的表现同数学上的无穷大有点儿不同：

- 任何正值，包括 `POSITIVE_INFINITY`，乘以 `POSITIVE_INFINITY` 为 `POSITIVE_INFINITY`。
- 任何负值，包括 `NEGATIVE_INFINITY`，乘以 `POSITIVE_INFINITY` 为 `NEGATIVE_INFINITY`。
- `0` 乘以 `POSITIVE_INFINITY` 为 `NaN`。
- `NaN` 乘以 `POSITIVE_INFINITY` 为 `NaN`。
- `POSITIVE_INFINITY` 除以 `NEGATIVE_INFINITY` 以外的任何负值为 `NEGATIVE_INFINITY`。
- `POSITIVE_INFINITY` 除以 `POSITIVE_INFINITY` 以外的任何正值为 `POSITIVE_INFINITY`。
- `POSITIVE_INFINITY` 除以 `NEGATIVE_INFINITY` 或 `POSITIVE_INFINITY` 为 `NaN`。
- 任何数除以 `POSITIVE_INFINITY` 为 `0`。

您可以使用`Number.POSITIVE_INFINITY`属性指示成功时返回有限数量的错误情况。 但是请注意，在这种情况下[`Number.isFinite()`](/zh-hans/webfrontend/Number.isFinite)更合适。

### `Number.prototype`

`Number.prototype` 属性的属性特性：

所有 `Number` 实例都继承自 `Number.prototype`。修改 `Number` 构造函数的原型对象会影响到所有 `Number` 实例。

## 示例

### 使用 `Number` 对象给数字变量赋值

下例使用 `Number` 对象的属性给几个数字变量赋值：

```javascript
var biggestNum = Number.MAX_VALUE;
var smallestNum = Number.MIN_VALUE;
var infiniteNum = Number.POSITIVE_INFINITY;
var negInfiniteNum = Number.NEGATIVE_INFINITY;
var notANum = Number.NaN;
```

### 整数类型的范围

JavaScript 能够准确表示的整数范围在\\(-2^{53}\\)到\\(2^{53}\\)之间（不含两个端点），超过这个范围，无法精确表示这个整数。 (详情请参阅 ECMAScript standard,
chapter [6.1.6 The Number Type](https://www.ecma-international.org/ecma-262/#sec-ecmascript-language-types-number-type)):

```javascript
var biggestInt = Number.MAX_SAFE_INTEGER;
//9007199254740991
var smallestInt = Number.MIN_SAFE_INTEGER;
//-9007199254740991
```

在解析序列化的JSON时，如果JSON解析器将它们强制转换为`Number`类型，那么超出此范围的整数值可能会被破坏。在工作中使用[`String`](/zh-hans/webfrontend/String)
类型代替，是一个可行的解决方案。

### 使用 `Number` 转换 `Date` 对象

下例使用 `Number` 作为函数来转换 [`Date`](/zh-hans/webfrontend/Date) 对象为数字值

```javascript
var d = new Date("December 17, 1995 03:24:00");
print(Number(d));
```

这将输出 "`819199440000`"。

### 转换数字字符串为数字

```javascript
Number('123')     // 123
Number('12.3')    // 12.3
Number('12.00')   // 12
Number('123e-1')  // 12.3
Number('')        // 0
Number(null)      // 0
Number('0x11')    // 17
Number('0b11')    // 3
Number('0o11')    // 9
Number('foo')     // NaN
Number('100a')    // NaN
```
