TOPICS: undefined

# JavaScript 全局属性: `undefined`

`undefined`是一个声明未定义的变量的初始值，或没有实际参数的形式参数。

## 语法

```javascript
undefined
```

## 描述

`undefined`是全局对象的一个属性。也就是说，它是**全局作用域**的一个变量。`undefined`的最初值就是基本数据类型`undefined`。

在现代浏览器自ECMAScript 5标准以来，`undefined`是一个不能被配置（non-configurable），不能被重写（non-writable）的属性。即便事实并非如此，也要避免去重写它。

一个没有被赋值的变量的类型是`undefined`。如果方法或者是语句中操作的变量没有返回值或被赋值，则会返回`undefined`。

## 严格相等和`undefined`

你可以使用`undefined`和严格相等或不相等操作符来决定一个变量是否拥有值。在下面的代码中，变量`x`是未定义的，`if`语句的求值结果将是`true`。

```javascript
var x;

if (x === undefined) {
    // 执行这些语句
} else {
    // 这些语句不会被执行
}
```

## `typeof`操作符和`undefined`

或者，可以使用`typeof`：

```javascript
// x之前未定义
var x;
if(typeof x === 'undefined') {  // 没有错误，执行结果为true
    // 执行这些语句
}

// 使用typeof的原因是它不会在一个变量没有被声明的时候抛出一个错误
if (x === undefined) {  // ReferenceError: x is not defined

}
```

## `void`操作符和`undefined`

```javascript
var x;
if(x === void 0) {
    // 执行这些语句
}

// 没有声明y
if(y === void 0) {
    // 抛出一个ReferenceError错误(与`typeof`相比)
}
```
