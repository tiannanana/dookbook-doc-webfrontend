TOPICS: Number.isInteger
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.isInteger()`

**`Number.isInteger()`** 方法用来判断给定的参数是否为整数。

## 语法

```javascript
Number.isInteger(value)
```

| 参数 | 说明 |
| :-- | :-- |
| `value` | 要判断此参数是否为整数 |

**返回值**: 判断给定值是否是整数的 `Boolean` 值。

## 描述

如果被检测的值是整数，则返回 `true`，否则返回 `false`。注意 `NaN` 和正负 `Infinity` 不是整数。

## 示例

```javascript
Number.isInteger(0);         // true
Number.isInteger(1);         // true
Number.isInteger(-100000);   // true

Number.isInteger(0.1);       // false
Number.isInteger(Math.PI);   // false

Number.isInteger(Infinity);  // false
Number.isInteger(-Infinity); // false
Number.isInteger("10");      // false
Number.isInteger(true);      // false
Number.isInteger(false);     // false
Number.isInteger([1]);       // false
```

## Polyfill

```javascript
Number.isInteger = Number.isInteger || function(value) {
  return typeof value === "number" &&
         isFinite(value) &&
         Math.floor(value) === value;
};
```
