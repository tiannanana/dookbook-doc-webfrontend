TOPICS: parseInt
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `parseInt()`

**`parseInt(string, radix)`** 将一个字符串 `string` 转换为 `radix` 进制的整数， `radix` 为介于`2-36`之间的数。

## 语法

```javascript
parseInt(string, radix);
```

| 参数 | 说明 |
| :-- | :-- |
| `string` | 要被解析的值。如果参数不是一个字符串，则将其转换为字符串(使用 [`ToString`](http://www.ecma-international.org/ecma-262/6.0/#sec-tostring) 抽象操作)。字符串开头的空白符将会被忽略。 |
| `radix` | 一个介于`2`和`36`之间的整数(数学系统的基础)，表示上述字符串的**基数**。比如参数 `10` 表示使用十进制数值系统。**始终指定此参数**可以消除阅读该代码时的困惑并且保证转换结果可预测。当未指定基数时，不同的实现会产生不同的结果，通常认为其值默认为 **`10`** ，但是如果你的代码运行在过时的浏览器中，那么请在使用时**总是显式地指定 `radix`**。 |

**返回值**: 返回解析后的整数值。 如果被解析参数的第一个字符无法被转化成数值类型，则返回 `NaN`。

!!! warn "注意"
    `radix`参数为`n`将会把第一个参数看作是一个数的`n`进制表示，而返回的值则是十进制的。例如：

```javascript
parseInt('123', 5) // 将'123'看作5进制数，返回十进制数38 => 1*5^2 + 2*5^1 + 3*5^0 = 38
```

## 描述

`parseInt` 函数将其第一个参数转换为字符串，解析它，并返回一个整数或`NaN`。如果不是`NaN`，返回的值将是作为指定基数（基数）中的数字的第一个参数的整数。

例如：`radix`参数为`10` 将会把第一个参数看作是一个数的十进制表示，`8` 对应八进制，`16` 对应十六进制，等等。基数大于 `10` 时，用字母表中的字母来表示大于 `9` 的数字。
例如十六进制中，使用 `A` 到 `F`。

如果`parseInt`的字符不是指定基数中的数字，则忽略该字符和所有后续字符，并返回解析到该点的整数值。`parseInt`将数字截断为整数值。允许使用前导空格和尾随空格。

一些数中可能包含`e`字符（例如`6.022e23`），使用`parseInt`去截取包含e字符数值部分会造成难以预料的结果。例如：

```javascript
parseInt("6.022e23", 10);        // 返回 6
parseInt(6.022e2, 10);          // 返回 602
```

`parseInt`不应该用作 [`Math.floor()`](/zh-hans/webfrontend/Math.floor)的替代品。

如果 `parseInt` 遇到了不属于`radix`参数所指定的基数中的字符那么该字符和其后的字符都将被忽略。接着返回已经解析的整数部分。`parseInt` 将截取整数部分。开头和结尾的空白符允许存在，会被忽略。

在基数为 [`undefined`](/zh-hans/webfrontend/undefined)，或者基数为 `0` 或者没有指定的情况下，JavaScript 作如下处理：

- 如果字符串 `string` 以"`0x`"或者"`0X`"开头, 则基数是`16` (16进制).
- 如果字符串 `string` 以"`0`"开头, 基数是`8`（八进制）或者`10`（十进制），那么具体是哪个基数由实现环境决定。ECMAScript 5 规定使用`10`，但是并不是所有的浏览器都遵循这个规定。因此，永远都要明确给出`radix`参数的值。
- 如果字符串 `string` 以其它任何值开头，则基数是`10` (十进制)。

如果第一个字符不能被转换成数字，`parseInt`返回`NaN`。

算术上， `NaN` 不是任何一个进制下的数。 你可以调用[`isNaN`](/zh-hans/webfrontend/isNaN) 来判断 `parseInt`
是否返回 `NaN`。`NaN` 参与的数学运算其结果总是 `NaN`。

将整型数值以特定基数转换成它的字符串值可以使用 `intValue.toString(radix)`.

## 示例

### 使用 `parseInt`

以下例子均返回`15`:

```javascript
parseInt("0xF", 16);
parseInt("F", 16);
parseInt("17", 8);
parseInt(021, 8);
parseInt("015", 10);   // parseInt(015, 10); 返回 15
parseInt(15.99, 10);
parseInt("15,123", 10);
parseInt("FXX123", 16);
parseInt("1111", 2);
parseInt("15 * 3", 10);
parseInt("15e2", 10);
parseInt("15px", 10);
parseInt("12", 13);
```

以下例子均返回 `NaN`:

```javascript
parseInt("Hello", 8); // 根本就不是数值
parseInt("546", 2);   // 除了“0、1”外，其它数字都不是有效二进制数字
```

以下例子均返回 `-15`：

```javascript
parseInt("-F", 16);
parseInt("-0F", 16);
parseInt("-0XF", 16);
parseInt(-15.1, 10);
parseInt(" -17", 8);
parseInt(" -15", 10);
parseInt("-1111", 2);
parseInt("-15e1", 10);
parseInt("-12", 13);
```

下例中全部返回 `4`:

```javascript
parseInt(4.7, 10);
parseInt(4.7 * 1e22, 10); // 非常大的数值变成 4
parseInt(0.00000000000434, 10); // 非常小的数值变成 4
```

下面的例子返回 `224`

```javascript
parseInt("0e0",16);
```

## 没有指定 `radix` 参数时的八进制解析

尽管 ECMAScript 3 已经不赞成这种做法，且 ECMAScript 5 已经禁止了这种做法，但是仍然有很多实现环境仍然把以 `0` 开头的数值字符串（numeric string）解释为一个八进制数。下面的例子可能返回八进制的结果，也可能返回十进制的结果。**总是指定一个基数（radix）可以避免这种不可靠的行为**。

```javascript
parseInt("0e0");
// 0

parseInt("08");
// 0, '8' 不是八进制数字.
```

### ECMAScript 5 移除了八进制解析

ECMAScript 5 规范不再允许`parseInt`函数的实现环境把以0字符开始的字符串作为八进制数值。ECMAScript 5 陈述如下：

根据给定`radix`，`parseInt`函数产生一个由字符串参数内容解析过来的整数值。字符串中开头的空白会被忽略。如果`radix`没有指定或者为`0`，参数会被假定以`10`为基数来解析，如果数值以字符对`0x`或`0X`开头，会假定以`16`为基数来解析。

这与ECMAScript 3有所不同，ECMAScript 3仅仅是不提倡这种做法但并没有禁止这种做法。

直至2013年，很多实现环境并没有采取新的规范所规定的做法, 而且由于必须兼容旧版的浏览器，所以**永远都要明确给出`radix`参数的值**.

## 一个更严格的解析函数

有时采用一个更严格的方法来解析整型值很有用。此时可以使用正则表达式：

```javascript
filterInt = function (value) {
  if(/^(\-|\+)?([0-9]+|Infinity)$/.test(value))
    return Number(value);
  return NaN;
}

console.log(filterInt('421'));               // 421
console.log(filterInt('-421'));              // -421
console.log(filterInt('+421'));              // 421
console.log(filterInt('Infinity'));          // Infinity
console.log(filterInt('421e+0'));            // NaN
console.log(filterInt('421hop'));            // NaN
console.log(filterInt('hop1.61803398875'));  // NaN
console.log(filterInt('1.61803398875'));     // NaN
```
