TOPICS: Array.includes
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.includes()`

`includes()` 方法用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 `true`，否则返回`false`。

## 语法

```javascript
arr.includes(valueToFind[, fromIndex])
```

| 参数 | 说明 |
| :-- | :-- |
| `valueToFind` | 需要查找的元素值。<br>**Note:** 使用 `includes()`比较字符串和字符时是区分大小写。
| `fromIndex` 可选 | 从`fromIndex` 索引处开始查找 `valueToFind`。如果为负值，则按升序从 `array.length + fromIndex` 的索引开始搜 （即使从末尾开始往前跳 `fromIndex` 的绝对值个索引，然后往后搜寻）。默认为 `0`。 |

**返回类型**: Boolean

## 示例

```javascript
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

### `fromIndex` 大于等于数组长度

如果 `fromIndex` 大于等于数组的长度，则会返回 `false`，且该数组不会被搜索。

```javascript
var arr = ['a', 'b', 'c'];

arr.includes('c', 3);   // false
arr.includes('c', 100); // false
```

### 计算出的索引小于 0

如果 `fromIndex` 为负值，计算出的索引将作为开始搜索`searchElement`的位置。如果计算出的索引小于 `0`，则整个数组都会被搜索。

```javascript
// array length is 3
// fromIndex is -100
// computed index is 3 + (-100) = -97

var arr = ['a', 'b', 'c'];

arr.includes('a', -100); // true
arr.includes('b', -100); // true
arr.includes('c', -100); // true
arr.includes('a', -2); // false
```

### 作为通用方法的 `includes()`

`includes()` 方法有意设计为通用方法。它不要求`this`值是数组对象，所以它可以被用于其他类型的对象 (比如类数组对象)。下面的例子展示了 在函数的 `arguments` 对象上调用的
`includes()` 方法。

```javascript
(function() {
  console.log([].includes.call(arguments, 'a')); // true
  console.log([].includes.call(arguments, 'd')); // false
})('a','b','c');
```

## Polyfill

`forEach()` 是在第五版本里被添加到 ECMA-262 标准的；这样它可能在标准的其他实现中不存在，你可以在你调用 `forEach()` 之前插入下面的代码，在本地不支持的情况下使用
`forEach()`。该算法是 ECMA-262 第5版中指定的算法。它假定 [`Object`](/zh-hans/webfrontend/Object) 和 [`TypeError`](/zh-hans/webfrontend/TypeError)
拥有它们的初始值，且 `callback.call` 等价于 [`Function.call()`](/zh-hans/webfrontend/Function.call)。

```javascript
// https://tc39.github.io/ecma262/#sec-array.prototype.includes
if (!Array.prototype.includes) {
  Object.defineProperty(Array.prototype, 'includes', {
    value: function(valueToFind, fromIndex) {

      if (this == null) {
        throw new TypeError('"this" is null or not defined');
      }

      // 1. Let O be ? ToObject(this value).
      var o = Object(this);

      // 2. Let len be ? ToLength(? Get(O, "length")).
      var len = o.length >>> 0;

      // 3. If len is 0, return false.
      if (len === 0) {
        return false;
      }

      // 4. Let n be ? ToInteger(fromIndex).
      //    (If fromIndex is undefined, this step produces the value 0.)
      var n = fromIndex | 0;

      // 5. If n ≥ 0, then
      //  a. Let k be n.
      // 6. Else n < 0,
      //  a. Let k be len + n.
      //  b. If k < 0, let k be 0.
      var k = Math.max(n >= 0 ? n : len - Math.abs(n), 0);

      function sameValueZero(x, y) {
        return x === y || (typeof x === 'number' && typeof y === 'number' && isNaN(x) && isNaN(y));
      }

      // 7. Repeat, while k < len
      while (k < len) {
        // a. Let elementK be the result of ? Get(O, ! ToString(k)).
        // b. If SameValueZero(valueToFind, elementK) is true, return true.
        if (sameValueZero(o[k], valueToFind)) {
          return true;
        }
        // c. Increase k by 1.
        k++;
      }

      // 8. Return false
      return false;
    }
  });
}
```

如果你需要支持那些不支持[`Object.defineProperty`](/zh-hans/webfrontend/Object.defineProperty)的废弃JavaScript 引擎，你最好不要
polyfill `Array.prototype` 方法，因为你不能使它们不可枚举。
