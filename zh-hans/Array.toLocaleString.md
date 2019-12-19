TOPICS: Array.toLocaleString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.toLocaleString()`

`toLocaleString()` 返回一个字符串表示数组中的元素。数组中的元素将使用各自的 `toLocaleString` 方法转成字符串，这些字符串将使用一个特定语言环境的字符串
（例如一个逗号 "`,`"）隔开。

## 语法

```javascript
arr.toLocaleString([locales[,options]]);
```

| 参数 | 说明 |
| :-- | :-- |
| `locales` | 带有BCP 47语言标记的字符串或字符串数组，关于`locales`参数的形式与解释，请看Intl页面。|
| `options` | 一个可配置属性的对象，对于数字 [`Number.toLocaleString()`](/zh-hans/webfrontend/Number.toLocaleString)，对于日期[`Date.toLocaleString()`](/zh-hans/webfrontend/Date.toLocaleString). |

**返回类型**: 表示数组元素的字符串。

## 示例

### 使用`locales`和`options`

数组中的元素将会使用各自的 toLocaleString 方法：

- `Object`: [`Object.toLocaleString()`](/zh-hans/webfrontend/Object.toLocaleString)
- `Number`: [`Number.toLocaleString()`](/zh-hans/webfrontend/Number.toLocaleString)
- `Date`: [`Date.toLocaleString()`](/zh-hans/webfrontend/Date.toLocaleString)

总是在`prices`数组中显示字符串和数字的货币符号：

```javascript
var numbers = [1, 4, 9];
var roots = numbers.map(Math.sqrt);
// roots的值为[1, 2, 3], numbers的值仍为[1, 4, 9]
```

## Polyfill

```javascript
// https://tc39.github.io/ecma402/#sup-array.prototype.tolocalestring
if (!Array.prototype.toLocaleString) {
  Object.defineProperty(Array.prototype, 'toLocaleString', {
    value: function(locales, options) {
      // 1. Let O be ? ToObject(this value).
      if (this == null) {
        throw new TypeError('"this" is null or not defined');
      }

      var a = Object(this);

      // 2. Let len be ? ToLength(? Get(A, "length")).
      var len = a.length >>> 0;

      // 3. Let separator be the String value for the
      //    list-separator String appropriate for the
      //    host environment's current locale (this is
      //    derived in an implementation-defined way).
      // NOTE: In this case, we will use a comma
      var separator = ',';

      // 4. If len is zero, return the empty String.
      if (len === 0) {
        return '';
      }

      // 5. Let firstElement be ? Get(A, "0").
      var firstElement = a[0];
      // 6. If firstElement is undefined or null, then
      //  a.Let R be the empty String.
      // 7. Else,
      //  a. Let R be ?
      //     ToString(?
      //       Invoke(
      //        firstElement,
      //        "toLocaleString",
      //        « locales, options »
      //       )
      //     )
      var r = firstElement == null ?
        '' : firstElement.toLocaleString(locales, options);

      // 8. Let k be 1.
      var k = 1;

      // 9. Repeat, while k < len
      while (k < len) {
        // a. Let S be a String value produced by
        //   concatenating R and separator.
        var s = r + separator;

        // b. Let nextElement be ? Get(A, ToString(k)).
        var nextElement = a[k];

        // c. If nextElement is undefined or null, then
        //   i. Let R be the empty String.
        // d. Else,
        //   i. Let R be ?
        //     ToString(?
        //       Invoke(
        //        nextElement,
        //        "toLocaleString",
        //        « locales, options »
        //       )
        //     )
        r = nextElement == null ?
          '' : nextElement.toLocaleString(locales, options);

        // e. Let R be a String value produced by
        //   concatenating S and R.
        r = s + r;

        // f. Increase k by 1.
        k++;
      }

      // 10. Return R.
      return r;
    }
  });
}
```

如果你需要支持真正不支持[`Object.defineProperty`](/zh-hans/webfrontend/Object.defineProperty)的JavaScript引擎，最好不要对Array方法进行填充，因为你不能使它们不可枚举。
