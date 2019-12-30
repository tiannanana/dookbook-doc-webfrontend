TOPICS: Object
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript `Object` Object

The **`Object`** constructor creates an object wrapper.

## Syntax

```javascript
// Object initialiser or literal
{ [ nameValuePair1[, nameValuePair2[, ...nameValuePairN] ] ] }

// Called as a constructor
new Object([value])
```

| parameter | Description |
| :-- | :-- |
| `nameValuePair1, nameValuePair2, ... nameValuePairN` | Pairs of names (strings) and values (any value) where the name is separated from the value by a colon. |
| `value` | Any value. |

## Description

The `Object` constructor creates an **object** wrapper for the given value.

- If the value is [`null`](/en/webfrontend/null) or [`undefined`](/en/webfrontend/undefined),
it will create and return an empty object.
- Otherwise, it will return an object of a Type that corresponds to the given value.
- If the value is an object already, it will return the value.

When called in a non-constructor context, `Object` behaves identically to `new Object()`.

## Deleting a property from an object

There isn't any method in an **Object** itself to `delete` its own properties (such as [`Map.delete()`](/en/webfrontend/Map.delete)).
To do so, one must use the [delete operator](/en/webfrontend/delete_operator).

## `Object.prototype`

The **`Object.prototype`** is a property of the `Object`
constructor. It is also the end of a prototype chain.

Nearly all objects in JavaScript are instances of `Object`; a typical object inherits properties
(including methods) from `Object.prototype`, although these properties may be
shadowed (a.k.a. overridden). However, an `Object` may be deliberately created for which this
is not true (e.g. by [`Object.create(null)`](/en/webfrontend/Object.create)), or it may be altered
so that this is no longer true (e.g. with [`Object.setPrototypeOf`](/en/webfrontend/Object.setPrototypeOf)).

Changes to the `Object` prototype object are seen by **all** objects through prototype chaining,
unless the properties and methods subject to those changes are overridden further along the
prototype chain. This provides a very powerful although potentially dangerous mechanism to
override or extend object behavior.

When altering the behavior of existing [`Object.methods`](/en/webfrontend/Object.methods),
consider injecting code by wrapping your extension before or after the existing logic. For example,
this (untested) code will pre-conditionally execute custom logic before the built-in logic or
someone else's extension is executed.

When a function is called, the arguments to the call are held in the array-like "variable"
arguments. For example, in the call "`myFn(a, b, c)`", the arguments within myFn's body will contain
3 array-like elements corresponding to (a, b, c). When modifying prototypes with hooks, simply pass
this & the arguments (the call state) to the current behavior by calling `apply()` on the function.
This pattern can be used for any prototype, such as [`Node.prototype`](/en/webfrontend/Node.prototype),
[`Function.prototype`](/en/webfrontend/Function.prototype), etc.

```javascript
var current = Object.prototype.valueOf;

// Since my property "-prop-value" is cross-cutting and isn't always
// on the same prototype chain, I want to modify Object.prototype:
Object.prototype.valueOf = function() {
  if (this.hasOwnProperty('-prop-value')) {
    return this['-prop-value'];
  } else {
    // It doesn't look like one of my objects, so let's fall back on
    // the default behavior by reproducing the current behavior as best we can.
    // The apply behaves like "super" in some other languages.
    // Even though valueOf() doesn't take arguments, some other hook may.
    return current.apply(this, arguments);
  }
}
```

Since JavaScript doesn't exactly have sub-class objects, prototype is a useful workaround to make
a “base class” object of certain functions that act as `objects`. For example:

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
Employee.prototype.constructor = Employee; //If you don't set Object.prototype.constructor to Employee,
                                           //it will take prototype.constructor of Person (parent).
                                           //To avoid that, we set the prototype.constructor to Employee (child).


Employee.prototype.greet = function() {
  if (this.canTalk) {
    console.log('Hi, I am ' + this.name + ', the ' + this.title);
  }
};

var Customer = function(name) {
  Person.call(this, name);
};

Customer.prototype = Object.create(Person.prototype);
Customer.prototype.constructor = Customer; //If you don't set Object.prototype.constructor to Customer,
                                           //it will take prototype.constructor of Person (parent).
                                           //To avoid that, we set the prototype.constructor to Customer (child).


var Mime = function(name) {
  Person.call(this, name);
  this.canTalk = false;
};

Mime.prototype = Object.create(Person.prototype);
Mime.prototype.constructor = Mime; //If you don't set Object.prototype.constructor to Mime,
                                   //it will take prototype.constructor of Person (parent).
                                   //To avoid that, we set the prototype.constructor to Mime (child).


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

## Examples

### Using `Object` given `undefined` and `null` types

The following examples store an empty `Object` object in `o`:

```javascript
let o = new Object()
```

```javascript
let o = new Object(undefined)
```

```javascript
let o = new Object(null)
```

### Using Object to create Boolean objects

The following examples store [`Boolean`](/en/webfrontend/Boolean) objects in `o`:

```javascript
// equivalent to o = new Boolean(true)
let o = new Object(true)
```

```javascript
// equivalent to o = new Boolean(false)
let o = new Object(Boolean())
```
