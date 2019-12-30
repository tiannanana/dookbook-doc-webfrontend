TOPICS: Object.toLocaleString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.toLocaleString()`

**`toLocaleString()`** 方法返回一个该对象的字符串表示。此方法被用于派生对象为了特定语言环境的目的（locale-specific purposes）而重载使用。

## 语法

```javascript
obj.toLocaleString();
```

**参数**: 没有参数

**返回值**: 表示对象的字符串。

## 描述

[`Object`](/zh-hans/webfrontend/Object) `toLocaleString` 返回调用
[`toString()`](/zh-hans/webfrontend/Object.toString) 的结果。

该函数提供给对象一个通用的 `toLocaleString` 方法，即使不是全部都可以使用它。 见下面的列表。

### 覆盖 `toLocaleString` 的对象

- [`Array`](/zh-hans/webfrontend/Array): [`Array.toLocaleString()`](/zh-hans/webfrontend/Array.toLocaleString)
- [`Number`](/zh-hans/webfrontend/Number): [`Number.toLocaleString()`](/zh-hans/webfrontend/Number.toLocaleString)
- [`Date`](/zh-hans/webfrontend/Date): [`Date.toLocaleString()`](/zh-hans/webfrontend/Date.toLocaleString)
