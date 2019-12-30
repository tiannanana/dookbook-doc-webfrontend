TOPICS: Object.fromEntries
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.fromEntries()`

The **`Object.fromEntries()`** method transforms a list of key-value pairs into an object.

## Syntax

```javascript
Object.fromEntries(iterable);
```

| parameter | Description |
| :-- | :-- |
| `iterable` | An iterable such as [`Array`](/en/webfrontend/Array) or [`Map`](/en/webfrontend/Map) or other objects implementing the iterable protocol. |

**Return value**: A new object whose properties are given by the entries of the iterable.

## Description

The `Object.fromEntries()` method takes a list of key-value pairs and returns a new object whose
properties are given by those entries. The iterable argument is expected to be an object that
implements an `@@iterator` method, that returns an iterator object, that produces a two element
array-like object, whose first element is a value that will be used as a property key, and whose
second element is the value to associate with that property key.

`Object.fromEntries()` performs the reverse of [`Object.entries()`](/en/webfrontend/Object.entries).

## Examples

### Converting a `Map` to an `Object`

With `Object.fromEntries`, you can convert from [`Map`](/en/webfrontend/Map) to [`Object`](/en/webfrontend/Object):

```javascript
const map = new Map([ ['foo', 'bar'], ['baz', 42] ]);
const obj = Object.fromEntries(map);
console.log(obj); // { foo: "bar", baz: 42 }
```

### Converting an `Array` to an `Object`

With `Object.fromEntries`, you can convert from [`Array`](/en/webfrontend/Array) to [`Object`](/en/webfrontend/Object):

```javascript
const arr = [ ['0', 'a'], ['1', 'b'], ['2', 'c'] ];
const obj = Object.fromEntries(arr);
console.log(obj); // { 0: "a", 1: "b", 2: "c" }
```

### Object transformations

With `Object.fromEntries`, its reverse method [`Object.entries()`](/en/webfrontend/Object.entries),
and array manipulation methods, you are able to transform objects like this:

```javascript
const object1 = { a: 1, b: 2, c: 3 };

const object2 = Object.fromEntries(
  Object.entries(object1)
  .map(([ key, val ]) => [ key, val * 2 ])
);

console.log(object2);
// { a: 2, b: 4, c: 6 }
```
