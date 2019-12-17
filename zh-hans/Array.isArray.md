TOPICS: Array.isArray
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.isArray()`

`Array.isArray()` 用于确定传递的值是否是一个 [`Array`](/zh-hans/webfrontend/Array_Object)。

```javascript
Array.isArray([1, 2, 3]);  
// true
Array.isArray({foo: 123});
// false
Array.isArray("foobar");
// false
Array.isArray(undefined);  
// false
```

## 语法

```javascript
Array.isArray(obj)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 需要检测的值。 |

**返回类型**: 如果值是 `Array`，则为`true`; 否则为`false`。

## 描述

如果对象是 [`Array`](/zh-hans/webfrontend/Array_Object) ，则返回`true`，否则为`false`。

有关更多详细信息，请参阅文章[严格判定JavaScript对象是否为数组](http://web.mit.edu/jwalden/www/isArray.html)。

有关更多详细信息，请参见文章[“绝对准确地确定JavaScript对象是否为数组”](http://web.mit.edu/jwalden/www/isArray.html)。 给定一个[`TypedArray`](/zh-hans/webfrontend/TypedArray)实例，总是返回`false`。

## 示例

```javascript
// 下面的函数调用都返回 true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
Array.isArray(new Array('a', 'b', 'c', 'd'))
// 鲜为人知的事实：其实 Array.prototype 也是一个数组。
Array.isArray(Array.prototype);

// 下面的函数调用都返回 false
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray('Array');
Array.isArray(true);
Array.isArray(false);
Array.isArray(new Uint8Array(32))
Array.isArray({ __proto__: Array.prototype });
```

### `instanceof` 和 `isArray`

当检测Array实例时, `Array.isArray` 优于 `instanceof`,因为`Array.isArray`能检测`iframes`.

```javascript
var iframe = document.createElement('iframe');
document.body.appendChild(iframe);
xArray = window.frames[window.frames.length-1].Array;
var arr = new xArray(1,2,3); // [1,2,3]

// Correctly checking for Array
Array.isArray(arr);  // true
// Considered harmful, because doesn't work though iframes
arr instanceof Array; // false
```

## Polyfill

假如不存在 `Array.isArray()`，则在其他代码之前运行下面的代码将创建该方法。

```javascript
if (!Array.isArray) {
  Array.isArray = function(arg) {
    return Object.prototype.toString.call(arg) === '[object Array]';
  };
}
```
