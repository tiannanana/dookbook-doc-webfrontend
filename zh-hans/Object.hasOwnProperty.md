TOPICS: Object.hasOwnProperty
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.hasOwnProperty()`

**`hasOwnProperty()`** 方法会返回一个布尔值，指示对象自身属性中是否具有指定的属性（也就是，是否有指定的键）。

## 语法

```javascript
obj.hasOwnProperty(prop)
```

| 参数 | 说明 |
| :-- | :-- |
| `prop` | 要检测的属性的 `String` 字符串形式表示的名称，或者 Symbol。 |

**返回值**: 用来判断某个对象是否含有指定的属性的布尔值 `Boolean`。

## 描述

所有继承了 [`Object`] 的对象都会继承到 `hasOwnProperty` 方法。这个方法可以用来检测一个对象是否含有特定的自身属性；和 `in` 运算符不同，该方法会忽略掉那些从原型链上继承到的属性。

## 备注

即使属性的值是 `null` 或 `undefined`，只要属性存在，`hasOwnProperty` 依旧会返回 `true`。

```javascript
o = new Object();
o.propOne = null;
o.hasOwnProperty('propOne'); // 返回 true
o.propTwo = undefined;  
o.hasOwnProperty('propTwo'); // 返回 true
```

## 示例

### 使用 `hasOwnProperty` 方法判断属性是否存在

下面的例子检测了对象 `o` 是否含有自身属性 `prop`：

```javascript
o = new Object();
o.hasOwnProperty('prop'); // 返回 false
o.prop = 'exists';
o.hasOwnProperty('prop'); // 返回 true
delete o.prop;
o.hasOwnProperty('prop'); // 返回 false
```

### 自身属性与继承属性

下面的例子演示了 `hasOwnProperty` 方法对待自身属性和继承属性的区别：

```javascript
o = new Object();
o.prop = 'exists';
o.hasOwnProperty('prop');             // 返回 true
o.hasOwnProperty('toString');         // 返回 false
o.hasOwnProperty('hasOwnProperty');   // 返回 false
```

### 遍历一个对象的所有自身属性

下面的例子演示了如何在遍历一个对象的所有属性时忽略掉继承属性，注意这里 `for...in`  循环只会遍历可枚举属性，所以不应该基于这个循环中没有不可枚举的属性而得出 `hasOwnProperty`
是严格限制于可枚举项目的（如同 [`Object.getOwnPropertyNames()`](/zh-hans/webfrontend/Object.getOwnPropertyNames)）。

```javascript
var buz = {
  fog: 'stack'
};

for (var name in buz) {
  if (buz.hasOwnProperty(name)) {
    console.log('this is fog (' +
      name + ') for sure. Value: ' + buz[name]);
  }
  else {
    console.log(name); // toString or something else
  }
}
```

### 使用 `hasOwnProperty` 作为属性名

JavaScript 并没有保护 `hasOwnProperty` 这个属性名，因此，当某个对象可能自有一个占用该属性名的属性是，就需要使用外部的 `hasOwnProperty` 获得正确的结果：

```javascript
var foo = {
  hasOwnProperty: function() {
    return false;
  },
  bar: 'Here be dragons'
};

foo.hasOwnProperty('bar'); // 始终返回 false

// 如果担心这种情况，
// 可以直接使用原型链上真正的 hasOwnProperty 方法
({}).hasOwnProperty.call(foo, 'bar'); // true

// 也可以使用 Object 原型上的 hasOwnProperty 属性
Object.prototype.hasOwnProperty.call(foo, 'bar'); // true
```

注意，只有在最后一种情况下，才不会新建任何对象。
