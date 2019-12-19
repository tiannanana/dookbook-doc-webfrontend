TOPICS: null

# JavaScript Null对象: `null`

值`null`特指对象的值未设置。它是*[[JavaScript]]* *基本类型*之一，且在布尔操作中被认为是**假**值。

## 语法

```javascript
null
```

## 描述

值`null`是一个字面量，不像[[`undefined`]](/zh-hans/webfrontend/undefined)，它不是全局对象的一个属性。`null`是表示缺少的标识，
指示变量未指向任何对象。把`null`作为尚未创建的对象，也许更好理解。在API中，`null`常在返回类型应是一个对象，但没有关联的值的地方使用。

```javascript
// foo不存在，既没有定义，也没有初始化：
foo;
"ReferenceError: foo is not defined"

// foo存在但是没有指定类型或值：
var foo = null;
foo;
"null"
```

## `null`和`undefined`的区别

当检测`null`或`undefined`时，注意相等（`==`）与全等（`===`）两个操作符的区别，前者会执行类型转换：

```javascript
typeof null          // "object" (因为历史原因而不是'null')
typeof undefined     // "undefined"
null === undefined   // false
null  == undefined   // true
null === null        // true
null == null         // true
!null                // true
isNaN(1 + null)      // false
isNaN(1 + undefined) // true
```

## 更多

- [Null术语](/zh-hans/glossary/Null)
