TOPICS: Math.floor
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.floor()`

**`Math.floor()`** 返回小于或等于一个给定数字的最大整数。

!!! warn "Note"
    `Math.floor() ===` 向下取整

## 语法

```javascript
Math.floor(x)
```

| 参数 | 说明 |
| :-- | :-- |
| `x` | 一个数值 |

**返回值**: Number

## 描述

由于 `floor` 是 [`Math`](/zh-hans/webfrontend/Math) 的一个静态方法，你总是应该像这样使用它 `Math.floor()`，而不是作为你创建的一个
[`Math`](/zh-hans/webfrontend/Math) 对象的一种方法（`Math`不是一个构造函数）。

## 示例

### 使用 `Math.floor()`

```javascript
Math.floor( 45.95);
// 45
Math.floor( 45.05);
// 45
Math.floor( 4 );
// 4
Math.floor(-45.05);
// -46
Math.floor(-45.95);
// -46
```

### 十进制调整

```javascript
// Closure
(function(){

  /**
   * Decimal adjustment of a number.
   *
   * @param {String} type   The type of adjustment.
   * @param {Number} value  The number.
   * @param {Integer} exp   The exponent (the 10 logarithm of the adjustment base).
   * @returns {Number}      The adjusted value.
   */
  function decimalAdjust(type, value, exp) {
    // If the exp is undefined or zero...
    if (typeof exp === 'undefined' || +exp === 0) {
      return Math[type](value);
    }
    value = +value;
    exp = +exp;
    // If the value is not a number or the exp is not an integer...
    if (isNaN(value) || !(typeof exp === 'number' && exp % 1 === 0)) {
      return NaN;
    }
    // Shift
    value = value.toString().split('e');
    value = Math[type](+(value[0] + 'e' + (value[1] ? (+value[1] - exp) : -exp)));
    // Shift back
    value = value.toString().split('e');
    return +(value[0] + 'e' + (value[1] ? (+value[1] + exp) : exp));
  }

  // Decimal round
  if (!Math.round10) {
    Math.round10 = function(value, exp) {
      return decimalAdjust('round', value, exp);
    };
  }
  // Decimal floor
  if (!Math.floor10) {
    Math.floor10 = function(value, exp) {
      return decimalAdjust('floor', value, exp);
    };
  }
  // Decimal ceil
  if (!Math.ceil10) {
    Math.ceil10 = function(value, exp) {
      return decimalAdjust('ceil', value, exp);
    };
  }

})();

// Round
Math.round10(55.55, -1); // 55.6
Math.round10(55.549, -1); // 55.5
Math.round10(55, 1); // 60
Math.round10(54.9, 1); // 50
Math.round10(-55.55, -1); // -55.5
Math.round10(-55.551, -1); // -55.6
Math.round10(-55, 1); // -50
Math.round10(-55.1, 1); // -60
// Floor
Math.floor10(55.59, -1); // 55.5
Math.floor10(59, 1); // 50
Math.floor10(-55.51, -1); // -55.6
Math.floor10(-51, 1); // -60
// Ceil
Math.ceil10(55.51, -1); // 55.6
Math.ceil10(51, 1); // 60
Math.ceil10(-55.59, -1); // -55.5
Math.ceil10(-59, 1); // -50
```
