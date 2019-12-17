TOPICS: Boolean.prototype.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Boolean.prototype.valueOf()`

`valueOf()` 方法返回一个[`Boolean`](/zh-hans/webfrontend/Boolean_Object)对象的原始值。

## 语法

```javascript
bool.valueOf()
```

**参数**: 没有参数

**返回类型**: 给定`Boolean`对象的原始值

## 描述

[`Boolean`](/zh-hans/webfrontend/Boolean_Object)的 `valueOf` 方法返回一个[`Boolean`](/zh-hans/webfrontend/Boolean_Object)对象或[`Boolean`](/zh-hans/webfrontend/Boolean_Object)字面量的原始值作为布尔数据类型。

该方法通常在 JavaScript 内部调用，而不是在代码中显式调用。

## 示例

### 使用`valueOf`

```javascript
x = new Boolean();
myVar = x.valueOf()      // assigns false to myVar
```
