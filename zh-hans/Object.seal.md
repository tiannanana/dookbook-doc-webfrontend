TOPICS: Object.seal
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.seal()`

**`Object.seal()`** 方法封闭一个对象，阻止添加新属性并将所有现有属性标记为不可配置。当前属性的值只要可写就可以改变。

## 语法

```javascript
Object.seal(obj)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 将要被密封的对象。 |

**返回值**: 被密封的对象。

## 描述

通常，一个对象是可扩展的（可以添加新的属性）。密封一个对象会让这个对象变的不能添加新属性，且所有已有属性会变的不可配置。属性不可配置的效果就是属性变的不可删除，以及一个数据属性不能被重新定义成为
访问器属性，或者反之。但属性的值仍然可以修改。尝试删除一个密封对象的属性或者将某个密封对象的属性从数据属性转换成访问器属性，结果会静默失败或抛出 `TypeError（在严格模式` 中最常见的，但不唯一）。

不会影响从原型链上继承的属性。但 `__proto__` 属性的值也会不能修改。

返回被密封对象的引用。

## 示例

```javascript
var obj = {
  prop: function() {},
  foo: 'bar'
};

// New properties may be added, existing properties
// may be changed or removed.
obj.foo = 'baz';
obj.lumpy = 'woof';
delete obj.prop;

var o = Object.seal(obj);

o === obj; // true
Object.isSealed(obj); // === true

// Changing property values on a sealed object
// still works.
obj.foo = 'quux';

// But you can't convert data properties to accessors,
// or vice versa.
Object.defineProperty(obj, 'foo', {
  get: function() { return 'g'; }
}); // throws a TypeError

// Now any changes, other than to property values,
// will fail.
obj.quaxxor = 'the friendly duck';
// silently doesn't add the property
delete obj.foo;
// silently doesn't delete the property

// ...and in strict mode such attempts
// will throw TypeErrors.
function fail() {
  'use strict';
  delete obj.foo; // throws a TypeError
  obj.sparky = 'arf'; // throws a TypeError
}
fail();

// Attempted additions through
// Object.defineProperty will also throw.
Object.defineProperty(obj, 'ohai', {
  value: 17
}); // throws a TypeError
Object.defineProperty(obj, 'foo', {
  value: 'eit'
}); // changes existing property value
```

## 注意

在ES5中，如果这个方法的参数不是一个（原始）对象，那么它将导致`TypeError`。在ES2015中，非对象参数将被视为已被密封的普通对象，会直接返回它。

```javascript
Object.seal(1);
// TypeError: 1 is not an object (ES5 code)

Object.seal(1);
// 1                             (ES2015 code)
```

### 对比 `Object.freeze()`

使用`Object.freeze()`冻结的对象中的现有属性是不可变的。用`Object.seal()`密封的对象可以改变其现有属性。
