TOPICS: Date.now
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.now()`

`Date.now()` 方法返回自1970年1月1日 `00:00:00 UTC`到当前时间的毫秒数。

## 语法

```javascript
var timeInMs = Date.now();
```

**参数**: 没有参数

## 描述

`now()`方法返回自1970年1月1日 `00:00:00 UTC`到当前时间的毫秒数，类型为[`Number`](/zh-hans/webfrontend/Number)。

因为 `now()` 是[`Date`](/zh-hans/webfrontend/Date)的一个静态函数，所以必须以 `Date.now()` 的形式来使用。

## 兼容旧环境

该方法在 ECMA-262 第五版中被标准化，可以通过下面的代码来兼容那些不支持该方法的引擎。

```javascript
if (!Date.now) {
  Date.now = function now() {
    return new Date().getTime();
  };
}
```
