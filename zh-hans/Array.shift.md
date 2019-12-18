TOPICS: Array.shift
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.shift()`

`shift()` 方法从数组中删除第一个元素，并返回该元素的值。此方法更改数组的长度。

## 语法

```javascript
arr.shift()
```

**参数**: 没有参数

**返回类型**: 从数组中删除的元素; 如果数组为空则返回`undefined`。

## 描述

`shift` 方法移除索引为 `0` 的元素(即第一个元素)，并返回被移除的元素，其他元素的索引值随之减 `1`。如果 `length` 属性的值为 `0` (长度为 `0`)，则返回 `undefined`。

`shift` 方法并不局限于数组：这个方法能够通过 [`call`](/zh-hans/webfrontend/Function.call) 或
u[`apply`](/zh-hans/webfrontend/Function.apply) 方法作用于类似数组的对象上。但是对于没有 `length` 属性（从`0`开始的一系列连续的数字属性的最后一个）的对象，调用该方法可能没有任何意义。

[`Array.pop()`](/zh-hans/webfrontend/Array.pop) 有着和 `shift`相似的行为, 但是是作用在数组的最后一个元素上的。

## 示例

### 移除数组中的一个元素

以下代码显示了删除其第一个元素之前和之后的myFish数组。它还显示已删除的元素：

```javascript
let myFish = ['angel', 'clown', 'mandarin', 'surgeon'];

console.log('调用 shift 之前: ' + myFish);
// "调用 shift 之前: angel,clown,mandarin,surgeon"

var shifted = myFish.shift();

console.log('调用 shift 之后: ' + myFish);
// "调用 shift 之后: clown,mandarin,surgeon"

console.log('被删除的元素: ' + shifted);
// "被删除的元素: angel"
```

```javascript
var myFish = ['angel', 'clown', 'mandarin', 'surgeon'];

console.log('myFish before:', JSON.stringify(myFish));
// myFish before: ['angel', 'clown', 'mandarin', 'surgeon']

var shifted = myFish.shift();

console.log('myFish after:', myFish);
// myFish after: ['clown', 'mandarin', 'surgeon']

console.log('Removed this element:', shifted);
// Removed this element: angel
```

### 在while循环中使用`shift()`

`shift()` 方法经常用于while loop的环境中.。下例中每个循环将要从一个数组中移除下一项元素，直至它成为空数组。

```javascript
var names = ["Andrew", "Edward", "Paul", "Chris" ,"John"];

while( (i = names.shift()) !== undefined ) {
    console.log(i);
}
// Andrew, Edward, Paul, Chris, John
```
