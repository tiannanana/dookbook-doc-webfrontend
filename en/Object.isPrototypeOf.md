TOPICS: Object.isPrototypeOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.isPrototypeOf()`

The **`isPrototypeOf()`** method checks if an object exists in another object's prototype chain.

!!! warn ""
    `isPrototypeOf()` differs from the `instanceof` operator. In the expression
    "`object instanceof AFunction`", the `object` prototype chain is checked against
    `AFunction.prototype`, not against `AFunction` itself.

## Syntax

```javascript
prototypeObj.isPrototypeOf(object)
```

| parameter | Description |
| :-- | :-- |
| `object` | The object whose prototype chain will be searched. |

**Return value**: A `Boolean` indicating whether the calling object lies in the prototype chain
of the specified object.

### Errors thrown

|  |  |
| :-- | :-- |
| `TypeError` | A `TypeError` is thrown if prototypeObj is `undefined` or `null`.

## Description

The `isPrototypeOf()` method allows you to check whether or not an object exists within
another object's prototype chain.

## Examples

This example demonstrates that `Baz.prototype`, `Bar.prototype`, `Foo.prototype` and
`Object.prototype` exist in the prototype chain for object `baz`:

```javascript
function Foo() {}
function Bar() {}
function Baz() {}

Bar.prototype = Object.create(Foo.prototype);
Baz.prototype = Object.create(Bar.prototype);

var baz = new Baz();

console.log(Baz.prototype.isPrototypeOf(baz)); // true
console.log(Bar.prototype.isPrototypeOf(baz)); // true
console.log(Foo.prototype.isPrototypeOf(baz)); // true
console.log(Object.prototype.isPrototypeOf(baz)); // true
```

`isPrototypeOf()` method, along with the `instanceof` operator particularly comes in handy if you
have code that can only function when dealing with objects descended from a specific prototype chain,
e.g., to guarantee that certain methods or properties will be present on that object.

For example, check if `baz` object descends from `Foo.prototype`:

```javascript
if (Foo.prototype.isPrototypeOf(baz)) {
  // do something safe
}
```
