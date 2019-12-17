TOPICS: Boolean.prototype.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Boolean.prototype.toString()`

`toString()` 方法返回指定的布尔对象的字符串形式。

## 语法

```javascript
bool.toString()
```

**参数**: 没有参数

**返回类型**: 表示特定`Boolean`对象的字符串。

## 描述

[`Boolean`](/zh-hans/webfrontend/Boolean_Object) 对象覆盖了 [`Object`](/zh-hans/webfrontend/Object) 对象的
`toString` 方法。并没有继承 [`Object.prototype.toString()`](/zh-hans/webfrontend/Object.prototype.toString)。对于布尔对象，`toString`
方法返回该对象的字符串形式。

当一个[`Boolean`](/zh-hans/webfrontend/Boolean_Object)对象作为文本值或进行字符串连接时，JavaScript 会自动调用其 `toString` 方法。

对于[`Boolean`](/zh-hans/webfrontend/Boolean_Object)对象或值，内置的 `toString` 方法返回字符串 "`true`" 或 "`false`"，具体返回哪个取决于布尔对象的值。

## 示例

### 使用 `toString`

下面的代码，`flag.toString` 返回 "`true`"：

```javascript
var flag = new Boolean(true)
var myVar = flag.toString()
```
