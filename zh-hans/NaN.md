TOPICS: NaN
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript 全局属性: `NaN`

全局属性 **`NaN`** 的值表示不是一个数字（**Not-A-Number**）。

## 语法

```javascript
NaN
```

## 描述

`NaN` 是一个*全局对象*的属性。

`NaN` 属性的初始值就是 `NaN`，和 `Number.NaN` 的值一样。在现代浏览器中（ES5中）， `NaN` 属性是一个*不可配置*（non-configurable），*不可写*（non-writable）的属性。但在ES3中，这个属性的值是可以被更改的，但是也应该避免覆盖。

编码中很少直接使用到 `NaN`。通常都是在计算失败时，作为 [`Math`](/zh-hans/webfrontend/Math) 的某个方法的返回值出现的（例如：`Math.sqrt(-1)`）或者尝试将一个字符串解析成数字但失败了的时候（例如：`parseInt("blabla")`）。

### 判断一个值是否是`NaN`

等号运算符（`==` 和 `===`） 不能被用来判断一个值是否是 `NaN`。必须使用 [`Number.isNaN()`](/zh-hans/webfrontend/Number.isNaN)
或 [`isNaN()`](/zh-hans/webfrontend/isNaN) 函数。在执行自比较之中：`NaN`，也只有`NaN`，比较之中不等于它自己。

```javascript
NaN === NaN;        // false
Number.NaN === NaN; // false
isNaN(NaN);         // true
isNaN(Number.NaN);  // true

function valueIsNaN(v) { return v !== v; }
valueIsNaN(1);          // false
valueIsNaN(NaN);        // true
valueIsNaN(Number.NaN); // true
```

但是，请注意[`isNaN()`](/zh-hans/webfrontend/isNaN)和[`Number.isNaN()`](/zh-hans/webfrontend/Number.isNaN)之间的区别：如果当前值是NaN，或者将其强制转换为数字后将是`NaN`，则前者将返回`true`。而后者仅当值当前为NaN时才为`true`：

```javascript
isNaN('hello world');        // true
Number.isNaN('hello world'); // false
```
