TOPICS: undefined

# JavaScript Undefined Primitive: `undefined`

`undefined` is a *primitive value* automatically assigned to variables that have just been declared,
or to formal arguments for which there are no actual arguments.

## Syntax

```javascript
undefined
```

## Description

`undefined` is a property of the **global object**; i.e., it is a variable in **global scope**.
The initial value of `undefined` is the primitive value `undefined`.

In modern browsers, `undefined` is a non-configurable, non-writable property per the ECMAScript 5
specification. Even when this is not the case, avoid overriding it.

A variable that has not been assigned a value is of type undefined. A method or statement also
returns `undefined` if the variable that is being evaluated does not have an assigned value.
A function returns `undefined` if a value was not returned.

## Strict Equality and `undefined`

You can use `undefined` and the strict equality and inequality operators to determine whether a
variable has a value. In the following code, the variable `x` is not initialized, and the `if` statement
evaluates to `true`.

```javascript
var x;
if (x === undefined) {
   // these statements execute
}
else {
   // these statements do not execute
}
```

## `typeof` operator and `undefined`

Alternatively, `typeof` can be used:

```javascript
// x has not been declared before
var x;
if (typeof x === 'undefined') {
   // these statements execute
}

// One reason to use `typeof` is that it does not throw an error
// if the variable has not been declared.
if (x === undefined) { // throws a ReferenceError

}
```

## `void` operator and `undefined`

```javascript
var x;
if (x === void 0) {
   // these statements execute
}

// y has not been declared before
if (y === void 0) {
   // throws a - Uncaught ReferenceError: x　 is not defined
}
```
