TOPICS: Object.getOwnPropertyDescriptor
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.getOwnPropertyDescriptor()`

**`Object.getOwnPropertyDescriptor()`** 方法返回指定对象上一个自有属性对应的属性描述符。（自有属性指的是直接赋予该对象的属性，不需要从原型链上进行查找的属性）

## 语法

```javascript
Object.getOwnPropertyDescriptor(obj, prop)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 需要查找的目标对象 |
| `prop` | 目标对象内属性名称 |

**返回值**: 如果指定的属性存在于对象上，则返回其属性描述符对象（property descriptor），否则返回 `undefined`。

## 描述

该方法允许对一个属性的描述进行检索。在 JavaScript 中， 属性 由一个字符串类型的“名字”（name）和一个“属性描述符”（property descriptor）对象构成。更多关于属性描述符类型以及他们属性的信息可以查看：[`Object.defineProperty`](/zh-hans/webfrontend/Object.defineProperty).

一个属性描述符是一个记录，由下面属性当中的某些组成的：

| 属性 | 说明 |
| :-- | :-- |
| `value` | 该属性的值(仅针对数据属性描述符有效) |
| `writable` | 当且仅当属性的值可以被改变时为`true`。(仅针对数据属性描述有效) |
| `get` | 获取该属性的访问器函数（getter）。如果没有访问器， 该值为`undefined`。(仅针对包含访问器或设置器的属性描述有效) |
| `set` | 获取该属性的设置器函数（setter）。 如果没有设置器， 该值为`undefined`。(仅针对包含访问器或设置器的属性描述有效) |
| `configurable` | 当且仅当指定对象的属性描述可以被改变或者属性可被删除时，为 `true`。 |
| `enumerable` | 当且仅当指定对象的属性可以被枚举出时，为 `true`。|

## 示例

```javascript
var o, d;

o = { get foo() { return 17; } };
d = Object.getOwnPropertyDescriptor(o, "foo");
// d {
//   configurable: true,
//   enumerable: true,
//   get: /*the getter function*/,
//   set: undefined
// }

o = { bar: 42 };
d = Object.getOwnPropertyDescriptor(o, "bar");
// d {
//   configurable: true,
//   enumerable: true,
//   value: 42,
//   writable: true
// }

o = {};
Object.defineProperty(o, "baz", {
  value: 8675309,
  writable: false,
  enumerable: false
});
d = Object.getOwnPropertyDescriptor(o, "baz");
// d {
//   value: 8675309,
//   writable: false,
//   enumerable: false,
//   configurable: false
// }
```

## 注意事项

在 ES5 中，如果该方法的第一个参数不是对象（而是原始类型），那么就会产生出现 `TypeError`。而在 ES2015，第一个的参数不是对象的话就会被强制转换为对象。

```javascript
Object.getOwnPropertyDescriptor('foo', 0);
// 类型错误: "foo" 不是一个对象  // ES5 code

Object.getOwnPropertyDescriptor('foo', 0);
// Object returned by ES2015 code: {
//   configurable: false,
//   enumerable: true,
//   value: "f",
//   writable: false
// }
```
