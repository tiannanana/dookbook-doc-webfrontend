TOPICS: Object.keys
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.keys()`

**`Object.keys()`** 方法会返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和使用 `for...in` 循环遍历该对象时返回的顺序一致 。

## 语法

```javascript
Object.keys(obj)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 要返回其枚举自身属性的对象。 |

**返回值**: 一个表示给定对象的所有可枚举属性的字符串数组。

## 描述

`Object.keys` 返回一个所有元素为字符串的数组，其元素来自于从给定的`object`上面可直接枚举的属性。这些属性的顺序与手动遍历该对象属性时的一致。

## 示例

```javascript
// simple array
var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // console: ['0', '1', '2']

// array like object
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // console: ['0', '1', '2']

// array like object with random key ordering
var anObj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(anObj)); // console: ['2', '7', '100']

// getFoo is a property which isn't enumerable
var myObj = Object.create({}, {
  getFoo: {
    value: function () { return this.foo; }
  }
});
myObj.foo = 1;
console.log(Object.keys(myObj)); // console: ['foo']
```

如果你想获取一个对象的所有属性,，甚至包括不可枚举的，请查看[`Object.getOwnPropertyNames`](/zh-hans/webfrontend/Object.getOwnPropertyNames)。

## 注意

在ES5里，如果此方法的参数不是对象（而是一个原始值），那么它会抛出 `TypeError`。在ES2015中，非对象的参数将被强制转换为一个对象。

```javascript
Object.keys("foo");
// TypeError: "foo" is not an object (ES5 code)

Object.keys("foo");
// ["0", "1", "2"]                   (ES2015 code)
```

## Polyfill

要在原生不支持的旧环境中添加兼容的`Object.keys`，请复制以下代码段：

```javascript
if (!Object.keys) {
  Object.keys = (function () {
    var hasOwnProperty = Object.prototype.hasOwnProperty,
        hasDontEnumBug = !({toString: null}).propertyIsEnumerable('toString'),
        dontEnums = [
          'toString',
          'toLocaleString',
          'valueOf',
          'hasOwnProperty',
          'isPrototypeOf',
          'propertyIsEnumerable',
          'constructor'
        ],
        dontEnumsLength = dontEnums.length;

    return function (obj) {
      if (typeof obj !== 'object' && typeof obj !== 'function' || obj === null) throw new TypeError('Object.keys called on non-object');

      var result = [];

      for (var prop in obj) {
        if (hasOwnProperty.call(obj, prop)) result.push(prop);
      }

      if (hasDontEnumBug) {
        for (var i=0; i < dontEnumsLength; i++) {
          if (hasOwnProperty.call(obj, dontEnums[i])) result.push(dontEnums[i]);
        }
      }
      return result;
    }
  })()
};
```

上面的代码在IE7（也许IE8也是）下有个问题，就是如果传入一个来自其他 window 对象下的对象时，不可枚举的属性也会获取到。
