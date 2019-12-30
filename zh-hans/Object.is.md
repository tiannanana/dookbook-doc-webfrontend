TOPICS: Object.is
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.is()`

**`Object.is()`** 方法判断两个值是否是相同的值。

## 语法

```javascript
Object.is(value1, value2);
```

| 参数 | 说明 |
| :-- | :-- |
| `value1` | 第一个需要比较的值。 |
| `value2` | 第二个需要比较的值。 |

**返回值**: 表示两个参数是否相同的布尔值。

## 描述

`Object.is()` 判断两个值是否相同。如果下列任何一项成立，则两个值相同：

- 两个值都是 `undefined`
- 两个值都是 `null`
- 两个值都是 `true` 或者都是 `false`
- 两个值是由相同个数的字符按照相同的顺序组成的字符串
- 两个值指向同一个对象
- 两个值都是数字并且
    - 都是正零 `+0`
    - 都是负零 `-0`
    - 都是 `NaN`
    - 都是除零和 `NaN` 外的其它同一个数字

这种相等性判断逻辑和传统的 `==` 运算不同，`==` 运算符会对它两边的操作数做隐式类型转换（如果它们类型不同），然后才进行相等性比较，（所以才会有类似 `""` `==` `false` 等于
`true` 的现象），但 O`bject.is` 不会做这种类型转换。

这与 `===` 运算符的判定方式也不一样。`===` 运算符（和 `==` 运算符）将数字值 `-0` 和 `+0` 视为相等，并认为
[`Number.NaN`](/zh-hans/webfrontend/Number) 不等于 `NaN`。

## 示例

```javascript
bject.is('foo', 'foo');     // true
Object.is(window, window);   // true

Object.is('foo', 'bar');     // false
Object.is([], []);           // false

var foo = { a: 1 };
var bar = { a: 1 };
Object.is(foo, foo);         // true
Object.is(foo, bar);         // false

Object.is(null, null);       // true

// 特例
Object.is(0, -0);            // false
Object.is(0, +0);            // true
Object.is(-0, -0);           // true
Object.is(NaN, 0/0);         // true
```

## Polyfill

```javascript
if (!Object.is) {
  Object.is = function(x, y) {
    // SameValue algorithm
    if (x === y) { // Steps 1-5, 7-10
      // Steps 6.b-6.e: +0 != -0
      return x !== 0 || 1 / x === 1 / y;
    } else {
      // Step 6.a: NaN == NaN
      return x !== x && y !== y;
    }
  };
}
```
