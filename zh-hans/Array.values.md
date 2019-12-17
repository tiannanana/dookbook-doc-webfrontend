TOPICS: Array.values
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.values()`

`values()` 方法返回一个新的 **`Array Iterator`** 对象，该对象包含数组每个索引的值

## 语法

```javascript
arr.values()
```

**返回类型**: 一个新的 `Array` 迭代对象。

## 描述

## 示例

### 使用 `for...of` 循环进行迭代

```javascript
let arr = ['w', 'y', 'k', 'o', 'p'];
let eArr = arr.values();
// 您的浏览器必须支持 for..of 循环
// 以及 let —— 将变量作用域限定在 for 循环中
for (let letter of eArr) {
  console.log(letter);
}
```

**`Array.values`** 是 **`Array [Symbol.iterator]`** 的默认实现。

```javascript
Array.values === Array[Symbol.iterator]
```

### 使用`.next()`迭代

```javascript
var arr = ['a', 'b', 'c', 'd', 'e'];
var iterator = arr.values();
iterator.next();               // Object { value: "a", done: false }
iterator.next().value;         // "b"
iterator.next()["value"];      // "c"
iterator.next();               // Object { value: "d", done: false }
iterator.next();               // Object { value: "e", done: false }
iterator.next();               // Object { value: undefined, done: true }
iteraroe.next().value;         // undefined
```

!!! error "一种用途"
    数组迭代器对象是一种用途或临时对象

```javascript
var arr = ['a', 'b', 'c', 'd', 'e'];
 var iterator = arr.values();
 for (let letter of iterator) {
 console.log(letter);
} //"a" "b" "c" "d"
for (let letter of iterator) {
console.log(letter);
} // undefined
```

**原因**：当`next().done=true`或`currentIndex>length`时，`for..of`循环结束。 请参阅迭代协议。

**值**：数组Iterator对象中没有存储任何值，而是它存储了用于创建它的数组的地址，因此它取决于存储在该数组中的值。

```javascript
var arr = ['a', 'b', 'c', 'd', 'e'];
var iterator = arr.values();
console.log(iterator);        // Array Iterator {  }
iterator.next().value;        // "a"
arr[1]='n';
iterator.next().value;        //  "n"
```

如果数组中的值更改，则数组迭代器对象的值也更改

TODO：请写出为什么我们需要它，用例。
