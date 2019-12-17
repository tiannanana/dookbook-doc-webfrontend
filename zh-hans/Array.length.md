TOPICS: Array.length
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.length`

`Array.length` 是`Array`的实例属性。返回或设置一个数组中的元素个数。该值是一个无符号 32-bit 整数，并且总是大于数组最高项的下标。

**返回值**：一个数字，表示数组中的对象的元素数目。

## 描述

`length` 属性的值是一个 `0` 到 2^32^-1 的整数。

```javascript
var namelistA = new Array(4294967296); // 2的32次方 = 4294967296
var namelistC = new Array(-100) // 负号

console.log(namelistA.length); // RangeError: 无效数组长度
console.log(namelistC.length); // RangeError: 无效数组长度

var namelistB = [];
namelistB.length = Math.pow(2,32)-1; //set array length less than 2 to the 32nd power
console.log(namelistB.length);

// 4294967295
```

你可以设置 `length` 属性的值来截断任何数组。当通过改变`length`属性值来扩展数组时，实际元素的数目将会增加。例如：将一个拥有 `2` 个元素的数组的 `length` 属性值设为
`3` 时，那么这个数组将会包含3个元素，并且，第三个元素的值将会是 `undefined` 。

```javascript
var arr = [1, 2, 3];
printEntries(arr);

arr.length = 5; // set array length to 5 while currently 3.
printEntries(arr);

function printEntries(arr) {
  var goNext = true;
  var entries = arr.entries();
  while (goNext) {
    var result = entries.next();
    if (result.done !== true) {
      console.log(result.value[1]);
      goNext = true;
    } else
      goNext = false;
  }
  console.log('=== printed ===');
}

// 1
// 2
// 3
// === printed ===
// 1
// 2
// 3
// undefined
// undefined
// === printed ===
```

但是，`length` 属性不一定表示数组中定义值的个数。了解更多：[长度与数值下标属性之间的关系](/zh-hans/webfrontend/Array)。

`Array.length` 属性的属性特性：

|  |  |
| :--- | :--- |
| `writable` | `true` |
| `enumerable` | `false` |
| `configurable` | `false` |

- `Writable` ：如果设置为`false`，该属性值将不能被修改。
- `Configurable` ：如果设置为`false`，删除或更改任何属性都将会失败。
- `Enumerable` ：如果设置为`true`，属性可以通过迭代器`for`或`for...in`进行迭代。

## 示例

### 遍历数组

下面的例子中，通过数组下标遍历数组元素，并把每个元素的值修改为原值的2倍。

```javascript
var numbers = [1, 2, 3, 4, 5];
var length = numbers.length;
for (var i = 0; i < length; i++) {
  numbers[i] *= 2;
}
// 遍历后的结果 [2, 4, 6, 8, 10]
```

### 截断数组

下面的例子中，如果数组长度大于 `3`，则把该数组的长度截断为 `3` 。

```javascript
var numbers = [1, 2, 3, 4, 5];

if (numbers.length > 3) {
  numbers.length = 3;
}

console.log(numbers); // [1, 2, 3]
console.log(numbers.length); // 3
```
