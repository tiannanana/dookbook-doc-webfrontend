TOPICS: Boolean.valueOf

# `Boolean.valueOf()`

`valueOf()` 方法返回一个[`Boolean`对象](/zh-hans/webfrontend/Boolean)的原始值。

## 语法

```javascript
bool.valueOf()
```

**参数**: 没有参数

**返回类型**: 给定`Boolean`对象的原始值

## 描述

[`Boolean`](/zh-hans/webfrontend/Boolean)的`valueOf()`方法返回一个[`Boolean`对象](/zh-hans/webfrontend/Boolean)或[`Boolean`](/zh-hans/webfrontend/Boolean)字面量的原始值作为[布尔数据类型](/zh-hans/glossary/Boolean)。

该方法通常在JavaScript内部调用，而不是在代码中显式调用。

## 示例

```javascript
x = new Boolean();
myVar = x.valueOf()      // assigns false to myVar
```
