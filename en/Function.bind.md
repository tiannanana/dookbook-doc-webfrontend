TOPICS: Function.bind
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Function.bind()`

The **`bind()`** method creates a new function that, when called, has its `this` keyword set to
the provided value, with a given sequence of arguments preceding any provided when the
new function is called.

## Syntax

```javascript
function.bind(thisArg[, arg1[, arg2[, ...]]])
```

| parameter | Description |
| :-- | :-- |
| `thisArg` | The value to be passed as the `this` parameter to the target function when the bound function is called. The value is ignored if the bound function is constructed using the `new` operator. When using `bind` to create a function(supplied as a callback) inside a `setTimeout`, any primitive value passed as `thisArg` is converted to object. If no arguments are provided to `bind`, the this of the executing scope is treated as the `thisArg` for the new function. |
| `arg1, arg2, ...` | Arguments to prepend to arguments provided to the bound function when invoking the target function. |

**Return value**: A copy of the given function with the specified `this` value and initial arguments.

## Description

The `bind()` function creates a new **bound function**, which is an exotic function object (a
term from ECMAScript 2015) that wraps the original function object. Calling the bound function
generally results in the execution of its wrapped function.

A bound function has the following internal properties:

- **`[[BoundTargetFunction]]`** - the wrapped function object;
- **`[[BoundThis]]`** - the value that is always passed as this value when calling the wrapped function.
- **`[[BoundArguments]]`** - a list of values whose elements are used as the first arguments to any
call to the wrapped function.
- **`[[Call]]`** - executes code associated with this object. Invoked via a function call expression.
The arguments to the internal method are a this value and a list containing the arguments passed to
the function by a call expression.

When a bound function is called, it calls internal method `[[Call]]` on `[[BoundTargetFunction]]`,
with following arguments `Call(boundThis, args)`. Where, `boundThis` is `[[BoundThis]]`, `args` is
`[[BoundArguments]]` followed by the arguments passed by the function call.

A bound function may also be constructed using the `new` operator: doing so acts as though the
target function had instead been constructed. The provided `this` value is ignored, while prepended
arguments are provided to the emulated function.

## Examples

### Creating a bound function

The simplest use of `bind()` is to make a function that, no matter how it is called, is called
with a particular `this` value. A common mistake for new JavaScript programmers is to extract a
method from an object, then to later call that function and expect it to use the original object as
its `this` (e.g. by using that method in callback-based code). Without special care, however, the
original object is usually lost. Creating a bound function from the function, using the original
object, neatly solves this problem:

```javascript
this.x = 9;    // this refers to global "window" object here in the browser
var module = {
  x: 81,
  getX: function() { return this.x; }
};

module.getX(); // 81

var retrieveX = module.getX;
retrieveX();
// returns 9 - The function gets invoked at the global scope

// Create a new function with 'this' bound to module
// New programmers might confuse the
// global var x with module's property x
var boundGetX = retrieveX.bind(module);
boundGetX(); // 81
```

### Partially applied functions

The next simplest use of `bind()` is to make a function with pre-specified initial arguments.
These arguments (if any) follow the provided `this` value and are then inserted at the start of
the arguments passed to the target function, followed by the arguments passed to the bound function,
whenever the bound function is called.

```javascript
function list() {
  return Array.prototype.slice.call(arguments);
}

function addArguments(arg1, arg2) {
    return arg1 + arg2
}

var list1 = list(1, 2, 3); // [1, 2, 3]

var result1 = addArguments(1, 2); // 3

// Create a function with a preset leading argument
var leadingThirtysevenList = list.bind(null, 37);

// Create a function with a preset first argument.
var addThirtySeven = addArguments.bind(null, 37);

var list2 = leadingThirtysevenList();
// [37]

var list3 = leadingThirtysevenList(1, 2, 3);
// [37, 1, 2, 3]

var result2 = addThirtySeven(5);
// 37 + 5 = 42

var result3 = addThirtySeven(5, 10);
// 37 + 5 = 42 , second argument is ignored
```

### With `setTimeout()`

By default within `window.setTimeout()`, the `this` keyword will be set to the `window` (or `global`)
object. When working with class methods that require `this` to refer to class instances, you may
explicitly bind `this` to the callback function, in order to maintain the instance.

```javascript
function LateBloomer() {
  this.petalCount = Math.floor(Math.random() * 12) + 1;
}

// Declare bloom after a delay of 1 second
LateBloomer.prototype.bloom = function() {
  window.setTimeout(this.declare.bind(this), 1000);
};

LateBloomer.prototype.declare = function() {
  console.log('I am a beautiful flower with ' +
    this.petalCount + ' petals!');
};

var flower = new LateBloomer();
flower.bloom();  
// after 1 second, triggers the 'declare' method
```

### Bound functions used as constructors

!!! error "Warning"
    This section demonstrates JavaScript capabilities and documents some edge cases of the `bind()`
    method. The methods shown below are not the best way to do things and probably should not be
    used in any production environment.

Bound functions are automatically suitable for use with the `new` operator to construct `new`
instances created by the target function. When a bound function is used to construct a value,
the provided `this` is ignored. However, provided arguments are still prepended to the constructor call:

```javascript
function Point(x, y) {
  this.x = x;
  this.y = y;
}

Point.prototype.toString = function() {
  return this.x + ',' + this.y;
};

var p = new Point(1, 2);
p.toString(); // '1,2'

// not supported in the polyfill below,

// works fine with native bind:

var YAxisPoint = Point.bind(null, 0/*x*/);


var emptyObj = {};
var YAxisPoint = Point.bind(emptyObj, 0/*x*/);

var axisPoint = new YAxisPoint(5);
axisPoint.toString(); // '0,5'

axisPoint instanceof Point; // true
axisPoint instanceof YAxisPoint; // true
new YAxisPoint(17, 42) instanceof Point; // true
```

Note that you need do nothing special to create a bound function for use with `new`. The corollary
is that you need do nothing special to create a bound function to be called plainly, even if you
would rather require the bound function to only be called using `new`.

```javascript
// Example can be run directly in your JavaScript console
// ...continuing from above

// Can still be called as a normal function
// (although usually this is undesired)
YAxisPoint(13);

emptyObj.x + ',' + emptyObj.y;
// >  '0,13'
```

If you wish to support the use of a bound function only using `new`, or only by calling it, the
target function must enforce that restriction.

### Creating shortcuts

`bind()` is also helpful in cases where you want to create a shortcut to a function which requires
a specific `this` value.

Take [`Array.slice`](/en/webfrontend/Array.slice), for example, which you want to use for converting
an array-like object to a real array. You could create a shortcut like this:

```javascript
var slice = Array.prototype.slice;

// ...

slice.apply(arguments);
```

With `bind()`, this can be simplified. In the following piece of code, `slice` is a bound function
to the [`apply()`](/en/webfrontend/Function.apply) function of `Function.prototype`, with the this
value set to the [`slice()`](/en/webfrontend/Array.slice) function of `Array.prototype`.
This means that additional [`apply()`](/en/webfrontend/Function.apply) calls can be eliminated:

```javascript
// same as "slice" in the previous example
var unboundSlice = Array.prototype.slice;
var slice = Function.prototype.apply.bind(unboundSlice);

// ...

slice(arguments);
```

## Polyfill

Because older browsers are generally also slower browsers, it is much more critical than most
people recognize to create performance polyfills to make the browsing experience in outdated browsers
slightly less horrible. Thus, presented below are two options for Function.prototype.bind polyfills.
The top first one is much smaller and more performant, but does not work when using the `new` operator.
The latter second one is less performant and bigger, but it permits some usage of the `new` operator
on bound functions. Generally, in most code it's very rare to see `new` used on a bound function,
so it is generally best to go with the first option.

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

You can partially work around this by inserting the following code at the beginning of your scripts,
allowing use of much of the functionality of `bind()` in implementations that do not
natively support it.

```javascript
// Yes, it does work with `new funcA.bind(thisArg, args)`
if (!Function.prototype.bind) (function(){
  var ArrayPrototypeSlice = Array.prototype.slice;
  Function.prototype.bind = function(otherThis) {
    if (typeof this !== 'function') {
      // closest thing possible to the ECMAScript 5
      // internal IsCallable function
      throw new TypeError('Function.prototype.bind - what is trying to be bound is not callable');
    }

    var baseArgs= ArrayPrototypeSlice .call(arguments, 1),
        baseArgsLength = baseArgs.length,
        fToBind = this,
        fNOP    = function() {},
        fBound  = function() {
          baseArgs.length = baseArgsLength; // reset to default base arguments
          baseArgs.push.apply(baseArgs, arguments);
          return fToBind.apply(
                 fNOP.prototype.isPrototypeOf(this) ? this : otherThis, baseArgs
          );
        };

    if (this.prototype) {
      // Function.prototype doesn't have a prototype property
      fNOP.prototype = this.prototype;
    }
    fBound.prototype = new fNOP();

    return fBound;
  };
})();
```

Some of the many differences (there may well be others, as this list does not seriously attempt to
be exhaustive) between this algorithm and the specified algorithm are:

- The partial implementation relies on [`Array.slice()`](/en/webfrontend/Array.slice),
[`Array.concat()`](/en/webfrontend/Array.concat), [`Function.call()`](/en/webfrontend/Function.call)
and [`Function.apply()`](/en/webfrontend/Function.apply), built-in methods to have their original values.
- The partial implementation creates functions that do not have immutable "poison pill" `caller`
and `arguments` properties that throw a `TypeError` upon get, set, or deletion. (This could be added
if the implementation supports [`Object.defineProperty`](/en/webfrontend/Object.defineProperty), or
partially implemented [without throw-on-delete behavior] if the implementation supports the
`__defineGetter__` and `__defineSetter__` extensions.)
- The partial implementation creates functions that have a `prototype` property.
(Proper bound functions have none.)
- The partial implementation creates bound functions whose `length` property does not agree with
that mandated by ECMA-262: it creates functions with `length` `0`, while a full implementation,
depending on the `length` of the target function and the number of pre-specified arguments, may
return a non-zero `length`.

If you choose to use this partial implementation, **you must not rely on those cases where behavior
deviates from ECMA-262, 5th edition!** Thankfully, these deviations from the specification do not
rarely (if ever) come up in most coding situations. If you do not understand any of the deviations
from the specification above, then it is safe in this particular case to not worry about these
noncompliant deviation details.

**If it's absolutely necessary and performance** is not a concern, a far slower (but more
specification compliant solution) can be found at [https://github.com/Raynos/function-bind](https://github.com/Raynos/function-bind).
