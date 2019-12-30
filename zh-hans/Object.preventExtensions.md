TOPICS: Object.preventExtensions
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.preventExtensions()`

**`Object.preventExtensions()`** 方法让一个对象变的不可扩展，也就是永远不能再添加新的属性。

## 语法

```javascript
Object.preventExtensions(obj)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 将要变得不可扩展的对象。 |

**返回值**: 已经不可扩展的对象。

## 描述

如果一个对象可以添加新的属性，则这个对象是可扩展的。`Object.preventExtensions()`将对象标记为不再可扩展，因此它将永远不会具有超出它被标记为不可扩展的属性。注意，一般来说，
不可扩展对象的属性可能仍然可被删除。尝试将新属性添加到不可扩展对象将静默失败或抛出`TypeError`（最常见但不排除其他情况，如在strict mode中）。

`Object.preventExtensions()`仅阻止添加自身的属性。但属性仍然可以添加到对象原型。

一旦使其不可扩展，就无法再对象进行扩展。

## 示例

```javascript
// Object.preventExtensions将原对象变的不可扩展,并且返回原对象.
var obj = {};
var obj2 = Object.preventExtensions(obj);
obj === obj2;  // true

// 字面量方式定义的对象默认是可扩展的.
var empty = {};
Object.isExtensible(empty) //=== true

// ...但可以改变.
Object.preventExtensions(empty);
Object.isExtensible(empty) //=== false

// 使用Object.defineProperty方法为一个不可扩展的对象添加新属性会抛出异常.
var nonExtensible = { removable: true };
Object.preventExtensions(nonExtensible);
Object.defineProperty(nonExtensible, "new", { value: 8675309 }); // 抛出TypeError异常

// 在严格模式中,为一个不可扩展对象的新属性赋值会抛出TypeError异常.
function fail()
{
  "use strict";
  nonExtensible.newProperty = "FAIL"; // throws a TypeError
}
fail();

// 一个不可扩展对象的原型是不可更改的,__proto__是个非标准魔法属性,可以更改一个对象的原型.
var fixed = Object.preventExtensions({});
fixed.__proto__ = { oh: "hai" }; // 抛出TypeError异常
```

## Notes

在 ES5 中，如果参数不是一个对象类型，将抛出一个`TypeError`异常。在 ES2015 中，非对象参数将被视为一个不可扩展的普通对象，因此会被直接返回。

```javascript
Object.preventExtensions(1);
// TypeError: 1 is not an object (ES5 code)

Object.preventExtensions(1);
// 1                             (ES2015 code)
```
