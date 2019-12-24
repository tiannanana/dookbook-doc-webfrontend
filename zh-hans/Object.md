TOPICS: Object
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Object 对象: `Object`

**`Object`** 构造函数创建一个对象包装器。

## 语法

```javascript
// 对象初始化器（Object initialiser）或对象字面量（literal）
{ [ nameValuePair1[, nameValuePair2[, ...nameValuePairN] ] ] }

// 以构造函数形式来调用
new Object([value])
```

| 参数 | 说明 |
| :-- | :-- |
| `nameValuePair1, nameValuePair2, ... nameValuePairN` | 成对的名称（字符串）与值（任何值），其中名称通过冒号与值分隔。 |
| `value` | 任何值。 |

## 描述

`Object` 构造函数为给定值创建一个对象包装器。如果给定值是 [`null`](/zh-hans/webfrontend/null) 或 [`undefined`](/zh-hans/webfrontend/undefined)，将会创建并返回一个空对象，否则，将返回一个与给定值对应类型的对象。

当以非构造函数形式被调用时，`Object` 等同于 `new Object()`。

## `Object.prototype`

**`Object.prototype`** 属性表示 `Object` 的原型对象。

几乎所有的 JavaScript 对象都是 `Object` 的实例；一个典型的对象继承了`Object.prototype`的属性（包括方法），尽管这些属性可能被遮蔽（亦称为覆盖）。但是有时候可能故意创建不具有典型原型链继承的对象，比如通过[`Object.create(null)`](/zh-hans/webfrontend/Object.create)创建的对象，或者通过[`Object.setPrototypeOf`](/zh-hans/webfrontend/Object.setPrototypeOf)方法改变原型链。

改变`Object`原型，会通过原型链改变所有对象；除非在原型链中进一步覆盖受这些变化影响的属性和方法。这提供了一个非常强大的、但有潜在危险的机制来覆盖或扩展对象行为。

当改变现有的 `Object.method`(方法)的行为时，考虑在现有逻辑之前或之后通过封装你的扩展来注入代码。例如,此(未测试的)代码将在内置逻辑或其他人的扩展执行之前 **pre-conditionally**（预条件地）执行自定义逻辑。

当一个函数被调用时,调用的参数被保留在类似数组 **"变量"** 的参数中。例如, 在调用 "`myFn(a、b、c)`"时, 在`myFn`的主体内的参数将包含 3个类似数组的元素对应于 `(a、b、c)`。
使用钩子修改原型时,只需通过调用该函数的 [`apply()`](/zh-hans/webfrontend/Function.apply)，将 `this` 与参数 (调用状态) 传递给当前行为。
这种模式可以用于任何原型，如 [`Node.prototype`](/zh-hans/webfrontend/Node.prototype)、
[`Function.prototype`](/zh-hans/webfrontend/Function.prototype) 等.

```javascript
var current = Object.prototype.valueOf;

// 由于我的属性 "-prop-value"是交叉性的, 并不总是
// 在同一个原型链上，我想要修改 Object.prototype:
Object.prototype.valueOf = function() {
  if (this.hasOwnProperty('-prop-value')) {
    return this['-prop-value'];
  } else {
    // 它看起来不像我的对象之一，因此，让我们退回到
    // 默认行为，通过尽可能地复制当前行为来实现.
    // 此apply的行为类似于其他语言中的"super".
    // 即使 valueOf() 不带参数, 其他的钩子可能会带有.
    return current.apply(this, arguments);
  }
}
```

由于 JavaScript 并不完全具有子类对象, 所以原型是一种有用的变通方法, 可以使用某些函数的 **"基类"** 对象来充当对象。例如:

```javascript
var Person = function(name) {
  this.name = name;
  this.canTalk = true;
};

Person.prototype.greet = function() {
  if (this.canTalk) {
    console.log('Hi, I am ' + this.name);
  }
};

var Employee = function(name, title) {
  Person.call(this, name);
  this.title = title;
};

Employee.prototype = Object.create(Person.prototype);

Employee.prototype.greet = function() {
  if (this.canTalk) {
    console.log('Hi, I am ' + this.name + ', the ' + this.title);
  }
};

var Customer = function(name) {
  Person.call(this, name);
};

Customer.prototype = Object.create(Person.prototype);

var Mime = function(name) {
  Person.call(this, name);
  this.canTalk = false;
};

Mime.prototype = Object.create(Person.prototype);

var bob = new Employee('Bob', 'Builder');
var joe = new Customer('Joe');
var rg = new Employee('Red Green', 'Handyman');
var mike = new Customer('Mike');
var mime = new Mime('Mime');

bob.greet();
// Hi, I am Bob, the Builder

joe.greet();
// Hi, I am Joe

rg.greet();
// Hi, I am Red Green, the Handyman

mike.greet();
// Hi, I am Mike

mime.greet();
```

## 示例

### 给定 `undefined` 和 `null` 类型使用 `Object`

下面的例子将一个空的 `Object` 对象存到 `o` 中：

```javascript
var o = new Object();
```

```javascript
var o = new Object(undefined);
```

```javascript
var o = new Object(null);
```

### 使用 `Object` 生成布尔对象

下面的例子将 [`Boolean`](/zh-hans/webfrontend/Boolean) 对象存到 `o` 中：

```javascript
// 等价于 o = new Boolean(true);
var o = new Object(true);
```

```javascript
// 等价于 o = new Boolean(false);
var o = new Object(Boolean());
```
