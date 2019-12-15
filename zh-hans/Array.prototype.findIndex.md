TOPICS: Array.prototype.findIndex
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.findIndex()`

"`findIndex()`"方法返回数组中满足提供的测试函数的第一个元素的索引。否则返回-1。

另请参见 [`find()`](/zh-hans/webfrontend/Array.prototype.find) 方法，它返回数组中找到的元素的值，而不是其索引。

## 语法

```html
arr.findIndex(callback[, thisArg])
```

| 参数 | 说明 |
| :-- | :-- |
| `callback` | 针对数组中的每个元素, 都会执行该回调函数, 执行时会自动传入下面三个参数:<br>**`element`**<br>当前元素。<br><br>**`index`**<br>当前元素的索引。<br><br>**`array`**<br>调用"`findIndex`"的数组。
| `thisValue` | 可选。执行`callback`时作为`this`对象的值. |

**返回类型**：返回符合测试条件的第一个数组元素索引，如果没有符合条件的则返回 -1。

## 示例

### 查找数组中首个质数元素的索引

以下示例查找数组中素数的元素的索引（如果不存在素数，则返回-1）。

```javascript
function isPrime(element, index, array) {
  var start = 2;
  while (start <= Math.sqrt(element)) {
    if (element % start++ < 1) {
      return false;
    }
  }
  return element > 1;
}

console.log([4, 6, 8, 12].findIndex(isPrime)); // -1, not found
console.log([4, 6, 7, 12].findIndex(isPrime)); // 2
```

## Polyfill

```javascript
// https://tc39.github.io/ecma262/#sec-array.prototype.findIndex
if (!Array.prototype.findIndex) {
  Object.defineProperty(Array.prototype, 'findIndex', {
    value: function(predicate) {
     // 1. Let O be ? ToObject(this value).
      if (this == null) {
        throw new TypeError('"this" is null or not defined');
      }

      var o = Object(this);

      // 2. Let len be ? ToLength(? Get(O, "length")).
      var len = o.length >>> 0;

      // 3. If IsCallable(predicate) is false, throw a TypeError exception.
      if (typeof predicate !== 'function') {
        throw new TypeError('predicate must be a function');
      }

      // 4. If thisArg was supplied, let T be thisArg; else let T be undefined.
      var thisArg = arguments[1];

      // 5. Let k be 0.
      var k = 0;

      // 6. Repeat, while k < len
      while (k < len) {
        // a. Let Pk be ! ToString(k).
        // b. Let kValue be ? Get(O, Pk).
        // c. Let testResult be ToBoolean(? Call(predicate, T, « kValue, k, O »)).
        // d. If testResult is true, return k.
        var kValue = o[k];
        if (predicate.call(thisArg, kValue, k, o)) {
          return k;
        }
        // e. Increase k by 1.
        k++;
      }

      // 7. Return -1.
      return -1;
    }
  });
}
```

如果您需要兼容不支持[`Object.defineProperty`](/zh-hans/webfrontend/Object.defineProperty)的JavaScript引擎，那么最好不要对`Array.prototype`方法进行
polyfill ，因为您无法使其成为不可枚举的。

使用此方法需要注意你是否在uc浏览器环境,如果你的页面在支付宝上使用尤其注意,因为支付宝使用的就是uc浏览器环境.
