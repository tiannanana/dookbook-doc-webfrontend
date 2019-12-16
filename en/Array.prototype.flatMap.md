TOPICS: Array.prototype.flatMap
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.flatMap()`

The `flatMap()` method first maps each element using a mapping function, then flattens the result
into a new array. It is identical to a [`map()`](/en/webfrontend/Array.prototype.map) followed by a
[`flat()`](/en/webfrontend/Array.prototype.flat) of depth `1`, but `flatMap()` is often
quite useful, as merging both into one method is slightly more efficient.

## Syntax

```javascript
var new_array = arr.flatMap(function callback(currentValue[, index[, array]]) {
    // return element for new_array
}[, thisArg])
```

| parameter | Description |
| :-- | :-- |
| `callback` | Function that produces an element of the new Array, taking three arguments:<br>**`currentValue`**<br>The current element being processed in the array.<br><br>**`index`** Optional<br>The index of the current element being processed in the array.<br><br>**`array`** Optional<br>The array map was called upon.
| `thisArg` | Value to use as this when executing callback. |

**Return value**：A new array with each element being the result of the callback function and
flattened to a depth of `1`.

## Description

See [`Array.prototype.map()`](/en/webfrontend/Array.prototype.map) for a detailed description of
the callback function. The `flatMap` method is identical to a
[`map`](/en/webfrontend/Array.prototype.map) followed by a call to
[`flat`](/en/webfrontend/Array.prototype.flat) of depth `1`.

## Examples

### `map()` and `flatMap()`

```javascript
let arr1 = [1, 2, 3, 4];

arr1.map(x => [x * 2]);
// [[2], [4], [6], [8]]

arr1.flatMap(x => [x * 2]);
// [2, 4, 6, 8]

// only one level is flattened
arr1.flatMap(x => [[x * 2]]);
// [[2], [4], [6], [8]]
```

While the above could have been achieved by using map itself, here is an example that better
showcases the use of `flatMap`.

Let's generate a list of words from a list of sentences.

```javascript
let arr1 = ["it's Sunny in", "", "California"];

arr1.map(x => x.split(" "));
// [["it's","Sunny","in"],[""],["California"]]

arr1.flatMap(x => x.split(" "));
// ["it's","Sunny","in", "", "California"]
```

Notice, the output list length can be different from the input list length.

### For adding and removing items during a `map()`

`flatMap` can be used as a way to add and remove items (modify the number of items) during a `map`.
In other words, it allows you to map many items to many items (by handling each input item separately),
rather than always one-to-one. In this sense, it works like the opposite of [`filter`](/en/webfrontend/Array.prototype.filter).
Simply return a 1-element array to keep the item, a multiple-element array to add items, or a
0-element array to remove the item.

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

## Alternative

### `reduce()` and `concat()`

```javascript
var arr = [1, 2, 3, 4];

arr.flatMap(x => [x, x * 2]);
// is equivalent to
arr.reduce((acc, x) => acc.concat([x, x * 2]), []);
// [1, 2, 2, 4, 3, 6, 4, 8]
```

Note, however, that this is inefficient and should be avoided for large arrays: in each iteration,
it creates a new temporary array that must be garbage-collected, and it copies elements from the
current accumulator array into a new array instead of just adding the new elements to the existing array.
