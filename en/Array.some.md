TOPICS: Array.some
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.some()`

The `some()` method tests whether at least one element in the array passes the test implemented by
the provided function. It returns a Boolean value.

!!! warn "Note"
    This method returns `false` for any condition put on an empty array.

## Syntax

```javascript
arr.some(callback(element[, index[, array]])[, thisArg])
```

| parameter | Description |
| :-- | :-- |
| `callback` | A function to test for each element, taking three arguments:<br>**`element`**<br>The current element being processed in the array.<br><br>**`index`** Optional<br>The index of the current element being processed in the array.<br><br>**`array`** Optional<br>TThe array `some()` was called upon.
| `thisArg` Optional | A value to use as `this` when executing `callback`. |

**Return value**: `true` if the `callback` function returns a truthy value for at least one element
in the array. Otherwise, `false`.

## Description

The `some()` method executes the `callback` function once for each element present in the array
until it finds the one where `callback` returns a truthy value (a value that becomes `true` when
converted to a Boolean). If such an element is found, `some()` immediately returns `true`. Otherwise,
`some()` returns false. `callback` is invoked only for indexes of the array with assigned values.
It is not invoked for indexes which have been deleted or which have never been assigned values.

`callback` is invoked with three arguments: the value of the element, the index of the element,
and the Array object being traversed.

If a `thisArg` parameter is provided to `some()`, it will be used as the `callback`'s `this` value.
Otherwise, the value [`undefined`](/en/webfrontend/undefined) will be used as its `this` value.
The `this` value ultimately observable by `callback` is determined according to the usual rules
for determining the `this` seen by a function.

`some()` does not mutate the array on which it is called.

The range of elements processed by `some()` is set before the first invocation of callback.
Elements appended to the array after the call to `some()` begins will not be visited by callback.
If an existing, unvisited element of the array is changed by `callback`, its value passed to the
visiting `callback` will be the value at the time that some() visits that element's index.
Elements that are deleted are not visited.

## Examples

### Testing value of array elements

The following example tests whether any element in the array is bigger than `10`.

```javascript
function isBiggerThan10(element, index, array) {
  return element > 10;
}

[2, 5, 8, 1, 4].some(isBiggerThan10);  // false
[12, 5, 8, 1, 4].some(isBiggerThan10); // true
```

### Testing array elements using arrow functions

Arrow functions provide a shorter syntax for the same test.

```javascript
[2, 5, 8, 1, 4].some(x => x > 10); //false
[12, 5, 8, 1, 4].some(x => x > 10); // true
```

### Checking whether a value exists in an array

To mimic the function of the `includes()` method, `this` custom function returns true if the element
exists in the array:

```javascript
const fruits = ['apple', 'banana', 'mango', 'guava'];

function checkAvailability(arr, val) {
  return arr.some(function(arrVal) {
    return val === arrVal;
  });
}

checkAvailability(fruits, 'kela');   // false
checkAvailability(fruits, 'banana'); // true
```

### Checking whether a value exists using an arrow function

```javascript
const fruits = ['apple', 'banana', 'mango', 'guava'];

function checkAvailability(arr, val) {
  return arr.some(arrVal => val === arrVal);
}

checkAvailability(fruits, 'kela');   // false
checkAvailability(fruits, 'banana'); // true
```

### Converting any value to `Boolean`

```javascript
const TRUTHY_VALUES = [true, 'true', 1];

function getBoolean(value) {
  'use strict';

  if (typeof value === 'string') {
    value = value.toLowerCase().trim();
  }

  return TRUTHY_VALUES.some(function(t) {
    return t === value;
  });
}

getBoolean(false);   // false
getBoolean('false'); // false
getBoolean(1);       // true
getBoolean('true');  // true
```

## Polyfill

`some()` was added to the ECMA-262 standard in the 5th edition, and it may not be present in all
implementations of the standard. You can work around `this` by inserting the following code at the
beginning of your scripts, allowing use of some() in implementations which do not natively support
it. `This` algorithm is exactly the one specified in ECMA-262, 5th edition, assuming [`Object`](/en/webfrontend/Object)
and [`TypeError`](/en/webfrontend/TypeError) have their original values and that `fun.call`
evaluates to the original value of [`Function.call()`](/en/webfrontend/Function.call).
