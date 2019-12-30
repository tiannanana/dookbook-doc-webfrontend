TOPICS: String
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript String 对象: `String`

**`String`** *全局对象*是一个用于字符串或一个字符序列的构造函数。

## 语法

字符串字面量采取以下形式：

```javascript
'string text'
"string text"
"中文/汉语"
"español"
"English "
"हिन्दी"
"العربية"
"português"
"বাংলা"
"русский"
"日本語"
"ਪੰਜਾਬੀ"
"한국어"
```

你也能使用 `String` 函数将其他值生成或转换成字符串：

```javascript
String(thing)
new String(thing)
```

## 参数

| 参数 | 说明 |
| :-- | :-- |
| `thing` | 任何可以被转换成字符串的值。 |

## 模板字面量

从 ECMAScript 2015 开始，字符串字面量也可以称为**模板字面量**：

```javascript
`hello world` `hello! world!` `hello ${who}` escape `<a>${who}</a>`
```

## 转义字符

除了普通的可打印字符以外，一些特殊有特殊功能的字符可以通过转义字符的形式放入字符串中：

| Code | Output |
| :--- | :----- |
| `\0` | 空字符 |
| `\'` | 单引号 |
| `\"` | 双引号 |
| `\\` | 反斜杠 |
| `\n` | 换行 |
| `\r` | 回车 |
| `\v` | 垂直制表符 |
| `\t` | 水平制表符 |
| `\b` | 退格 |
| `\f` | 换页 |
| `\uXXXX` | unicode 码 |
| `\u{X} ... \u{XXXXXX}` | unicode codepoint |
| `\xXX` | Latin-1 字符(x小写) |

!!! warn ""
    和其他语言不同，JavaScript 的字符串不区分单引号和双引号，所以不论是单引号还是双引号的字符串，上面的转义字符都能运行 。

## 长字符串

有时，你的代码可能含有很长的字符串。你可能想将这样的字符串写成多行，而不是让这一行无限延长或着被编辑器折叠。有两种方法可以做到这一点。

其一，可以使用 `+` 运算符将多个字符串连接起来，如下所示：

```javascript
let longString = "This is a very long string which needs " +
                 "to wrap across multiple lines because " +
                 "otherwise my code is unreadable.";
```

其二，可以在每行末尾使用反斜杠字符（“`\`”），以指示字符串将在下一行继续。确保反斜杠后面没有空格或任何除换行符之外的字符或缩进; 否则反斜杠将不会工作。 如下所示：

```javascript
let longString = "This is a very long string which needs \
to wrap across multiple lines because \
otherwise my code is unreadable.";
```

使用这两种方式会创建相同的字符串。

## 描述

字符串对于保存可以以文本形式表示的数据非常有用。 一些常用的字符串操作有：查询字符串长度，使用 `+` 和 `+=` 运算符来构建和连接字符串，使用 [`indexOf`](/zh-hans/webfrontend/String.indexOf)
方法检查某一子字符串在父字符串中的位置，又或是使用 `substring` 方法提取从父字符串中提取子字符串。

### 从字符串中获取单个字

获取字符串的某个字符有两种方法。 第一种是使用 [`charAt`](/zh-hans/webfrontend/String.charAt) 方法：

```javascript
return 'cat'.charAt(1); // returns "a"
```

另一种 (在ECMAScript 5中有所介绍) 是把字符串当作一个类似数组的对象，其中的每个字符对应一个数值索引：

```javascript
return 'cat'[1]; // returns "a"
```

使用括号访问字符串不可以对其进行删除或添加，因为字符串对应未知的属性并不是可读或配置的。 (更多的信息请参阅 [`Object.defineProperty`](/zh-hans/webfrontend/Object.defineProperty)。)

### 字符串比较

熟练使用 `C` 语言的开发者经常使用 `strcmp` 函数来比较字符串，但在 JavaScript 中，你只需要使用比较操作符(`>/</>=/<=`)：

```javascript
var a = "a";
var b = "b";
if (a < b) // true
  print(a + " is less than " + b);
else if (a > b)
  print(a + " is greater than " + b);
else
  print(a + " and " + b + " are equal.");
```

使用从字符串实例继承而来的 [`localeCompare`](/zh-hans/webfrontend/String.localeCompare) 方法也能达到同样的效果。

### 基本字符串和字符串对象的区别

请注意区分 JavaScript 字符串对象和基本字符串值 . ( 对于 [`Boolean`](/zh-hans/webfrontend/Boolean) 和
[`Numbers`](/zh-hans/webfrontend/Numbers) 也同样如此.)

字符串字面量 (通过单引号或双引号定义) 和 直接调用 `String` 方法(没有通过 `new` 生成字符串对象实例)的字符串都是基本字符串。JavaScript会自动将基本字符串转换为字符串对象，
只有将基本字符串转化为字符串对象之后才可以使用字符串对象的方法。当基本字符串需要调用一个字符串对象才有的方法或者查询值的时候(基本字符串是没有这些方法的)，JavaScript 会自动将基本字符串转化为字符串对象并且调用相应的方法或者执行查询。

```javascript
var s_prim = "foo";
var s_obj = new String(s_prim);

console.log(typeof s_prim); // Logs "string"
console.log(typeof s_obj);  // Logs "object"
```

当使用 [`eval`]((/zh-hans/webfrontend/eval)时，基本字符串和字符串对象也会产生不同的结果。`eval` 会将基本字符串作为源代码处理;
而字符串对象则被看作对象处理, 返回对象。 例如：

```javascript
s1 = "2 + 2";               // creates a string primitive
s2 = new String("2 + 2");   // creates a String object
console.log(eval(s1));      // returns the number 4
console.log(eval(s2));      // returns the string "2 + 2"
```

由于上述原因, 当一段代码在需要使用基本字符串的时候却使用了字符串对象就会导致执行失败(虽然一般情况下程序员们并不需要考虑这样的问题)。

利用 [`valueOf`](/zh-hans/webfrontend/String.valueOf) 方法，我们可以将字符串对象转换为其对应的基本字符串。

```javascript
console.log(eval(s2.valueOf())); // returns the number 4
```

## 属性

### `String.prototype`

**`String.prototype`** 属性表示 `String` 原型对象。

所有 `String` 的实例都继承自 `String.prototype`. 任何`String.prototype`上的改变都会影响到所有的 `String` 实例。

### `String.length`

**`length`** 属性表示一个字符串的长度。

该属性返回字符串中字符编码单元的数量。JavaScript 使用 `UTF-16` 编码，该编码使用一个 `16` 比特的编码单元来表示大部分常见的字符，使用两个代码单元表示不常用的字符。
因此 `length` 返回值可能与字符串中实际的字符数量不相同。

空字符串的 `length` 为 `0`。

静态属性 `String.length` 返回 `1`。

```javascript
var x = "Mozilla";
var empty = "";

console.log("Mozilla is " + x.length + " code units long");
/* "Mozilla is 7 code units long" */

console.log("The empty string is has a length of " + empty.length);
/* "The empty string is has a length of 0" */
```

## 示例

### 将其他值转换成字符串

使用 `String()` 方法将其它对象转化为字符串可以被认为是一种更加安全的做法，虽然该方法底层使用的也是 [`toString()`](/zh-hans/webfrontend/String.toString)
方法，但是针对 [`null`](/zh-hans/webfrontend/null)/[`undefined`](/zh-hans/webfrontend/undefined)/[`symbols`](/zh-hans/webfrontend/symbols)
`String()` 方法会有特殊的处理：

```javascript
var outputStrings = [];
for (let i = 0, n = inputValues.length; i < n; ++i) {
  outputStrings.push(String(inputValues[i]));
}
```
