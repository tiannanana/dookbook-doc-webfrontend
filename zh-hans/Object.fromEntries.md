TOPICS: Object.fromEntries
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.fromEntries()`

**`Object.fromEntries()`** 方法把键值对列表转换为一个对象。

## 语法

```javascript
Object.fromEntries(iterable);
```

| 参数 | 说明 |
| :-- | :-- |
| `iterable` | 可迭代对象，类似 [`Array`](/zh-hans/webfrontend/Array) 、 [`Map`](/zh-hans/webfrontend/Map) 或者其它实现了可迭代协议的对象。 |

**返回值**: 一个由该迭代对象条目提供对应属性的新对象。

## 描述

`Object.fromEntries()` 方法接收一个键值对的列表参数，并返回一个带有这些键值对的新对象。这个迭代参数应该是一个能够实现@iterator方法的的对象，返回一个迭代器对象。它生成一个具有两个元素的类数组的对象，第一个元素是将用作属性键的值，第二个元素是与该属性键关联的值。

`Object.fromEntries()` 是 [`Object.entries`](/zh-hans/webfrontend/Object.entries) 的反转。

## 示例

### `Map` 转化为 `Object`

通过 `Object.fromEntries`， 可以将 [`Map`](/zh-hans/webfrontend/Map) 转化为 [`Object`](/zh-hans/webfrontend/Object):

```javascript
const map = new Map([ ['foo', 'bar'], ['baz', 42] ]);
const obj = Object.fromEntries(map);
console.log(obj); // { foo: "bar", baz: 42 }
```

### `Array` 转化为 `Object`

通过 `Object.fromEntries`， 可以将 [`Array`](/zh-hans/webfrontend/Array) 转化为 [`Object`](/zh-hans/webfrontend/Object):

```javascript
const arr = [ ['0', 'a'], ['1', 'b'], ['2', 'c'] ];
const obj = Object.fromEntries(arr);
console.log(obj); // { 0: "a", 1: "b", 2: "c" }
```

### 对象转换

`Object.fromEntries` 是 `Object.entries()` 的反转函数， 借用 数组处理函数 可以转换对象，如下：

```javascript
const object1 = { a: 1, b: 2, c: 3 };

const object2 = Object.fromEntries(
  Object.entries(object1)
  .map(([ key, val ]) => [ key, val * 2 ])
);

console.log(object2);
// { a: 2, b: 4, c: 6 }
```
