TOPICS: Array.prototype.flatMap
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.flatMap()`

`flatMap()` 方法首先使用映射函数映射每个元素，然后将结果压缩成一个新数组。它与 [`map`](/zh-hans/webfrontend/Array.prototype.map)
连着深度值为1的 [`flat`](/zh-hans/webfrontend/Array.prototype.flat) 几乎相同，但 `flatMap` 通常在合并成一种方法的效率稍微高一些。

## 语法

```javascript
var new_array = arr.flatMap(function callback(currentValue[, index[, array]]) {
    // return element for new_array
}[, thisArg])
```

| 参数 | 说明 |
| :-- | :-- |
| `callback` | 可以生成一个新数组中的元素的函数，可以传入三个参数：<br>**`currentValue`**<br>当前正在数组中处理的元素<br><br>**`index`**<br>可选的。数组中正在处理的当前元素的索引。<br><br>**`array`**<br>可选的。被调用的 `map` 数组
| `thisArg` | 可选的。执行 `callback` 函数时 使用的this 值。

**返回类型**：一个新的数组，其中每个元素都是回调函数的结果，并且结构深度 depth 值为"`1`"。

## 示例

### `map()` 与 `flatMap()`

```javascript
var arr1 = [1, 2, 3, 4];

arr1.map(x => [x * 2]);
// [[2], [4], [6], [8]]

arr1.flatMap(x => [x * 2]);
// [2, 4, 6, 8]

// only one level is flattened
arr1.flatMap(x => [[x * 2]]);
// [[2], [4], [6], [8]]
```

虽然上面的代码使用 `map` 和 `flatMap` 好像都可以，但这只能展示如何使用 `flatMap`

所以，为了更好的展示 `flatMap` 的作用，下面我们将包含几句话的数组拆分成单个汉字组成的新数组。

```javascript
let arr1 = ["it's Sunny in", "", "California"];

arr1.map(x => x.split(" "));
// [["it's","Sunny","in"],[""],["California"]]

arr1.flatMap(x => x.split(" "));
// ["it's","Sunny","in", "", "California"]
```

注意，输出列表长度可以不同于输入列表长度。

### 在一个 `map()` 期间增加或去除一些项

`flatMap` 能用于在map期间增删项目（也就是修改items的数量）。换句话说，它允许你遍历很多项使之成为另一些项（靠分别把它们放进去来处理），而不是总是一对一。 从这个意义上讲，它的作用类似于
[`filter`](/zh-hans/webfrontend/Array.prototype.filter)的对立面。只需返回一个1项元素数组以保留该项，返回一个多元素数组以添加项，或返回一个0项元素数组以删除该项。

```javascript
// Let's say we want to remove all the negative numbers and split the odd numbers into an even number and a 1
let a = [5, 4, -3, 20, 17, -33, -4, 18]
//       |\  \  x   |  | \   x   x   |
//      [4,1, 4,   20, 16, 1,       18]

a.flatMap( (n) =>
  (n < 0) ?      [] :
  (n % 2 == 0) ? [n] :
                 [n-1, 1]
)

// expected output: [4, 1, 4, 20, 16, 1, 18]
```

## 替代方案

### `reduce()` 与 `concat()`

```javascript
var arr = [1, 2, 3, 4];

arr.flatMap(x => [x, x * 2]);
// is equivalent to
arr.reduce((acc, x) => acc.concat([x, x * 2]), []);
// [1, 2, 2, 4, 3, 6, 4, 8]
```

请注意，这是低效的，并且应该避免大型阵列：在每次迭代中，它创建一个必须被垃圾收集的新临时数组，并且它将元素从当前的累加器数组复制到一个新的数组中，而不是将新的元素添加到现有的数组中。
