TOPICS: Function.bind
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Function.bind()`

**`bind()`** 方法创建一个新的函数，在 `bind()` 被调用时，这个新函数的`this`被`bind`的第一个参数指定，其余的参数将作为新函数的参数供调用时使用。

## 语法

```javascript
function.bind(thisArg[,arg1[,arg2[, ...]]])
```

| 参数 | 说明 |
| :-- | :-- |
| `thisArg` | 调用绑定函数时作为`this`参数传递给目标函数的值。 如果使用`new`运算符构造绑定函数，则忽略该值。当使用`bind`在`setTimeout`中创建一个函数（作为回调提供）时，作为`thisArg`传递的任何原始值都将转换为`object`。如果`bind`函数的参数列表为空，执行作用域的`this`将被视为新函数的`thisArg`。
| `arg1, arg2, ...` | 当目标函数被调用时，预先添加到绑定函数的参数列表中的参数。

**返回值**: 返回一个原函数的拷贝，并拥有指定的 **`this`** 值和初始参数。

## 描述

`bind()` 函数会创建一个新 **绑定函数（bound function，BF）**。绑定函数是一个 **exotic function object**
（怪异函数对象，**ECMAScript 2015** 中的术语），它包装了原函数对象。调用 **绑定函数** 通常会导致执行 **包装函数** 。

**绑定函数** 具有以下内部属性：

- **[[BoundTargetFunction]]** - 包装的函数对象
- **[[BoundThis]]** - 在调用包装函数时始终作为this值传递的值。
- **[[BoundArguments]]** - 列表，在对包装函数做任何调用都会优先用列表元素填充参数列表。
- **[[Call]]** - 执行与此对象关联的代码。通过函数调用表达式调用。内部方法的参数是一个this值和一个包含通过调用表达式传递给函数的参数的列表。

当调用绑定函数时，它调用 **[[BoundTargetFunction]]** 上的内部方法 **[[Call]]**，就像这样 **Call(boundThis, args)**。其中，
**boundThis** 是 **[[BoundThis]]**，**args** 是 **[[BoundArguments]]** 加上通过函数调用传入的参数列表。

绑定函数也可以使用`new`运算符构造，它会表现为目标函数已经被构建完毕了似的。提供的`this`值会被忽略，但前置参数仍会提供给模拟函数。

## 示例

### 创建绑定函数

`bind()` 最简单的用法是创建一个函数，不论怎么调用，这个函数都有同样的 `this` 值。JavaScript新手经常犯的一个错误是将一个方法从对象中拿出来，然后再调用，期望方法中的
`this` 是原来的对象（比如在回调中传入这个方法）。如果不做特殊处理的话，一般会丢失原来的对象。基于这个函数，用原始的对象创建一个绑定函数，巧妙地解决了这个问题：

```javascript
this.x = 9;    // 在浏览器中，this指向全局的 "window" 对象
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81

var retrieveX = module.getX;
retrieveX();
// 返回9 - 因为函数是在全局作用域中调用的

// 创建一个新函数，把 'this' 绑定到 module 对象
// 新手可能会将全局变量 x 与 module 的属性 x 混淆
var boundGetX = retrieveX.bind(module);
boundGetX(); // 81
```

### 偏函数

`bind()`的另一个最简单的用法是使一个函数拥有预设的初始参数。只要将这些参数（如果有的话）作为`bind()`的参数写在`this`后面。当绑定函数被调用时，这些参数会被插入到目标函数的参数列表的开始位置，传递给绑定函数的参数会跟在它们后面。

```javascript
function list() {
  return Array.slice.call(arguments);
}

function addArguments(arg1, arg2) {
    return arg1 + arg2
}

var list1 = list(1, 2, 3); // [1, 2, 3]

var result1 = addArguments(1, 2); // 3

// 创建一个函数，它拥有预设参数列表。
var leadingThirtysevenList = list.bind(null, 37);

// 创建一个函数，它拥有预设的第一个参数
var addThirtySeven = addArguments.bind(null, 37);

var list2 = leadingThirtysevenList();
// [37]

var list3 = leadingThirtysevenList(1, 2, 3);
// [37, 1, 2, 3]

var result2 = addThirtySeven(5);
// 37 + 5 = 42

var result3 = addThirtySeven(5, 10);
// 37 + 5 = 42 ，第二个参数被忽略
```

### 配合 `setTimeout`

在默认情况下，使用 `window.setTimeout()` 时，`this` 关键字会指向 `window` （或`global`）对象。当类的方法中需要 `this` 指向类的实例时，
你可能需要显式地把 `this` 绑定到回调函数，就不会丢失该实例的引用。

```javascript
function LateBloomer() {
  this.petalCount = Math.ceil(Math.random() * 12) + 1;
}

// 在 1 秒钟后声明 bloom
LateBloomer.bloom = function() {
  window.setTimeout(this.declare.bind(this), 1000);
};

LateBloomer.declare = function() {
  console.log('I am a beautiful flower with ' +
    this.petalCount + ' petals!');
};

var flower = new LateBloomer();
flower.bloom();  // 一秒钟后, 调用'declare'方法
```

### 作为构造函数使用的绑定函数

!!! error "警告"
    这部分演示了 JavaScript 的能力并且记录了 `bind()` 的超前用法。以下展示的方法并不是最佳的解决方案，且可能不应该用在任何生产环境中。

绑定函数自动适应于使用 `new` 操作符去构造一个由目标函数创建的新实例。当一个绑定函数是用来构建一个值的，原来提供的 `this` 就会被忽略。不过提供的参数列表仍然会插入到构造函数调用时的参数列表之前。

```javascript
function Point(x, y) {
  this.x = x;
  this.y = y;
}

Point.toString = function() {
  return this.x + ',' + this.y;
};

var p = new Point(1, 2);
p.toString(); // '1,2'

var emptyObj = {};
var YAxisPoint = Point.bind(emptyObj, 0/*x*/);

// 以下这行代码在 polyfill 不支持，
// 在原生的bind方法运行没问题:
//(译注：polyfill的bind方法如果加上把bind的第一个参数，即新绑定的this执行Object()来包装为对象，Object(null)则是{}，那么也可以支持)
var YAxisPoint = Point.bind(null, 0/*x*/);

var axisPoint = new YAxisPoint(5);
axisPoint.toString(); // '0,5'

axisPoint instanceof Point; // true
axisPoint instanceof YAxisPoint; // true
new YAxisPoint(17, 42) instanceof Point; // true
```

请注意，你不需要做特别的处理就可以用 `new` 操作符创建一个绑定函数。也就是说，你不需要做特别处理就可以创建一个可以被直接调用的绑定函数，即使你更希望绑定函数是用 `new` 操作符来调用。

```javascript
// 这个例子可以直接在你的 javascript 控制台运行
// ...接着上面的代码继续

// 仍然能作为一个普通函数来调用
// (即使通常来说这个不是被期望发生的)
YAxisPoint(13);

emptyObj.x + ',' + emptyObj.y;   //  '0,13'
```

如果你希望一个绑定函数要么只能用 `new` 操作符，要么只能直接调用，那你必须在目标函数上显式规定这个限制。

### 快捷调用

在你想要为一个需要特定的 **`this`** 值的函数创建一个捷径（shortcut）的时候，`bind()` 也很好用。

你可以用 [`Array.slice`](/zh-hans/webfrontend/Array.slice) 来将一个类似于数组的对象（array-like object）转换成一个真正的数组，就拿它来举例子吧。你可以简单地这样写：

```javascript
var slice = Array.slice;

// ...

slice.apply(arguments);
```

用 `bind()`可以使这个过程变得简单。在下面这段代码里面，`slice` 是 [`Function`](/zh-hans/webfrontend/Function) 的
[`apply()`](/zh-hans/webfrontend/Function.slice) 方法的绑定函数，并且将 `Array` 的
[`slice()`](/zh-hans/webfrontend/Array.slice) 方法作为 `this` 的值。这意味着我们压根儿用不着上面那个 `apply()`调用了。

```javascript
// 与前一段代码的 "slice" 效果相同
var unboundSlice = Array.slice;
var slice = Function.apply.bind(unboundSlice);

// ...

slice(arguments);
```

## Polyfill

你可以将这段代码插入到你的脚本开头，从而使你的 `bind()` 在没有内置实现支持的环境中也可以部分地使用`bind`。

```javascript
// Does not work with `new funcA.bind(thisArg, args)`
if (!Function.prototype.bind) (function(){
  var slice = Array.prototype.slice;
  Function.prototype.bind = function() {
    var thatFunc = this, thatArg = arguments[0];
    var args = slice.call(arguments, 1);
    if (typeof thatFunc !== 'function') {
      // closest thing possible to the ECMAScript 5
      // internal IsCallable function
      throw new TypeError('Function.prototype.bind - ' +
             'what is trying to be bound is not callable');
    }
    return function(){
      var funcArgs = args.concat(slice.call(arguments))
      return thatFunc.apply(thatArg, funcArgs);
    };
  };
})();
```

上述算法和实际的实现算法还有许多其他的不同 （尽管可能还有其他不同之处，却没有那个必要去穷尽）：

- 这部分实现依赖于[`Array.slice()`](/zh-hans/webfrontend/Array.slice)， [`Array.concat()`](/zh-hans/webfrontend/Array.concat)，
`Function.call()`这些原生方法。
- 这部分实现创建的函数并没有`caller` 以及会在 get，set或者deletion上抛出`TypeError`错误的 arguments 属性这两个不可改变的“毒药” 。
（假如环境支持[`Object.defineProperty()`](/zh-hans/webfrontend/Object.defineProperty)， 或者实现支持
`__defineGetter__` 和 `__defineSetter__` 扩展）
- 这部分实现创建的函数有 `prototype` 属性。（正确的绑定函数没有）
- 这部分实现创建的绑定函数所有的 `length` 属性并不是同ECMA-262标准一致的：它创建的函数的 `length` 是`0`，而在实际的实现中根据目标函数的
`length` 和预先指定的参数个数可能会返回非零的 `length`。

如果你选择使用这部分实现，**你不能依赖于那些与 ECMA-262, 5th edition 规定的行为偏离的例子**。在 `bind()` 函数被广泛支持之前，某些情况下（或者为了兼容某些特定需求对其做一些特定修改后）可以选择用这个实现作为过渡。

请访问 [https://github.com/Raynos/function-bind](https://github.com/Raynos/function-bind) 以查找更完整的解决方案！
