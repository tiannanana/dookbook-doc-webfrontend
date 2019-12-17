TOPICS: Boolean Object
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# Boolean Object

`Boolean`对象是一个布尔值的对象包装器。

## 语法

```javascript
new Boolean([value])
```

### 参数

| 参数 | 说明 |
| :-- | :-- |
| `value` | 可选，用来初始化 `Boolean` 对象的值。|

## 描述

如果第一个参数不是布尔值，则会将其转换为布尔值。如果省略该参数，或者其值为 `0`、`-0`、[`null`](/zh-hans/webfrontend/null)、`false`、
[`NaN`](/zh-hans/webfrontend/NaN)、[`undefined`](/zh-hans/webfrontend/undefined)、或者空字符串（`""`），则生成的 `Boolean`
对象的值为 `false`。如果传入的参数是 DOM 对象 [`document.all`](/zh-hans/webfrontend/document.all)，也会生成值为 `false` 的
`Boolean` 对象。任何其他的值，包括值为 `"false"` 的字符串和任何对象，都会创建一个值为 `true` 的 `Boolean` 对象。

注意不要将基本类型中的布尔值 `true` 和 `false` 与值为 `true` 和 `false` 的 `Boolean` 对象弄混了。

任何不是 [`undefined`](/zh-hans/webfrontend/undefined) 和 [`null`](/zh-hans/webfrontend/null) 的对象，包括值为
`false` 的 `Boolean` 对象，直接用于条件语句时都会被当做 `true` 来对待。例如，下面 [`if`](/zh-hans/webfrontend/if) 语句中的条件为真:

```javascript
var x = new Boolean(false);
if (x) {
  // 这里的代码会被执行
}
```

基本类型的布尔值不受此规则影响。例如下面的 [`if`](/zh-hans/webfrontend/if) 语句的条件为假：

```javascript
var x = false;
if (x) {
  // 这里的代码不会执行
}
```

不要用创建 `Boolean` 对象的方式将一个非布尔值转化成布尔值，直接将 `Boolean` 当做转换函数来使用即可，或者使用[双重非（!!）运算符](/zh-hans/webfrontend/Logical_operators)：

```javascript
var x = Boolean(expression);     // 推荐
var x = !!(expression);          // 推荐
var x = new Boolean(expression); // 不太好
```

对于任何对象，即使是值为 `false` 的 `Boolean` 对象，当将其传给 `Boolean` 函数时，生成的 `Boolean` 对象的值都是 `true`。

```javascript
ar myFalse = new Boolean(false);   // false
var g = new Boolean(myFalse);       // true
var myString = new String("Hello");
var s = new Boolean(myString);      // true
```

最后，不要在应该使用基本类型布尔值的地方使用 `Boolean` 对象。

## 示例

### 创建值为 `false` 的 `Boolean` 对象

```javascript
var bNoParam = new Boolean();
var bZero = new Boolean(0);
var bNull = new Boolean(null);
var bEmptyString = new Boolean('');
var bfalse = new Boolean(false);
```

### 创建值为 `true` 的  `Boolean` 对象

```javascript
var btrue = new Boolean(true);
var btrueString = new Boolean('true');
var bfalseString = new Boolean('false');
var bSuLin = new Boolean('Su Lin');
var bArrayProto = new Boolean([]);
var bObjProto = new Boolean({});
```
