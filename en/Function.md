TOPICS: Function
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Function Object

The `Function` constructor creates a new `Function` **object**. Calling the constructor directly
can create functions dynamically, but suffers from security and similar (but far less significant)
performance issues to `eval`. However, unlike eval, the Function constructor creates functions which
execute in the global scope only.

Every JavaScript function is actually a `Function` object. This can be seen with the code
`(function(){}).constructor === Function` which returns true.

## Syntax

```javascript
new Function ([arg1[, arg2[, ...argN]],] functionBody)
```

| parameter | Description |
| :-- | :-- |
| `arg1, arg2, ... argN` | Names to be used by the function as formal argument names. Each must be a string that corresponds to a valid JavaScript identifier or a list of such strings separated with a comma; for example "`x`", "`theValue`", or "`a,b`". |
| `functionBody` | A string containing the JavaScript statements comprising the function definition. |

## Description

`Function` objects created with the `Function` constructor are parsed when the function is created.
This is less efficient than declaring a function with a function expression or function statement
and calling it within your code because such functions are parsed with the rest of the code.

All arguments passed to the function are treated as the names of the identifiers of the parameters
in the function to be created, in the order in which they are passed. Omitting an argument will
result in the value of that parameter being `undefined`.

Invoking the `Function` constructor as a function (without using the new operator) has the same
effect as invoking it as a constructor.

## 属性

### `Function.length`

The `length` property indicates the number of parameters expected by the function.

`length` is a property of a function object, and indicates how many arguments the function expects,
i.e. the number of formal parameters. This number excludes the rest parameter and only includes
parameters before the first one with a default value. By contrast, `arguments.length` is local to
a function and provides the number of arguments actually passed to the function.

**Data property of the `Function` constructor**

The `Function` constructor is itself a `Function` object. Its `length` data property has a value of
`1`. The property attributes are: Writable: `false`, Enumerable: `false`, Configurable: `true`.

**Property of the `Function` prototype object**

The `length` property of the `Function` prototype object has a value of `0`.

### `Function.name`

A `Function` object's read-only **`name`** property indicates the function's name as specified when
it was created, or it may be rather `anonymous` or `''`(an empty string) for functions created anonymously.

## `Function.prototype`

The **`Function.prototype`** property represents the Function prototype object.

`Function` objects inherit from `Function.prototype`.  `Function.prototype` cannot be modified.

## 示例

### Specifying arguments with the Function constructor

The following code creates a `Function` object that takes two arguments.

```javascript
// 可以直接在 JavaScript 控制台中运行

// 创建了一个能返回两个参数和的函数
const adder = new Function("a", "b", "return a + b");

// 调用函数
adder(2, 6);
// > 8
```

The arguments "`a`" and "`b`" are formal argument names that are used in the function body,
"`return a + b`".

### Difference between `Function` constructor and function declaration

Functions created with the `Function` constructor do not create closures to their creation contexts;
they always are created in the global scope. When running them, they will only be able to access
their own local variables and global ones, not the ones from the scope in which the `Function`
constructor was created. This is different from using `eval` with code for a function expression.

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

While this code works in web browsers, `f1()` will produce a `ReferenceError` in Node.js, as `x`
will not be found. This is because the top-level scope in Node is not the global scope, and `x`
will be local to the module.

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

### Function statement name

The `name` property returns the name of a function statement.

```javascript
function doSomething() { }
doSomething.name;  // "doSomething"
```

### Function constructor name

Functions created with the syntax `new Function(...)` or just `Function(...)` create `Function`
objects and their name is "anonymous".

```javascript
(new Function).name; // "anonymous"
```

### Anonymous function expression

Anonymous function expressions that were created using the keyword `function` or arrow functions
would have `""`(an empty string) as their name.

```javascript
(function() {}).name; // ""
(() => {}).name; // ""
```

### Inferred function names

Variables and methods can infer the name of an anonymous function from its syntactic position
(new in ECMAScript 2015).

```javascript
let f = function() {};
let object = {
  someMethod: function() {}
};

console.log(f.name); // "f"
console.log(object.someMethod.name); // "someMethod"
```

You can define a function with a name in a function expression:

```javascript
let object = {
  someMethod: function object_someMethod() {}
};
console.log(object.someMethod.name); // logs "object_someMethod"

try { object_someMethod } catch(e) { console.log(e); }
// ReferenceError: object_someMethod is not defined
```

The name property is read-only and cannot be changed by the assigner operator:

```javascript
let object = {
  // anonymous
  someMethod: function() {}
};

object.someMethod.name = 'otherMethod';
console.log(object.someMethod.name); // someMethod
```

To change it, use [`Object.defineProperty()`](/en/webfrontend/Object.defineProperty).

### Shorthand method names

```javascript
var o = {
  foo(){}
};
o.foo.name; // "foo";
```

### Bound function names

[`Function.bind()`](/en/webfrontend/Function.bind) produces a function whose name is
"bound " plus the function name.

```javascript
function foo() {};
foo.bind({}).name; // "bound foo"
```

### Function names for getters and setters

When using `get` and `set` accessor properties, "get" or "set" will appear in the function name.

```javascript
let o = {
  get foo(){},
  set foo(x){}
};

var descriptor = Object.getOwnPropertyDescriptor(o, "foo");
descriptor.get.name; // "get foo"
descriptor.set.name; // "set foo";
```

### Function names in classes

You can use `obj.constructor.name` to check the "class" of an object
(but be sure to read the warnings below):

```javascript
function Foo() {}  // ES2015 Syntax: class Foo {}

var fooInstance = new Foo();
console.log(fooInstance.constructor.name); // logs "Foo"
```

!!! error "Warning"
    The script interpreter will set the built-in `Function.name` property only if a function does
    not have an own property called name (see section [9.2.11 of the ECMAScript2015 Language Specification](https://www.ecma-international.org/ecma-262/6.0/#sec-setfunctionname)).
    However, ES2015 specifies the static keyword such that static methods will be set as OwnProperty
    of the class constructor function (ECMAScript2015, [14.5.14.21.b](https://www.ecma-international.org/ecma-262/6.0/#sec-runtime-semantics-classdefinitionevaluation)
    + [12.2.6.9](https://www.ecma-international.org/ecma-262/6.0/#sec-object-initializer-runtime-semantics-propertydefinitionevaluation)).

Therefore we can't obtain the class name for virtually any class with a static method property name():

```javascript
class Foo {
  constructor() {}
  static name() {}
}
```

With a `static name()` method `Foo.name` no longer holds the actual class name but a reference to
the `name()` function object. Above class definition in ES2015 syntax will behave in Chrome or
Firefox similar to the following snippet in ES5 syntax:

```javascript
function Foo() {}
Object.defineProperty(Foo, 'name', { writable: true });
Foo.name = function() {};
```

Trying to obtain the class of `fooInstance` via `fooInstance.constructor.name` won't give us the
class name at all but a reference to the static class method. Example:

```javascript
let fooInstance = new Foo();
console.log(fooInstance.constructor.name); // logs function name()
```

You may also see from the ES5 syntax example that in Chrome or Firefox our static definition of
`Foo.name` becomes writable. The built-in definition in the absence of a custom static definition
is read-only:

```javascript
Foo.name = 'Hello';
console.log(Foo.name);
//如果Foo具有静态name()属性，则输出“Hello”，否则为“Foo”
```

Therefore you may not rely on the built-in `Function.name` property to always hold a class's name.

### Symbols as function names

If a `Symbol` is used a function name and the symbol has a description, the method's name is
the description in square brackets.

```javascript
let sym1 = Symbol("foo");
let sym2 = Symbol();
let o = {
  [sym1]: function(){},
  [sym2]: function(){}
};

o[sym1].name; // "[foo]"
o[sym2].name; // ""
```
