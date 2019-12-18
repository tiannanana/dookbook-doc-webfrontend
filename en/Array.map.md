TOPICS: Array.map
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.map()`

The `map()` method **creates a new array** with the results of calling a provided function on every
element in the calling array.

## Syntax

```javascript
var new_array = arr.map(function callback(currentValue[, index[, array]]) {
    // Return element for new_array
}[, thisArg])
```

| parameter | Description |
| :-- | :-- |
| `callback` | Function that produces an element of the new Array, taking three arguments:<br>**`currentValue`**<br>The current element being processed in the array.<br><br>**`index`** Optional<br>The index of the current element being processed in the array.<br><br>**`array`** Optional<br>The array `map` was called upon. |
| `thisValue` | Value to use as `this` when executing `callback`. |

**Return value**: A new array with each element being the result of the callback function.

## Description

`map` calls a provided `callback` function **once for each element** in an array, in order, and
constructs a new array from the results. `callback` is invoked only for indexes of the array
which have assigned values, including [`undefined`](/en/webfrontend/undefined). It is not called for
missing elements of the array (that is, indexes that have never been set, which have been deleted or
which have never been
assigned a value).

Since `map` builds a new array, using it when you aren't using the returned array is an anti-pattern;
use [`forEach`](/en/webfrontend/forEach) or [`for-of`](/en/webfrontend/for-of) instead. Signs you
shouldn't be using `map`: A) You're not using the array it returns, and/or B) You're not returning
a value from the `callback`.

`callback` is invoked with three arguments: the value of the element, the index of the element, and
the Array object being traversed.

If a thisArg parameter is provided to `map`, it will be used as `callback`'s this value. Otherwise,
the value [`undefined`](/en/webfrontend/undefined) will be used as its this value. The this value
ultimately observable by `callback` is determined according to the usual rules for determining
the this seen by a function.

`map` does not mutate the array on which it is called (although `callback`, if invoked, may do so).

The range of elements processed by `map` is set before the first invocation of `callback`. Elements
which are appended to the array after the call to `map` begins will not be visited by `callback`. If
existing elements of the array are changed, their value as passed to `callback` will be the value at
the time `map` visits them. Elements that are deleted after the call to `map` begins and before being
visited are not visited.

Due to the algorithm defined in the specification, if the array which `map` was called upon is sparse,
resulting array will also be sparse keeping same indices blank.

## Examples

### Mapping an array of numbers to an array of square roots

The following code takes an array of numbers and creates a new array containing the square roots
of the numbers in the first array.

```javascript
var numbers = [1, 4, 9];
var roots = numbers.map(function(num) {
return Math.sqrt(num)
});
// roots is now [1, 2, 3]
// numbers is still [1, 4, 9]
```

### Using `map` to reformat objects in an array

The following code takes an array of objects and creates a new array containing the newly
reformatted objects.

```javascript
var kvArray = [{key: 1, value: 10},
               {key: 2, value: 20},
               {key: 3, value: 30}];

var reformattedArray = kvArray.map(obj =>{
   var rObj = {};
   rObj[obj.key] = obj.value;
   return rObj;
});
// reformattedArray is now [{1: 10}, {2: 20}, {3: 30}],

// kvArray is still:
// [{key: 1, value: 10},
//  {key: 2, value: 20},
//  {key: 3, value: 30}]
```

Mapping an array of numbers using a function containing an argument

The following code shows how `map` works when a function requiring one argument is used with it. The
argument will automatically be assigned from each element of the array as `map` loops through the
original array.

```javascript
var numbers = [1, 4, 9];
var doubles = numbers.map(function(num) {
  return num * 2;
});

// doubles is now [2, 8, 18]
// numbers is still [1, 4, 9]
```

### Using `map` generically

This example shows how to use `map` on a [`String`](/en/webfrontend/String) to get an array of
bytes in the ASCII encoding
representing the character values:

```javascript
var map = Array.prototype.map;
var a = map.call('Hello World', function(x) {
  return x.charCodeAt(0);
});
// a now equals [72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100]
```

### Using `map` generically `querySelectorAll`

This example shows how to iterate through a collection of objects collected by `querySelectorAll`.
This is because `querySelectorAll` returns a NodeList which is a collection of objects.
In this case we return all the selected options' values on the screen:

```javascript
var elems = document.querySelectorAll('select option:checked');
var values = Array.prototype.map.call(elems, function(obj) {
  return obj.value;
});
```

Easier way would be using Array.from() method.

### Tricky use case

([inspired by this blog post](http://www.wirfs-brock.com/allen/posts/166))

It is common to use the callback with one argument (the element being traversed). Certain functions
are also commonly used with one argument, even though they take additional optional arguments.
These habits may lead to confusing behaviors.

Consider:

```javascript
["1", "2", "3"].map(parseInt);
```

While one could expect `[1, 2, 3]`, The actual result is `[1, NaN, NaN]`.

parseInt is often used with one argument, but takes two. The first is an expression and the second
is the radix to the callback function, `Array.map` passes 3 arguments:

- the element
- the index
- the array

The third argument is ignored by parseInt, but not the second one, hence the possible confusion.
Here is concise example of the iteration steps:

```javascript
// parseInt(string, radix) -> map(parseInt(value, index))
/*  first iteration (index is 0): */ parseInt("1", 0); // 1
/*  second iteration (index is 1): */ parseInt("2", 1); // NaN
/*  third iteration (index is 2): */ parseInt("3", 2); // NaN
```

Then let's talk about solutions.

```javascript
function returnInt(element) {
  return parseInt(element, 10);
}

['1', '2', '3'].map(returnInt); // [1, 2, 3]
// Actual result is an array of numbers (as expected)

// Same as above, but using the concise arrow function syntax
['1', '2', '3'].map( str => parseInt(str) );

// A simpler way to achieve the above, while avoiding the "gotcha":
['1', '2', '3'].map(Number); // [1, 2, 3]

// But unlike parseInt(), Number() will also return a float or (resolved) exponential notation:
['1.1', '2.2e2', '3e300'].map(Number); // [1.1, 220, 3e+300]
// For comparison, if we use parseInt() on the array above:
['1.1', '2.2e2', '3e300'].map( str => parseInt(str) ); // [1, 2, 3]
```

One alternative output of the `map` method being called with parseInt as a parameter runs as follows:

```javascript
var xs = ['10', '10', '10'];

xs = xs.map(parseInt);

console.log(xs);
// Actual result of 10,NaN,2 may be unexpected based on the above description.
```

### Mapped array contains undefined

When undefined or nothing is returned:

```javascript
var numbers = [1, 2, 3, 4];
var filteredNumbers = numbers.map(function(num, index) {
  if (index < 3) {
     return num;
  }
});
// index goes from 0, so the filterNumbers are 1,2,3 and undefined.
// filteredNumbers is [1, 2, 3, undefined]
// numbers is still [1, 2, 3, 4]
```

## Polyfill

`map` was added to the ECMA-262 standard in the 5th edition; as such it may not be present in all
implementations of the standard. You can work around this by inserting the following code at the
beginning of your scripts, allowing use of `map` in implementations which do not natively support
it. This algorithm is exactly the one specified in ECMA-262, 5th edition, assuming [`Object`](/en/webfrontend/Object),
[`TypeError`](/en/webfrontend/TypeError), and [`Array`](/en/webfrontend/Array) have their
original values and that callback.call evaluates to the
original value of [`Function.call`](/en/webfrontend/Function.call).

```javascript
// Production steps of ECMA-262, Edition 5, 15.4.4.19
// Reference: http://es5.github.io/#x15.4.4.19
if (!Array.prototype.map) {

  Array.prototype.map = function(callback/*, thisArg*/) {

    var T, A, k;

    if (this == null) {
      throw new TypeError('this is null or not defined');
    }

    // 1. Let O be the result of calling ToObject passing the |this|
    //    value as the argument.
    var O = Object(this);

    // 2. Let lenValue be the result of calling the Get internal
    //    method of O with the argument "length".
    // 3. Let len be ToUint32(lenValue).
    var len = O.length >>> 0;

    // 4. If IsCallable(callback) is false, throw a TypeError exception.
    // See: http://es5.github.com/#x9.11
    if (typeof callback !== 'function') {
      throw new TypeError(callback + ' is not a function');
    }

    // 5. If thisArg was supplied, let T be thisArg; else let T be undefined.
    if (arguments.length > 1) {
      T = arguments[1];
    }

    // 6. Let A be a new array created as if by the expression new Array(len)
    //    where Array is the standard built-in constructor with that name and
    //    len is the value of len.
    A = new Array(len);

    // 7. Let k be 0
    k = 0;

    // 8. Repeat, while k < len
    while (k < len) {

      var kValue, mappedValue;

      // a. Let Pk be ToString(k).
      //   This is implicit for LHS operands of the in operator
      // b. Let kPresent be the result of calling the HasProperty internal
      //    method of O with argument Pk.
      //   This step can be combined with c
      // c. If kPresent is true, then
      if (k in O) {

        // i. Let kValue be the result of calling the Get internal
        //    method of O with argument Pk.
        kValue = O[k];

        // ii. Let mappedValue be the result of calling the Call internal
        //     method of callback with T as the this value and argument
        //     list containing kValue, k, and O.
        mappedValue = callback.call(T, kValue, k, O);

        // iii. Call the DefineOwnProperty internal method of A with arguments
        // Pk, Property Descriptor
        // { Value: mappedValue,
        //   Writable: true,
        //   Enumerable: true,
        //   Configurable: true },
        // and false.

        // In browsers that support Object.defineProperty, use the following:
        // Object.defineProperty(A, k, {
        //   value: mappedValue,
        //   writable: true,
        //   enumerable: true,
        //   configurable: true
        // });

        // For best browser support, use the following:
        A[k] = mappedValue;
      }
      // d. Increase k by 1.
      k++;
    }

    // 9. return A
    return A;
  };
}
```
