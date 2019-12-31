TOPICS: Function.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Function.toString()`

**`toString()`** 方法返回一个表示当前函数源代码的字符串。

## 语法

```javascript
function.toString()
```

**参数**: 没有参数

**返回值**: 表示函数源代码的一个字符串

## 描述

[`Function`](/zh-hans/webfrontend/Function) 对象覆盖了从[`Object`](/zh-hans/webfrontend/Object)继承来的
`toString` 方法。对于用户定义的 [`Function`](/zh-hans/webfrontend/Function) 对象，`toString` 方法返回一个字符串，其中包含用于定义函数的源文本段。

在 `Function` 需要转换为字符串时，通常会自动调用函数的 `toString` 方法。

若 `this` 不是 `Function` 对象，则 `toString()` 方法将抛出 `TypeError`  
("Function.prototype.toString called on incompatible object") 异常，比如 `Proxy` 对象就会抛出异常。

```javascript
Function.prototype.toString.call('foo'); // TypeError
```

如果是在内置函数或由 [`Function.bind`](/zh-hans/webfrontend/Function.bind) 返回的函数上调用 `toString()`，则
`toString()` 返回原生代码字符串，如下

```javascript
"function () {\n    [native code]\n}"
```

若是在由 `Function` 构造器生成的函数上调用 `toString()` ，则 `toString()` 返回创建后的函数源码，包括形参和函数体，函数名为 "anonymous"。

## 示例

```javascript
function f(){} // "function f(){}"
```

```javascript
class A { a(){} } // "class A { a(){} }"
```

```javascript
function* g(){} // "function* g(){}"
```

```javascript
a => a // "a => a"
```

```javascript
({ a(){} }.a) // "a(){}"
```

```javascript
({ *a(){} }.a) // "*a(){}"
```

```javascript
({ [0](){} }[0]) // "[0](){}"
```

```javascript
Object.getOwnPropertyDescriptor({
    get a(){}
}, "a").get
// "get a(){}"
```

```javascript
Object.getOwnPropertyDescriptor({
    set a(x){}
}, "a").set
// "set a(x){}"
```

```javascript
Function.prototype.toString // "function toString() { [native code] }"
```

```javascript
(function f(){}.bind(0)) // "function () { [native code] }"
```

```javascript
Function("a", "b") // "function anonymous(a\n) {\nb\n}"
```
