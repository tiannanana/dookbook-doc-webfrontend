TOPICS: Object.getPrototypeOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.getPrototypeOf()`

**`Object.getPrototypeOf()`** 方法返回指定对象的原型（内部`[[Prototype]]`属性的值）。

## 语法

```javascript
Object.getPrototypeOf(object)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 要返回其原型的对象。

**返回值**: 给定对象的原型。如果没有继承属性，则返回 `null` 。

## 示例

```javascript
var proto = {};
var obj = Object.create(proto);
Object.getPrototypeOf(obj) === proto; // true

var reg = /a/;
Object.getPrototypeOf(reg) === RegExp.prototype; // true
```

### 说明

`Object.getPrototypeOf(Object)`  不是 `Object.prototype`

```javascript
//JavaScript中的 Object 是构造函数（创建对象的包装器）。
//一般用法是：
var obj = new Object();

//所以：
Object.getPrototypeOf( Object );               // ƒ () { [native code] }
Object.getPrototypeOf( Function );             // ƒ () { [native code] }

Object.getPrototypeOf( Object ) === Function.prototype;        // true

Object.getPrototypeOf( Object )是把Object这一构造函数看作对象，

//返回的当然是函数对象的原型，也就是 Function.prototype。

//正确的方法是，Object.prototype是构造出来的对象的原型。
var obj = new Object();
Object.prototype === Object.getPrototypeOf( obj );              // true

Object.prototype === Object.getPrototypeOf( {} );               // true
```

## Notes

在 ES5 中，如果参数不是一个对象类型，将抛出一个`TypeError`异常。在 ES2015 中，参数会被强制转换为一个 `Object`。

```javascript
Object.getPrototypeOf('foo');
// TypeError: "foo" is not an object (ES5 code)
Object.getPrototypeOf('foo');
// String.prototype                  (ES2015 code)
```
