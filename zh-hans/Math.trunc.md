TOPICS: Math.trunc
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.trunc()`

**`Math.trunc()`** 方法会将数字的小数部分去掉，只保留整数部分。

## 语法

```javascript
Math.trunc(value)
```

| 参数 | 说明 |
| :-- | :-- |
| `value` | 任意数字 |

**返回值**: Number

## 描述

不像 [`Math`](/zh-hans/webfrontend/Math) 的其他三个方法： [`Math.floor()`](/zh-hans/webfrontend/Math.floor)、
[`Math.ceil()`](/zh-hans/webfrontend/Math.ceil)、[`Math.round()`](/zh-hans/webfrontend/Math.round)，
`Math.trunc()` 的执行逻辑很简单，仅仅是删除掉数字的小数部分和小数点，不管参数是正数还是负数。

传入该方法的参数会被隐式转换成数字类型。

因为 `trunc()` 是 [`Math`](/zh-hans/webfrontend/Math) 对象的静态方法，你必须用 `Math.trunc()` 来使用，而不是调用你创建的
[`Math`](/zh-hans/webfrontend/Math) 对象的一个实例方法（`Math` 没有构造函数）

## 示例

```javascript
Math.trunc(13.37)    // 13
Math.trunc(42.84)    // 42
Math.trunc(0.123)    //  0
Math.trunc(-0.123)   // -0
Math.trunc("-1.123") // -1
Math.trunc(NaN)      // NaN
Math.trunc("foo")    // NaN
Math.trunc()         // NaN
```

## Polyfill

```javascript
if (!Math.trunc) {
  Math.trunc = function(v) {
     v = +v;
     if (!isFinite(v)) return v;

      return (v - v % 1) || (v < 0 ? -0 : v === 0 ? v : 0);

      // 返回:
      //  0        ->  0
      // -0        -> -0
      //  0.2      ->  0
      // -0.2      -> -0
      //  0.7      ->  0
      // -0.7      -> -0
      //  Infinity ->  Infinity
      // -Infinity -> -Infinity
      //  NaN      ->  NaN
      //  null     ->  0
  };
}
```

或:

```javascript
if (!Math.trunc) {
   Math.trunc = function(v) {
      v = +v;
      return (v - v % 1) || (!isFinite(v) || v === 0 ? v : v < 0 ? -0 : 0);
   };
}
```
