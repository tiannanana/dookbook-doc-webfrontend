TOPICS: Array.prototype
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.prototype`

Symbol 属性 `@@unscopable` 包含了所有 ES2015 (ES6) 中新定义的、且并未被更早的 ECMAScript 标准收纳的属性名。这些属性被排除在由 `with` 语句绑定的环境中。

## 语法

```javascript
arr[Symbol.unscopables]
```

## 描述

`with` 绑定中未包含的数组默认属性有：

- [`copyWithin()`](/zh-hans/webfrontend/Array.copyWithin)
- [`entries()`](/zh-hans/webfrontend/Array.entries)
- [`fill()`](/zh-hans/webfrontend/Array.fill)
- [`find()`](/zh-hans/webfrontend/Array.find)
- [`findIndex()`](/zh-hans/webfrontend/Array.findIndex)
- [`includes()`](/zh-hans/webfrontend/Array.includes)
- [`keys()`](/zh-hans/webfrontend/Array.keys)
- [`values()`](/zh-hans/webfrontend/Array.values)

参考 [`Symbol.unscopables`](/zh-hans/webfrontend/Symbol.unscopables) 以了解如何为自定义的对象设置 `unscopables`。

`Array.prototype[@@unscopables]` 属性的属性特性：

|  |  |
| :--- | :--- |
| `writable` | `false` |
| `enumerable` | `false` |
| `configurable` | `true` |

## 示例

以下的代码在 ES5 或更早的版本中能正常工作。然而 ECMAScript 2015 (ES6) 或之后的版本中新添加了 [`Array.keys()`](/zh-hans/webfrontend/Array.keys)
这个方法。这意味着在 `with` 语句的作用域中，"keys"只能作为方法，而不能作为某个变量。这正是内置的 `@@unscopables` 即 `Array[@@unscopables]`
symbol 属性所要解决的问题：防止某些数组方法被添加到 `with` 语句的作用域内。

```javascript
var keys = [];

with(Array) {
  keys.push("something");
}

Object.keys(Array[Symbol.unscopables]);
// ["copyWithin", "entries", "fill", "find", "findIndex",
//  "includes", "keys", "values"]
```
