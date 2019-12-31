TOPICS: Function.apply
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Function.apply()`

The **`apply()`** method calls a function with a given `this` value, and `arguments` provided as an
array (or an array-like object).

!!! warn "Note"
    While the syntax of this function is almost identical to that of
    [`call()`](/en/webfrontend/Function.call), the fundamental difference is that
    [`call()`](/en/webfrontend/Function.call) accepts an **argument list**, while `apply()`
    accepts a **single array of arguments**.

!!! warn "Note"
    When the first argument is undefined or null a similar outcome can be achieved using
    the array spread syntax.

## Syntax

```javascript
function.apply(thisArg, [argsArray])
```

| parameter | Description |
| :-- | :-- |
| `thisArg` | The value of `this` provided for the `call` to `func`. Note that `this` may not be the actual value seen by the method: if the method is a function in non-strict mode code, `null` and `undefined` will be replaced with the global object, and primitive values will be boxed. This argument is not optional |
| `argsArray` | Optional. An array-like object, specifying the arguments with which `func` should be called, or `null` or `undefined` if no arguments should be provided to the function. Starting with ECMAScript 5 these arguments can be a generic array-like object instead of an array. See below for browser compatibility information. |

**Return value**: The result of calling the function with the specified **`this`** value and arguments.

## Description

You can assign a different `this` object when calling an existing function. `this` refers to the
current object, the calling object. With `apply`, you can write a method once and then inherit it
in another object, without having to rewrite the method for the new object.

`apply` is very similar to [`call()`](/en/webfrontend/Function.call), except for the type of
arguments it supports. You use an arguments array instead of a list of arguments (parameters).
With `apply`, you can also use an array literal, for example, `func.apply(this, ['eat', 'bananas'])`,
or an [`Array`](/en/webfrontend/Array) object, for example, `func.apply(this, new Array('eat', 'bananas'))`.

You can also use `arguments` for the `argsArray` parameter. `arguments` is a local variable of a
function. It can be used for all unspecified arguments of the called object. Thus, you do not have
to know the arguments of the called object when you use the `apply` method. You can use
`arguments` to pass all the arguments to the called object. The called object is then
responsible for handling the arguments.

Since ECMAScript 5th Edition you can also use any kind of object which is array-like, so in
practice, this means it's going to have a property `length` and integer properties in the range
(`0..length-1`). As an example you can now use a `NodeList` or a custom object like
`{ 'length': 2, '0': 'eat', '1': 'bananas' }`.

!!! warn ""
    Many older browsers, including Chrome <17 and Internet Explorer <9, don't accept array-like
    objects and will throw an exception.

## Examples

### Using `apply` to append an array to another

We can use `push` to append an element to an array. And, because `push` accepts a variable number of
arguments, we can also `push` multiple elements at once. But, if we pass an array to `push`,
it will actually add that array as a single element, instead of adding the elements individually,
so we end up with an array inside an array. What if that is not what we want? concat does have the
behaviour we want in this case, but it does not actually append to the existing array but creates
and returns a new array. But we wanted to append to our existing array... So what now? Write a
loop? Surely not?

`apply` to the rescue!

```javascript
var array = ['a', 'b'];
var elements = [0, 1, 2];
array.push.apply(array, elements);
console.info(array); // ["a", "b", 0, 1, 2]
```

### Using `apply` and built-in functions

Clever usage of `apply` allows you to use built-in functions for some tasks, that otherwise
probably would have been written by looping over the array values. As an example here we are going
to use `Math.max/Math.min`, to find out the `maximum/minimum` value in an array.

```javascript
// min/max number in an array
var numbers = [5, 6, 2, 3, 7];

// using Math.min/Math.max apply
var max = Math.max.apply(null, numbers);
// This about equal to Math.max(numbers[0], ...)
// or Math.max(5, 6, ...)

var min = Math.min.apply(null, numbers);

// vs. simple loop based algorithm
max = -Infinity, min = +Infinity;

for (var i = 0; i < numbers.length; i++) {
  if (numbers[i] > max) {
    max = numbers[i];
  }
  if (numbers[i] < min) {
    min = numbers[i];
  }
}
```

But beware: in using `apply` this way, you run the risk of exceeding the JavaScript engine's
argument length limit. The consequences of applying a function with too many arguments (think more
than tens of thousands of arguments) vary across engines (JavaScriptCore has hard-coded argument
limit of 65536), because the limit (indeed even the nature of any excessively-large-stack behavior)
is unspecified. Some engines will throw an exception. More perniciously, others will arbitrarily
limit the number of arguments actually passed to the applied function. To illustrate this latter
case: if such an engine had a limit of four arguments (actual limits are of course significantly
higher), it would be as if the arguments `5, 6, 2, 3` had been passed to apply in the examples above,
rather than the full `array`.

If your value `array` might grow into the tens of thousands, use a hybrid strategy: `apply` your
function to chunks of the array at a time:

```javascript
function minOfArray(arr) {
  var min = Infinity;
  var QUANTUM = 32768;

  for (var i = 0, len = arr.length; i < len; i += QUANTUM) {
    var submin = Math.min.apply(null,
                                arr.slice(i, Math.min(i+QUANTUM, len)));
    min = Math.min(submin, min);
  }

  return min;
}

var min = minOfArray([5, 6, 2, 3, 7]);
```

### Using apply to chain constructors

You can use `apply` to chain constructors for an object, similar to Java. In the following example
we will create a global `Function` method called `construct`, which will enable you to use an
array-like object with a constructor instead of an arguments list.

```javascript
Function.prototype.construct = function(aArgs) {
  var oNew = Object.create(this.prototype);
  this.apply(oNew, aArgs);
  return oNew;
};
```

!!! warn "Note"
    The [`Object.create()`](/en/webfrontend/Object.create) method used above is relatively new.
    For alternative methods, please consider one of the following approaches:
    Using `Object.__proto__`:

```javascript
Function.prototype.construct = function (aArgs) {
  var oNew = {};
  oNew.__proto__ = this.prototype;
  this.apply(oNew, aArgs);
  return oNew;
};
```

Using closures:

```javascript
Function.prototype.construct = function(aArgs) {
  var fConstructor = this, fNewConstr = function() {
    fConstructor.apply(this, aArgs);
  };
  fNewConstr.prototype = fConstructor.prototype;
  return new fNewConstr();
};
Using the Function constructor:

Function.prototype.construct = function (aArgs) {
  var fNewConstr = new Function("");
  fNewConstr.prototype = this.prototype;
  var oNew = new fNewConstr();
  this.apply(oNew, aArgs);
  return oNew;
};
```

Example usage:

```javascript
function MyConstructor() {
  for (var nProp = 0; nProp < arguments.length; nProp++) {
    this['property' + nProp] = arguments[nProp];
  }
}

var myArray = [4, 'Hello world!', false];
var myInstance = MyConstructor.construct(myArray);

console.log(myInstance.property1);                // logs 'Hello world!'
console.log(myInstance instanceof MyConstructor); // logs 'true'
console.log(myInstance.constructor);              // logs 'MyConstructor'
```

!!! warn "Note"
    This non-native `Function.construct` method will not work with some native constructors; like [`Date`](/en/webfrontend/Date),
    for example. In these cases you have to use the [`Function.bind`](/en/webfrontend/Function.bind)
    method. For example, imagine having an array like the following, to be used with [`Date`](/en/webfrontend/Date)
    constructor: `[2012, 11, 4]`; in this case you have to write something like:
    `new (Function.prototype.bind.apply(Date, [null].concat([2012, 11, 4])))()`. This is not the
    best way to do things, and probably not to be used in any production environment.
