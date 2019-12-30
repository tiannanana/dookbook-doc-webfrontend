TOPICS: Object.defineProperty
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.defineProperty()`

**`Object.defineProperty()`** 方法会直接在一个对象上定义一个新属性，或者修改一个对象的现有属性， 并返回这个对象。

## 语法

```javascript
Object.defineProperty(obj, prop, descriptor)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 要在其上定义属性的对象。 |
| `prop` | 要定义或修改的属性的名称。 |
| `descriptor` | 将被定义或修改的属性描述符。 |

**返回值**: 被传递给函数的对象。

!!! warn ""
    在ES6中，由于 Symbol类型的特殊性，用Symbol类型的值来做对象的key与常规的定义或修改不同，而`Object.defineProperty` 是定义`key`为Symbol的属性的方法之一。

## 描述

该方法允许精确添加或修改对象的属性。通过赋值操作添加的普通属性是可枚举的，能够在属性枚举期间呈现出来（`for...in` 或 `Object.keys` 方法），这些属性的值可以被改变，
也可以被删除。这个方法允许修改默认的额外选项（或配置）。默认情况下，使用 `Object.defineProperty()` 添加的属性值是不可修改的。

## 属性描述符

对象里目前存在的属性描述符有两种主要形式：**数据描述符**和**存取描述符**。**数据描述符**是一个具有值的属性，该值可能是可写的，也可能不是可写的。**存取描述符** 是由getter-setter函数对描述的属性。描述符必须是这两种形式之一；不能同时是两者。

**数据描述符和存取描述符均具有** 以下可选键值(默认值是在使用`Object.defineProperty()`定义属性的情况下)：

|  |  |
| :-- | :-- |
| **`configurable`** | 当且仅当该属性的 `configurable` 为 `true` 时，该属性描述符才能够被改变，同时该属性也能从对应的对象上被删除。默认为 `false`。
| **`enumerable`** | 当且仅当该属性的`enumerable`为`true`时，该属性才能够出现在对象的枚举属性中。默认为 `false`。

### 数据描述符同时具有以下可选键值

|  |  |
| :-- | :-- |
| **`value`** | 该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 `undefined`。
| **`writable`** | 当且仅当该属性的`writable`为`true`时，`value`才能被赋值运算符改变。默认为 `false`。

### 存取描述符同时具有以下可选键值

|  |  |
| :-- | :-- |
| **`get`** | 一个给属性提供 `getter` 的方法，如果没有 `getter` 则为 `undefined`。当访问该属性时，该方法会被执行，方法执行时没有参数传入，但是会传入this对象（由于继承关系，这里的`this`并不一定是定义该属性的对象）。
默认为 `undefined。`
| **`set`** | 一个给属性提供 `setter` 的方法，如果没有 `setter` 则为 `undefined`。当属性值修改时，触发执行该方法。该方法将接受唯一参数，即该属性新的参数值。
默认为 `undefined。`

描述符可同时具有的键值

|  | configurable | enumerable | value | writable | get | set |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| **数据描述符** | Yes | Yes | Yes | Yes | No | No |
| **存取描述符** | Yes | Yes | No | No | Yes | Yes |

如果一个描述符不具有`value`,`writable`,`get` 和 `set` 任意一个关键字，那么它将被认为是一个数据描述符。如果一个描述符同时有(`value`或`writable`)和(`get`或`set`)关键字，将会产生一个异常。

记住，这些选项不一定是自身属性，如果是继承来的也要考虑。为了确认保留这些默认值，你可能要在这之前冻结 `Object.prototype`，明确指定所有的选项，或者通过 `Object.create(null)`将`__proto__`属性指向`null`。

```javascript
// 使用 __proto__
var obj = {};
var descriptor = Object.create(null); // 没有继承的属性
// 默认没有 enumerable，没有 configurable，没有 writable
descriptor.value = 'static';
Object.defineProperty(obj, 'key', descriptor);

// 显式
Object.defineProperty(obj, "key", {
  enumerable: false,
  configurable: false,
  writable: false,
  value: "static"
});

// 循环使用同一对象
function withValue(value) {
  var d = withValue.d || (
    withValue.d = {
      enumerable: false,
      writable: false,
      configurable: false,
      value: null
    }
  );
  d.value = value;
  return d;
}
// ... 并且 ...
Object.defineProperty(obj, "key", withValue("static"));

// 如果 freeze 可用, 防止代码添加或删除对象原型的属性
// （value, get, set, enumerable, writable, configurable）
(Object.freeze||Object)(Object.prototype);
```

## 示例

### 使用二进制标志代替属性来描述对象

如果你通过`Object.defineProperty()`方法定义了许多属性，你可以通过二进制标志使用相同的描述对象，一次次重新定义每个属性。

```javascript
var oDesc = {};
function setProp (nMask, oObj, sKey, vVal_fGet, fSet) {
  if (nMask & 8) {
    // accessor descriptor
    if (vVal_fGet) {
      oDesc.get = vVal_fGet;
    } else {
      delete oDesc.get;
    }
    if (fSet) {
      oDesc.set = fSet;
    } else {
      delete oDesc.set;
    }
    delete oDesc.value;
    delete oDesc.writable;
  } else {
    // data descriptor
    if (arguments.length > 3) {
      oDesc.value = vVal_fGet;
    } else {
      delete oDesc.value;
    }
    oDesc.writable = Boolean(nMask & 4);
    delete oDesc.get;
    delete oDesc.set;
  }
  oDesc.enumerable = Boolean(nMask & 1);
  oDesc.configurable = Boolean(nMask & 2);
  Object.defineProperty(oObj, sKey, oDesc);
  return oObj;
}

/*
* :: function setProp ::
*
* nMask is a bitmask:
*  flag 0x1: property is enumerable,
*  flag 0x2: property is configurable,
*  flag 0x4: property is writable,
*  flag 0x8: property is accessor descriptor.
* oObj is the object on which to define the property;
* sKey is the name of the property to be defined or modified;
* vVal_fGet is the value to assign to a data descriptor or the getter function
* to assign to an accessor descriptor (depending on the bitmask);
* fSet is the setter function to assign to an accessor descriptor;
*
* Bitmask possible values:
*
*  0  : readonly data descriptor - not configurable, not enumerable (0000).
*  1  : readonly data descriptor - not configurable, enumerable (0001).
*  2  : readonly data descriptor - configurable, not enumerable (0010).
*  3  : readonly data descriptor - configurable, enumerable (0011).
*  4  : writable data descriptor - not configurable, not enumerable (0100).
*  5  : writable data descriptor - not configurable, enumerable (0101).
*  6  : writable data descriptor - configurable, not enumerable (0110).
*  7  : writable data descriptor - configurable, enumerable (0111).
*  8  : accessor descriptor - not configurable, not enumerable (1000).
*  9  : accessor descriptor - not configurable, enumerable (1001).
*  10 : accessor descriptor - configurable, not enumerable (1010).
*  11 : accessor descriptor - configurable, enumerable (1011).
*
*  Note: If the flag 0x8 is setted to "accessor descriptor" the flag 0x4 (writable)
*  will be ignored. If not, the fSet argument will be ignored.
*/

// creating a new empty object
var myObj = {};

// adding a writable data descriptor - not configurable, not enumerable
setProp(4, myObj, 'myNumber', 25);

// adding a readonly data descriptor - not configurable, enumerable
setProp(1, myObj, 'myString', 'Hello world!');

// adding an accessor descriptor - not configurable, enumerable
setProp(9, myObj, 'myArray', function() {
  for (var iBit = 0, iFlag = 1, aBoolArr = [false];
    iFlag < this.myNumber + 1 || (this.myNumber & iFlag);
    iFlag = iFlag << 1
  ) {
    aBoolArr[iBit++] = Boolean(this.myNumber & iFlag);
  }
  return aBoolArr;
}, function(aNewMask) {
  for (var nNew = 0, iBit = 0; iBit < aNewMask.length; iBit++) {
    nNew |= Boolean(aNewMask[iBit]) << iBit;
  }
  this.myNumber = nNew;
});

// adding a writable data descriptor (undefined value) - configurable, enumerable
setProp(7, myObj, 'myUndefined');

// adding an accessor descriptor (only getter) - configurable, enumerable
setProp(11, myObj, 'myDate', function() { return new Date(); });

// adding an accessor descriptor (only setter) - not configurable, not enumerable
setProp(8, myObj, 'myAlert', null, function(sTxt) { alert(sTxt); });

myObj.myAlert = myObj.myDate.toLocaleString() + '\n\n' + myObj.myString +
  '\nThe number ' + myObj.myNumber + ' represents the following bitmask: ' +
  myObj.myArray.join(', ') + '.';

// listing the enumerable properties
var sList = 'Here are the enumerable properties of myObj object:\n';
for (var sProp in myObj) {
  sList += '\nmyObj.' + sProp + ' => ' + myObj[sProp] + ';'
}

alert(sList);
```

### 创建属性

如果对象中不存在指定的属性，`Object.defineProperty()`就创建这个属性。当描述符中省略某些字段时，这些字段将使用它们的默认值。拥有布尔值的字段的默认值都是`false`。`value`，`get`和`set`字段的默认值为`undefined`。一个没有`get/set/value/writable`定义的属性被称为“通用的”，并被“键入”为一个数据描述符。

```javascript
var o = {}; // 创建一个新对象

// 在对象中添加一个属性与数据描述符的示例
Object.defineProperty(o, "a", {
  value : 37,
  writable : true,
  enumerable : true,
  configurable : true
});

// 对象o拥有了属性a，值为37

// 在对象中添加一个属性与存取描述符的示例
var bValue;
Object.defineProperty(o, "b", {
  get : function(){
    return bValue;
  },
  set : function(newValue){
    bValue = newValue;
  },
  enumerable : true,
  configurable : true
});

o.b = 38;
// 对象o拥有了属性b，值为38

// o.b的值现在总是与bValue相同，除非重新定义o.b

// 数据描述符和存取描述符不能混合使用
Object.defineProperty(o, "conflict", {
  value: 0x9f91102,
  get: function() {
    return 0xdeadbeef;
  }
});
// throws a TypeError: value appears only in data descriptors, get appears only in accessor descriptors
```

### 修改属性

如果属性已经存在，`Object.defineProperty()`将尝试根据描述符中的值以及对象当前的配置来修改这个属性。如果旧描述符将其`configurable` 属性设置为`false`，
则该属性被认为是“不可配置的”，并且没有属性可以被改变（除了单向改变 `writable` 为 `false`）。当属性不可配置时，不能在数据和访问器属性类型之间切换。

当试图改变不可配置属性（除了`value`和`writable` 属性之外）的值时会抛出`TypeError`，除非当前值和新值相同。

### `Writable` 属性

当`writable`属性设置为`false`时，该属性被称为“不可写”。它不能被重新分配。

```javascript
var o = {}; // Creates a new object

Object.defineProperty(o, 'a', {
  value: 37,
  writable: false
});

console.log(o.a); // logs 37
o.a = 25; // No error thrown
// (it would throw in strict mode,
// even if the value had been the same)
console.log(o.a); // logs 37. The assignment didn't work.

// strict mode
(function() {
  'use strict';
  var o = {};
  Object.defineProperty(o, 'b', {
    value: 2,
    writable: false
  });
  o.b = 3; // throws TypeError: "b" is read-only
  return o.b; // returns 2 without the line above
}());
```

如示例所示，试图写入非可写属性不会改变它，也不会引发错误。

### `Enumerable` 特性

`enumerable`定义了对象的属性是否可以在 `for...in` 循环和 `Object.keys()` 中被枚举。

```javascript
var o = {};
Object.defineProperty(o, "a", { value : 1, enumerable:true });
Object.defineProperty(o, "b", { value : 2, enumerable:false });
Object.defineProperty(o, "c", { value : 3 }); // enumerable defaults to false
o.d = 4; // 如果使用直接赋值的方式创建对象的属性，则这个属性的enumerable为true

for (var i in o) {
  console.log(i);  
}
// 打印 'a' 和 'd' (in undefined order)

Object.keys(o); // ["a", "d"]

o.propertyIsEnumerable('a'); // true
o.propertyIsEnumerable('b'); // false
o.propertyIsEnumerable('c'); // false
```

### `Configurable` 特性

`configurable`特性表示对象的属性是否可以被删除，以及除`value`和`writable`特性外的其他特性是否可以被修改。

```javascript
var o = {};
Object.defineProperty(o, "a", { get : function(){return 1;},
                                configurable : false } );

// throws a TypeError
Object.defineProperty(o, "a", {configurable : true});
// throws a TypeError
Object.defineProperty(o, "a", {enumerable : true});
// throws a TypeError (set was undefined previously)
Object.defineProperty(o, "a", {set : function(){}});
// throws a TypeError (even though the new get does exactly the same thing)
Object.defineProperty(o, "a", {get : function(){return 1;}});
// throws a TypeError
Object.defineProperty(o, "a", {value : 12});

console.log(o.a); // logs 1
delete o.a; // Nothing happens
console.log(o.a); // logs 1
```

如果`o.a`的`configurable`属性为`true`，则不会抛出任何错误，并且该属性将在最后被删除。

### 添加多个属性和默认值

考虑特性被赋予的默认特性值非常重要，通常，使用点运算符和`Object.defineProperty()`为对象的属性赋值时，数据描述符中的属性默认值是不同的，如下例所示。

```javascript
var o = {};

o.a = 1;
// 等同于 :
Object.defineProperty(o, "a", {
  value : 1,
  writable : true,
  configurable : true,
  enumerable : true
});


// 另一方面，
Object.defineProperty(o, "a", { value : 1 });
// 等同于 :
Object.defineProperty(o, "a", {
  value : 1,
  writable : false,
  configurable : false,
  enumerable : false
});
```

### 一般的 Setters 和 Getters

下面的例子展示了如何实现一个自存档对象。 当设置temperature 属性时，archive 数组会获取日志条目。

```javascript
function Archiver() {
  var temperature = null;
  var archive = [];

  Object.defineProperty(this, 'temperature', {
    get: function() {
      console.log('get!');
      return temperature;
    },
    set: function(value) {
      temperature = value;
      archive.push({ val: temperature });
    }
  });

  this.getArchive = function() { return archive; };
}

var arc = new Archiver();
arc.temperature; // 'get!'
arc.temperature = 11;
arc.temperature = 13;
arc.getArchive(); // [{ val: 11 }, { val: 13 }]
```

或

```javascript
var pattern = {
    get: function () {
        return 'I alway return this string,whatever you have assigned';
    },
    set: function () {
        this.myname = 'this is my name string';
    }
};


function TestDefineSetAndGet() {
    Object.defineProperty(this, 'myproperty', pattern);
}


var instance = new TestDefineSetAndGet();
instance.myproperty = 'test';

// 'I alway return this string,whatever you have assigned'
console.log(instance.myproperty);
// 'this is my name string'
console.log(instance.myname);继承属性
```

### 继承属性

如果访问者的属性是被继承的，它的 `get` 和 `set` 方法会在子对象的属性被访问或者修改时被调用。如果这些方法用一个变量存值，该值会被所有对象共享。

```javascript
function myclass() {
}

var value;
Object.defineProperty(myclass.prototype, "x", {
  get() {
    return value;
  },
  set(x) {
    value = x;
  }
});

var a = new myclass();
var b = new myclass();
a.x = 1;
console.log(b.x); // 1
```

这可以通过将值存储在另一个属性中解决。在 `get` 和 `set` `方法中，this` 指向某个被访问和修改属性的对象。

```javascript
function myclass() {
}

Object.defineProperty(myclass.prototype, "x", {
  get() {
    return this.stored_x;
  },
  set(x) {
    this.stored_x = x;
  }
});

var a = new myclass();
var b = new myclass();
a.x = 1;
console.log(b.x); // undefined
```

不像访问者属性，值属性始终在对象自身上设置，而不是一个原型。然而，如果一个不可写的属性被继承，它仍然可以防止修改对象的属性。

```javascript
function myclass() {
}

myclass.prototype.x = 1;
Object.defineProperty(myclass.prototype, "y", {
  writable: false,
  value: 1
});

var a = new myclass();
a.x = 2;
console.log(a.x); // 2
console.log(myclass.prototype.x); // 1
a.y = 2; // Ignored, throws in strict mode
console.log(a.y); // 1
console.log(myclass.prototype.y); // 1
```
