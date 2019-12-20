TOPICS: Array.filter
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.filter()`

The `filter()` method creates a new array with all elements that pass the test implemented by the
provided function.

## Syntax

```javascript
var newArray = arr.filter(callback(element[, index[, array]])[, thisArg])
```

| parameter | Description |
| :-- | :-- |
| `callback` | Function is a predicate, to test each element of the array. Return true to keep the element, false otherwise. It accepts three arguments:<br><br>**`element`**<br>The current element being processed in the array.<br><br>**`index`** Optional<br>The index of the current element being processed in the array.<br>**`array`** Optional<br>The array filter was called upon.
| `thisValue` | Optional, Value to use as this when executing callback. |

**Return value**：A new array with the elements that pass the test. If no elements pass the test, an
empty array will be returned.

## Description

`filter()` calls a provided `callback` function once for each element in an array, and constructs a
new array of all the values for which `callback` returns a value that coerces to `true`. `callback` is
invoked only for indexes of the array which have assigned values; it is not invoked for indexes
which have been deleted or which have never been assigned values. Array elements which do not pass
the callback test are simply skipped, and are not included in the new array.

`callback` is invoked with three arguments:

1. the value of the element
1. the index of the element
1. the Array object being traversed

If a `thisArg` parameter is provided to `filter`, it will be used as the callback's `this` value.
Otherwise, the value `undefined` will be used as its `this` value. The `this` value ultimately
observable by `callback` is determined according to the usual rules for determining the `this` seen
by a function.

`filter()` does not mutate the array on which it is called.

The range of elements processed by `filter()` is set before the first invocation of `callback`.
Elements which are appended to the array after the call to `filter()` begins will not be visited by
`callback`. If existing elements of the array are changed, or deleted, their value as passed to
`callback` will be the value at the time `filter()` visits them; elements that are deleted are not visited.

## Examples

### Filtering out all small values

The following example uses `filter()` to create a filtered array that has all elements with values
less than `10` removed.

```javascript
function isBigEnough(value) {
  return value >= 10;
}

var filtered = [12, 5, 8, 130, 44].filter(isBigEnough);
// filtered is [12, 130, 44]
```

### Filtering invalid entries from JSON

The following example uses `filter()` to create a filtered JSON of all elements with non-zero,
numeric `id`.

```javascript
var arr = [
  { id: 15 },
  { id: -1 },
  { id: 0 },
  { id: 3 },
  { id: 12.2 },
  { },
  { id: null },
  { id: NaN },
  { id: 'undefined' }
];

var invalidEntries = 0;

function isNumber(obj) {
  return obj !== undefined && typeof(obj) === 'number' && !isNaN(obj);
}

function filterByID(item) {
  if (isNumber(item.id) && item.id !== 0) {
    return true;
  }
  invalidEntries++;
  return false;
}

var arrByID = arr.filter(filterByID);

console.log('Filtered Array\n', arrByID);
// Filtered Array
// [{ id: 15 }, { id: -1 }, { id: 3 }, { id: 12.2 }]

console.log('Number of Invalid Entries = ', invalidEntries);
// Number of Invalid Entries = 5
```

### Searching in array

Following example uses `filter()` to filter array content based on search criteria

```javascript
var fruits = ['apple', 'banana', 'grapes', 'mango', 'orange'];

/**
 * Array filters items based on search criteria (query)
 */
function filterItems(query) {
  return fruits.filter(function(el) {
      return el.toLowerCase().indexOf(query.toLowerCase()) > -1;
  })
}

console.log(filterItems('ap')); // ['apple', 'grapes']
console.log(filterItems('an')); // ['banana', 'mango', 'orange']
```

ES2015 Implementation

```javascript
const fruits = ['apple', 'banana', 'grapes', 'mango', 'orange'];

/**
 * Array filters items based on search criteria (query)
 */
const filterItems = (query) => {
  return fruits.filter((el) =>
    el.toLowerCase().indexOf(query.toLowerCase()) > -1
  );
}

console.log(filterItems('ap')); // ['apple', 'grapes']
console.log(filterItems('an')); // ['banana', 'mango', 'orange']
```

## Affecting Initial Array (modifying, appending and deleting)

The following examples tests the behavior of the `filter` method when the array is modified.

```javascript
// Modifying each words
let words = ['spray', 'limit', 'exuberant', 'destruction','elite', 'present'];
const modifiedWords = words.filter((word,index,arr)=>{
  arr[index+1]+=' extra'
  return word.length < 6
})
console.log(modifiedWords)
// Notice there are three words below length 6, but since they've been modified one is returned
// ["spray"]

// Appending new words
words = ['spray', 'limit', 'exuberant', 'destruction','elite', 'present'];
const appendedWords = words.filter((word,index,arr)=>{
  arr.push('new')
  return word.length < 6
})
console.log(appendedWords)
// Only three fits the condition even though the `words` itself now has a lot more words with character length less than 6
// ["spray" ,"limit" ,"elite"]

// Deleting words
words = ['spray', 'limit', 'exuberant', 'destruction','elite', 'present'];
const deleteWords = words.filter((word,index,arr)=>{
  arr.pop()
  return word.length < 6
})
console.log(deleteWords)
// Notice 'elite' is not even obtained as its been popped off `words` before filter can even get there
// ["spray" ,"limit"]
```

## Polyfill

`filter()` was added to the ECMA-262 standard in the 5th edition; as such it may not be present in all
implementations of the standard. You can work around this by inserting the following code at
the beginning of your scripts, allowing use of `filter()` in ECMA-262 implementations which do not
natively support it. This algorithm is exactly equivalent to the one specified in ECMA-262, 5th
edition, assuming that `fn.call` evaluates to the original value of
[`Function.bind()`](/en/webfrontend/Function.bind), and that
[`Array.push()`](/en/webfrontend/Array.push) has its original value.

```javascript
if (!Array.prototype.filter){
  Array.prototype.filter = function(func, thisArg) {
    'use strict';
    if ( ! ((typeof func === 'Function' || typeof func === 'function') && this) )
        throw new TypeError();

    var len = this.length >>> 0,
        res = new Array(len), // preallocate array
        t = this, c = 0, i = -1;
    if (thisArg === undefined){
      while (++i !== len){
        // checks to see if the key was set
        if (i in this){
          if (func(t[i], i, t)){
            res[c++] = t[i];
          }
        }
      }
    }
    else{
      while (++i !== len){
        // checks to see if the key was set
        if (i in this){
          if (func.call(thisArg, t[i], i, t)){
            res[c++] = t[i];
          }
        }
      }
    }

    res.length = c; // shrink down array to proper size
    return res;
  };
}
```
