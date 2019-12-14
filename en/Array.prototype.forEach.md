TOPICS: Array.prototype.forEach
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.forEach()`

The `forEach()` method executes a provided function once for each array element.

## Syntax

```html
arr.forEach(callback(currentValue [, index [, array]])[, thisArg]);
```

| parameter | Description |
| :-- | :-- |
| `callback` | Function to execute on each element, taking three arguments:<br>**`element`**<br>The current element being processed in the array.<br>**`index`** Optional<br>The index of the current element being processed in the array.<br>**`array`** Optional<br>TThe array `forEach()` was called upon.
| `thisValue` | Value to use as `this` when executing `callback`. |

**Return value**：undefined

## Description

`forEach()` calls a provided `callback` function once for each element in an array in ascending order.
It is not invoked for index properties that have been deleted or are uninitialized (i.e. on sparse
arrays, see example below).

`callback` is invoked with three arguments:

1. the value of the element
1. the index of the element
1. the Array object being traversed

If a `thisArg` parameter is provided to `forEach()`, it will be used as `callback`'s `this` value.
The `this` value ultimately observable by `callback` is determined according to the usual rules for
determining the `this` seen by a function.

The range of elements processed by `forEach()` is set before the first invocation of `callback`.
Elements which are appended to the array after the call to `forEach()` begins will not be visited by
`callback`. If existing elements of the array are changed or deleted, their value as passed to
`callback` will be the value at the time `forEach()` visits them; elements that are deleted before
being visited are not visited. If elements that are already visited are removed (e.g. using
[`shift()`](/en/webfrontend/Array.prototype.shift)) during the iteration, later elements will be
skipped - see example below.

`forEach()` executes the `callback` function once for each array element; unlike [`map()`](/en/webfrontend/Array.prototype.map)
or [`reduce()`](/en/webfrontend/Array.prototype.reduce) it always returns the value [`undefined`](/en/webfrontend/undefined)
and is not chainable. The typical use case is to execute side effects at the end of a chain.

`forEach()` does not mutate the array on which it is called (although `callback`,
if invoked, may do so).

!!! warn ""
    There is no way to stop or break a `forEach()` loop other than by throwing an exception.
    If you need such behavior, the `forEach()` method is the wrong tool.
    Early termination may be accomplished with:
    1. A simple `for` loop
    2. A `for...of` / `for...in` loops
    3. [`Array.prototype.every()`](/en/webfrontend/Array.prototype.every)
    4. [`Array.prototype.some()`](/en/webfrontend/Array.prototype.some)
    5. [`Array.prototype.find()`](/en/webfrontend/Array.prototype.find)
    6. [`Array.prototype.findIndex()`](/en/webfrontend/Array.prototype.findIndex)
    Array methods: [`every()`](/en/webfrontend/Array.prototype.every),
    [`some()`](/en/webfrontend/Array.prototype.some), [`find()`](/en/webfrontend/Array.prototype.find),
    and [`findIndex()`](/en/webfrontend/Array.prototype.findIndex) test the array elements with a
    predicate returning a truthy value to determine if further iteration is required.

## Examples

### No operation for uninitialized values (sparse arrays)

如你所见，`3` 和 `7` 之间空缺的数组单元未被 `forEach()` 调用 `callback` 函数，或进行任何其他操作。

```javascript
const arraySparse = [1,3,,7];
let numCallbackRuns = 0;

arraySparse.forEach(function(element){
  console.log(element);
  numCallbackRuns++;
});

console.log("numCallbackRuns: ", numCallbackRuns);

// 1
// 3
// 7
// numCallbackRuns: 3
// comment: as you can see the missing value between 3 and 7 didn't invoke callback function.
```

### Converting a for loop to forEach

```javascript
const items = ['item1', 'item2', 'item3'];
const copy = [];

// before
for (let i=0; i<items.length; i++) {
  copy.push(items[i]);
}

// after
items.forEach(function(item){
  copy.push(item);
});
```

### Printing the contents of an array

!!! warn ""
    Note: In order to display the content of an array in the console, you can use [`console.table()`](/en/webfrontend/console.table)
    which will print a formatted version of the array. The following example illustrates another
    way of doing so, using forEach().

The following code logs a line for each element in an array:

```javascript
function logArrayElements(element, index, array) {
  console.log('a[' + index + '] = ' + element);
}

// Notice that index 2 is skipped since there is no item at
// that position in the array.
[2, 5, , 9].forEach(logArrayElements);
// logs:
// a[0] = 2
// a[1] = 5
// a[3] = 9
```

### Using `thisArg`

The following (contrived) example updates an object's properties from each entry in the array:

```javascript
function Counter() {
  this.sum = 0;
  this.count = 0;
}
Counter.prototype.add = function(array) {
  array.forEach(function(entry) {
    this.sum += entry;
    ++this.count;
  }, this);
  // ^---- Note
};

const obj = new Counter();
obj.add([2, 5, 9]);
obj.count;
// 3
obj.sum;
// 16
```

Since the `thisArg` parameter (`this`) is provided to `forEach()`, it is passed to `callback` each
time it's invoked, for use as its `this` value.

!!! warn ""
    If passing the function argument using an arrow function expression the `thisArg` parameter can
    be omitted as arrow functions lexically bind the `this` value.

### An object copy function

The following code creates a copy of a given object. There are different ways to create a copy of
an object; the following is just one way and is presented to explain how `Array.prototype.forEach()`
works by using ECMAScript 5 `Object.*` meta property functions.

```javascript
function copy(obj) {
  const copy = Object.create(Object.getPrototypeOf(obj));
  const propNames = Object.getOwnPropertyNames(obj);

  propNames.forEach(function(name) {
    const desc = Object.getOwnPropertyDescriptor(obj, name);
    Object.defineProperty(copy, name, desc);
  });

  return copy;
}

const obj1 = { a: 1, b: 2 };
const obj2 = copy(obj1); // obj2 looks like obj1 now
```

If the array is modified during iteration, other elements might be skipped.

The following example logs "one", "two", "four". When the entry containing the value "two" is
reached, the first entry of the whole array is shifted off, which results in all remaining
entries moving up one position. Because element "four" is now at an earlier position in the array,
"three" will be skipped. `forEach()` does not make a copy of the array before iterating.

```javascript
var words = ['one', 'two', 'three', 'four'];
words.forEach(function(word) {
  console.log(word);
  if (word === 'two') {
    words.shift();
  }
});
// one
// two
// four
```

### Flatten an array

The following example is only here for learning purpose. If you want to flatten an array using
built-in methods you can use [`Array.prototype.flat()`](/en/webfrontend/Array.prototype.flat)
(expected to be part of ES2019 and already implemented in some browsers).

```javascript
/**
 * Flattens passed array in one dimensional array
 *
 * @params {array} arr
 * @returns {array}
 */
function flatten(arr) {
  const result = []

  arr.forEach((i) => {
    if (Array.isArray(i)) {
      result.push(...flatten(i))
    } else {
      result.push(i)
    }
  })
  
  return result
}

// Usage
const problem = [1, 2, 3, [4, 5, [6, 7], 8, 9]]

flatten(problem) // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

## Note regarding usage of promise or async function

```javascript
let ratings = [5, 4, 5]

let sum = 0

let sumFunction = async function (a, b)
{
    return a + b
}

ratings.forEach(async function(rating) {
    sum = await sumFunction(sum, rating)
})

console.log(sum)
// Expected output: 14
// Actual output: 0
```
