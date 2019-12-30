TOPICS: Object.isExtensible
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.isExtensible()`

**`Object.isExtensible()`** 方法判断一个对象是否是可扩展的（是否可以在它上面添加新的属性）。

## 语法

```javascript
Object.isExtensible(obj)
```

| 参数 | 说明 |
| :-- | :-- |
| `obj` | 需要检测的对象 |

**返回值**: 表示给定对象是否可扩展的一个 `Boolean` 。

## 描述

默认情况下，对象是可扩展的：即可以为他们添加新的属性。以及它们的 `__proto__` 属性可以被更改。
[`Object.preventExtensions`](/zh-hans/webfrontend/Object.preventExtensions)，
[`Object.seal`](/zh-hans/webfrontend/Object.seal) 或
[`Object.freeze`](/zh-hans/webfrontend/Object.freeze) 方法都可以标记一个对象为不可扩展（non-extensible）。

## 示例

```javascript
// 新对象默认是可扩展的.
var empty = {};
Object.isExtensible(empty); // === true

// ...可以变的不可扩展.
Object.preventExtensions(empty);
Object.isExtensible(empty); // === false

// 密封对象是不可扩展的.
var sealed = Object.seal({});
Object.isExtensible(sealed); // === false

// 冻结对象也是不可扩展.
var frozen = Object.freeze({});
Object.isExtensible(frozen); // === false
```
