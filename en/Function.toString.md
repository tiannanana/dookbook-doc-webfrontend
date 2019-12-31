TOPICS: Function.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Function.toString()`

The **`toString()`** method returns a string representing the source code of the function.

## Syntax

```javascript
function.toString()
```

**parameter**: No parameters

**Return value**: A string representing the source code of the function.

## Description

The [`Function`](/en/webfrontend/Function) object overrides the `toString` method inherited from
[`Object`](/en/webfrontend/Object); it does not inherit [`Object.toString`](/en/webfrontend/Object.toString).
For user-defined [`Function`](/en/webfrontend/Function) objects, the `toString` method returns a
string containing the source text segment which was used to define the function.

JavaScript calls the `toString` method automatically when a [`Function`](/en/webfrontend/Function)
is to be represented as a text value, e.g. when a function is concatenated with a string.

The `toString()` method will throw a `TypeError` exception ("`Function.toString` called on
incompatible object"), if its `this` value object is not a `Function` object.

```javascript
Function.prototype.toString.call('foo'); // TypeError
```

If the `toString()` method is called on built-in function objects or a function created by [`Function.bind`](/en/webfrontend/Function.bind),
`toString()` returns a native function string which looks like

```javascript
"function () {\n    [native code]\n}"
```

If the `toString()` method is called on a function created by the `Function` constructor,
`toString()` returns the source code of a synthesized function declaration named "anonymous"
using the provided parameters and function body.

## Examples

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
