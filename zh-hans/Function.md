TOPICS: Function
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript函数对象 : `Function`

`Function` 构造函数创建一个新的 `Function` 对象。直接调用此构造函数可用动态创建函数，但会遭遇来自 · 的安全问题和相对较小的性能问题。
然而，与 `eval` 不同的是，`Function` 构造函数只在全局作用域中运行。

每个 JavaScript 函数实际上都是一个 `Function` 对象。运行 `(function(){}).constructor === Function` 便可以得到这个结论。

## 语法

```javascript
new Function ([arg1[, arg2[, ...argN]],] functionBody)
```

| 参数 | 说明 |
| :-- | :-- |
| `arg1, arg2, ... argN` | 被函数使用的参数的名称必须是合法命名的。参数名称是一个有效的JavaScript标识符的字符串，或者一个用逗号分隔的有效字符串的列表;例如“`×`”，“`theValue`”，或“`a,b`”。|
| `functionBody` | 一个含有包括函数定义的 JavaScript 语句的**字符串**。|

## 描述

使用 `Function` 构造器生成的 `Function` 对象是在函数创建时解析的。这比你使用函数声明或者函数表达式并在你的代码中调用更为低效，因为使用后者创建的函数是跟其他代码一起解析的。

所有被传递到构造函数中的参数，都将被视为将被创建的函数的参数，并且是相同的标示符名称和传递顺序。

以调用函数的方式调用 `Function` 的构造函数（而不是使用 `new` 关键字) 跟以构造函数来调用是一样的。

## 属性

### `Function.length`

`length` 属性指明函数的形参个数。

`length` 是函数对象的一个属性值，指该函数有多少个必须要传入的参数，即形参的个数。

形参的数量不包括剩余参数个数，仅包括第一个具有默认值之前的参数个数。

与之对比的是，`arguments.length` 是函数被调用时实际传参的个数。

**`Function` 构造器的属性**

`Function` 构造器本身也是个 `Function`。他的 `length` 属性值为 `1`。该属性 Writable: `false`, Enumerable: `false`,
Configurable: `true`.

**`Function` 对象的属性**

`Function`  对象的 `length` 属性值为 `0`

### `Function.name`

`function.name` 属性返回函数实例的名称。

## `Function.prototype`

**`Function.prototype`** 属性存储了 `Function` 的原型对象。

`Function` 对象继承自 `Function.prototype` 属性。因此，`Function.prototype` 不能被修改。

## 示例

### 传入参数调用 `Function` 构造函数

下面的代码会创建一个需要两个参数的 `Function` 对象。

```javascript
// 可以直接在 JavaScript 控制台中运行

// 创建了一个能返回两个参数和的函数
const adder = new Function("a", "b", "return a + b");

// 调用函数
adder(2, 6);
// > 8
```

参数 "`a`" 和 "`b`" 是参数的名字，在函数体中被使用，"`return a + b`"。

### `Function` 构造器与函数声明之间的不同

使用 `Function` 构造函数创建的函数不会创建其创建上下文的闭包。 它们总是在全局范围内创建。 运行它们时，它们将只能访问自己的局部变量和全局变量，而不能访问创建 `Function`
构造函数的作用域中的局部变量和全局变量。 这与对函数表达式使用带有代码的`eval`不同。

```javascript
var x = 10;

function createFunction1() {
    var x = 20;
    return new Function('return x;'); // 这里的 x 指向最上面全局作用域内的 x
}

function createFunction2() {
    var x = 20;
    function f() {
        return x; // 这里的 x 指向上方本地作用域内的 x
    }
    return f;
}

var f1 = createFunction1();
console.log(f1());          // 10
var f2 = createFunction2();
console.log(f2());          // 20
```

虽然这段代码可以在浏览器中正常运行，但在 Node.js 中，`f1()` 会产生一个 `ReferenceError`，因为找不到变量 `x`。这是因为，在 Node 中，
顶级作用域不是全局作用域，而 `x` 其实是在模块的作用域之中。

```javascript
console.log(Function.length); /* 1 */

console.log((function()        {}).length); /* 0 */
console.log((function(a)       {}).length); /* 1 */
console.log((function(a, b)    {}).length); /* 2 etc. */

console.log((function(...args) {}).length);
// 0, rest parameter is not counted

console.log((function(a, b = 1, c) {}).length);
// 1, only parameters before the first one with
// a default value is counted
```

### 函数声明的名称

`name` 属性返回一个函数声明的名称。

```javascript
function doSomething() { }
doSomething.name;  // "doSomething"
```

### 构造函数的名称

使用`new Function(...)`语法创建的函数或只是 `Function(...) create` `Function`对象及其名称为“anonymous”。

```javascript
(new Function).name; // "anonymous"
```

### 推断函数名称

变量和方法可以从句法位置推断匿名函数的名称（ECMAScript 2015中新增）。

```javascript
var f = function() {};
var object = {
  someMethod: function() {}
};

console.log(f.name); // "f"
console.log(object.someMethod.name); // "someMethod"
```

你可以在 函数表达式中定义函数的名称:

```javascript
var object = {
  someMethod: function object_someMethod() {}
};

console.log(object.someMethod.name); // "object_someMethod"

try { object_someMethod } catch(e) { alert(e); }
// ReferenceError: object_someMethod is not defined
```

你不能更改函数的名称，此属性是只读的：

```javascript
var object = {
  // anonymous
  someMethod: function() {}
};

object.someMethod.name = 'otherMethod';
console.log(object.someMethod.name); // someMethod
```

要更改它，可以使用[`Object.defineProperty()`](/zh-hans/webfrontend/Object.defineProperty)。

### 简写方法的名称

```javascript
var o = {
  foo(){}
};
o.foo.name; // "foo";
```

### 绑定函数的名称

[`Function.bind()`](/zh-hans/webfrontend/Function.bind) 所创建的函数将会在函数的名称前加上"bound " 。

```javascript
function foo() {};
foo.bind({}).name; // "bound foo"
```

### `getters` 和 `setters` 的函数名

当通过 `get` 和 `set` 访问器来存取属性时, "get" 或 "set" 会出现在函数名称前。

```javascript
var o = {
  get foo(){},
  set foo(x){}
};

var descriptor = Object.getOwnPropertyDescriptor(o, "foo");
descriptor.get.name; // "get foo"
descriptor.set.name; // "set foo";
```

### 类中的函数名称

你可以使用`obj.constructor.name`来检查对象的“类”（但请务必阅读以下警告）：

```javascript
function Foo() {}  // ES2015 Syntax: class Foo {}

var fooInstance = new Foo();
console.log(fooInstance.constructor.name); // logs "Foo"
```

!!! error "警告"
    脚本解释器只有在函数没有名为name的属性时才会设置内置的`Function.name`属性
    （参见 [9.2.11 of the ECMAScript2015 Language Specification](https://www.ecma-international.org/ecma-262/6.0/#sec-setfunctionname)）。
    但是，ES2015规定由关键字static修饰的静态方法也会被认为是类的属性（ECMAScript2015, [14.5.14.21.b](https://www.ecma-international.org/ecma-262/6.0/#sec-runtime-semantics-classdefinitionevaluation)
    + [12.2.6.9](https://www.ecma-international.org/ecma-262/6.0/#sec-object-initializer-runtime-semantics-propertydefinitionevaluation)）。

因此，我们无法获取具有静态方法属性`name()`的几乎任何类的类名称：

```javascript
class Foo {
  constructor() {}
  static name() {}
}
```

使用`static name()`方法`Foo.name`不再保存实际的类名称，而是引用`name()`函数对象。 ES2015语法中的上述类定义将在Chrome或Firefox中运行，类似于ES5语法中的以下代码段：

```javascript
function Foo() {}
Object.defineProperty(Foo, 'name', { writable: true });
Foo.name = function() {};
```

通过`fooInstance.constructor.name`获取`fooInstance`类不会给我们所有的类名，而是静态类方法的引用。 例如：

```javascript
var fooInstance = new Foo();
console.log(fooInstance.constructor.name); // logs function name()
```

你也可以从ES5语法示例中看到，在Chrome或Firefox的中静态定义的`Foo.name`变得可写。内置定义在没有自定义静态定义时是只读的：

```javascript
Foo.name = 'Hello';
console.log(Foo.name);
//如果Foo具有静态name()属性，则输出“Hello”，否则为“Foo”
```

因此，你不能依赖内置的`Function.name`属性来保持一个类的名称。

### Symbol作为函数名称

如果`Symbol` 被用于函数名称，并且这个`symbol`具有相应的描述符，那么方法的名字就是方括号中的描述符。

```javascript
var sym1 = Symbol("foo");
var sym2 = Symbol();
var o = {
  [sym1]: function(){},
  [sym2]: function(){}
};

o[sym1].name; // "[foo]"
o[sym2].name; // ""
```
