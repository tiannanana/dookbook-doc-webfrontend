TOPICS: Float64Array
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Float64Array Object

The `Float64Array` typed array represents an array of 64-bit floating point numbers
(corresponding to the C double data type) in the platform byte order.
If control over byte order is needed, use [`DataView`](/en/webfrontend/DataView) instead.
The contents are initialized to `0`. Once established,
you can reference elements in the array using the object's methods,
or using standard array index syntax (that is, using bracket notation).

## Syntax

```JavaScript
new Float64Array(); // new in ES2017
new Float64Array(length);
new Float64Array(typedArray);
new Float64Array(object);
new Float64Array(buffer [, byteOffset [, length]]);
```

For more information about the constructor syntax and the parameters, see [`TypedArray`](/en/webfrontend/TypedArray).

## Properties

| Properties | Description |
| :-- | :-- |
|**[`Float64Array.BYTES_PER_ELEMENT`](/en/webfrontend/TypedArray.BYTES_PER_ELEMENT)**|Returns a number value of the element size. `4` in the case of an `Float64Array`.|
|**`Float64Array.length`**|Static length property whose value is `3`. For the actual length (number of elements), see [`Float64Array.prototype.length`](ens/webfrontend/TypedArray.prototype.length).|
|**[`Float64Array.name`](/en/webfrontend/TypedArray.name)**|Returns the string value of the constructor name. In the case of the `Float64Array` type: `"Float64Array"`.|
|**[`Float64Array.prototype`](/en/webfrontend/TypedArray.prototype)**|Prototype for the [`TypedArray`](/en/webfrontend/TypedArray) objects.|

## Methods

| Methods | Description |
| :-- | :-- |
|**[`Float64Array.from()`](/en/webfrontend/TypedArray.from)**|Creates a new `Float64Array` from an array-like or iterable object. See also [`Array.from()`](/en/webfrontend/Array.from).|
|**[`Float64Array.of()`](/en/webfrontend/TypedArray.of)**|Creates a new `Float64Array` with a variable number of arguments. See also [`Array.of()`](/en/webfrontend/Array.from).|

## Float64Array prototype

All `Float64Array` objects inherit from [`TypedArray.prototype`](/en/webfrontend/TypedArray.prototype).

### Prototype Properties

| Properties | Description |
| :-- | :-- |
|**`Float64Array.prototype.constructor`**|Returns the function that created an instance's prototype. This is the `Float64Array` constructor by default.|
|**[`Float64Array.prototype.buffer`](/en/webfrontend/TypedArray.prototype.buffer)** *(read only)*|Returns the [`ArrayBuffer`](/en/webfrontend/ArrayBuffer) referenced by the `Float64Array` Fixed at construction time and thus read only.|
|**[`Float64Array.prototype.byteLength`](/en/webfrontend/TypedArray.prototype.byteLength)** *(read only)*|Returns the length (in bytes) of the `Float64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). Fixed at construction time and thus read only.|
|**[`Float64Array.prototype.byteOffset`](/en/webfrontend/TypedArray.prototype.byteOffset)** *(read only)*|Returns the offset (in bytes) of the `Float64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). Fixed at construction time and thus read only.|
|**[`Float64Array.prototype.length`](/en/webfrontend/TypedArray.prototype.length)** *(read only)*|Returns the number of elements hold in the `Float64Array`. Fixed at construction time and thus read only.|

### Prototype Methods

| Methods | Description |
| :-- | :-- |
|**[`Float64Array.prototype.copyWithin()`](/en/webfrontend/TypedArray.prototype.copyWithin)**|Copies a sequence of array elements within the array. See also[`Array.prototype.copyWithin()`](/en/webfrontend/Array.prototype.copyWithin)。|
|**[`Float64Array.prototype.entries()`](/en/webfrontend/TypedArray.prototype.entries)**|Returns a new `Array Iterator` object that contains the key/value pairs for each index in the array. See also[`Array.prototype.entries()`](/en/webfrontend/Array.prototype.entries)。|
|**[`Float64Array.prototype.every()`](/en/webfrontend/TypedArray.prototype.every)**|Tests whether all elements in the array pass the test provided by a function. See also[`Array.prototype.every()`](/en/webfrontend/Array.prototype.every)。|
|**[`Float64Array.prototype.fill()`](/en/webfrontend/TypedArray.prototype.fill)**|Fills all the elements of an array from a start index to an end index with a static value. See also[`Array.prototype.fill()`](/en/webfrontend/Array.prototype.fill)。|
|**[`Float64Array.prototype.filter()`](/en/webfrontend/TypedArray.prototype.filter)**|Creates a new array with all of the elements of this array for which the provided filtering function returns true. See also[`Array.prototype.filter()`](/en/webfrontend/Array.prototype.filter)。|
|**[`Float64Array.prototype.find()`](/en/webfrontend/TypedArray.prototype.find)**|Returns the found value in the array, if an element in the array satisfies the provided testing function or `undefined` if not found. See also [`Array.prototype.find()`](/en/webfrontend/Array.prototype.find)。|
|**[`Float64Array.prototype.findIndex()`](/en/webfrontend/TypedArray.prototype.findIndex)**|Returns the found index in the array, if an element in the array satisfies the provided testing function or `-1` if not found. See also [`Array.prototype.findIndex()`](/en/webfrontend/Array.prototype.findIndex)。|
|**[`Float64Array.prototype.forEach()`](/en/webfrontend/TypedArray.prototype.forEach)**|Calls a function for each element in the array. See also [`Array.prototype.forEach()`](/en/webfrontend/Array.prototype.forEach)。|
|**[`Float64Array.prototype.includes()`](/en/webfrontend/TypedArray.prototype.includes)**|Determines whether a typed array includes a certain element, returning `true` or `false` as appropriate. See also[`Array.prototype.includes()`](/en/webfrontend/Array.prototype.includes)。|
|**[`Float64Array.prototype.indexOf()`](/en/webfrontend/TypedArray.prototype.indexOf)**|Returns the first (least) index of an element within the array equal to the specified value, or `-1` if none is found. See also[`Array.prototype.indexOf()`](/en/webfrontend/Array.prototype.indexOf)。|
|**[`Float64Array.prototype.join()`](/en/webfrontend/TypedArray.prototype.join)**|Joins all elements of an array into a string. See also [`Array.prototype.join()`](/en/webfrontend/Array.prototype.join)。|
|**[`Float64Array.prototype.keys()`](/en/webfrontend/TypedArray.prototype.keys)**|Returns a new Array Iterator that contains the keys for each index in the array. See also[`Array.prototype.keys()`](/en/webfrontend/Array.prototype.keys)。|
|**[`Float64Array.prototype.lastIndexOf()`](/en/webfrontend/TypedArray.prototype.lastIndexOf)**|Returns the last (greatest) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.prototype.lastIndexOf()`](/en/webfrontend/Array.prototype.lastIndexOf)。|
|**[`Float64Array.prototype.map()`](/en/webfrontend/TypedArray.prototype.map)**|Creates a new array with the results of calling a provided function on every element in this array. See also [`Array.prototype.map()`](/en/webfrontend/Array.prototype.map)。|
|**[`Float64Array.prototype.move()`](/en/webfrontend/TypedArray.prototype.move)**| Former non-standard version of [`Float64Array.prototype.copyWithin()`](/en/webfrontend/TypedArray.prototype.copyWithin). |
|**[`Float64Array.prototype.reduce()`](/en/webfrontend/TypedArray.prototype.reduce)**|Apply a function against an accumulator and each value of the array (from left-to-right) as to reduce it to a single value. See also [`Array.prototype.reduce()`](/en/webfrontend/Array.prototype.reduce)。|
|**[`Float64Array.prototype.reduceRight()`](/en/webfrontend/TypedArray.prototype.reduceRight)**|Apply a function against an accumulator and each value of the array (from right-to-left) as to reduce it to a single value. See also [`Array.prototype.reduceRight()`](/en/webfrontend/Array.prototype.reduceRight)。|
|**[`Float64Array.prototype.reverse()`](/en/webfrontend/TypedArray.prototype.reverse)**|Reverses the order of the elements of an array — the first becomes the last, and the last becomes the first. See also  [`Array.prototype.reverse()`](/en/webfrontend/Array.prototype.reverse)。|
|**[`Float64Array.prototype.set()`](/en/webfrontend/TypedArray.prototype.set)**|Stores multiple values in the typed array, reading input values from a specified array.|
|**[`Float64Array.prototype.slice()`](/en/webfrontend/TypedArray.prototype.slice)**|Extracts a section of an array and returns a new array. See also [`Array.prototype.slice()`](/en/webfrontend/Array.prototype.slice)。|
|**[`Float64Array.prototype.some()`](/en/webfrontend/TypedArray.prototype.some)**|Returns `true` if at least one element in this array satisfies the provided testing function. See also [`Array.prototype.some()`](/en/webfrontend/Array.prototype.some)。|
|**[`Float64Array.prototype.sort()`](/en/webfrontend/TypedArray.prototype.sort)**|Sorts the elements of an array in place and returns the array. See also [`Array.prototype.sort()`](/en/webfrontend/Array.prototype.sort)。|
|**[`Float64Array.prototype.subarray()`](/en/webfrontend/TypedArray.prototype.subarray)**|Returns a new `Float64Array` from the given start and end element index.|
|**[`Float64Array.prototype.values()`](/en/webfrontend/TypedArray.prototype.values)**|Returns a new Array Iterator object that contains the values for each index in the array. See also [`Array.prototype.values()`](/en/webfrontend/Array.prototype.values)。|
|**[`Float64Array.prototype.toLocaleString()`](/en/webfrontend/TypedArray.prototype.toLocaleString)**|Returns a localized string representing the array and its elements. See also [`Array.prototype.toLocaleString()`](/en/webfrontend/Array.prototype.toLocaleString)。|
|**[`Float64Array.prototype.toString()`](/en/webfrontend/TypedArray.prototype.toString)**|Returns a string representing the array and its elements. See also [`Array.prototype.toString()`](/en/webfrontend/Array.prototype.toString)。|
|**[`Float64Array.prototype[@@iterator]()`](/en/webfrontend/TypedArray.prototype[@@iterator])**|Returns a new Array Iterator object that contains the values for each index in the array.|

## Examples

Different ways to create a `Float64Array`:

```JavaScript
// From a length
var float64 = new Float64Array(2);
float64[0] = 42;
console.log(float64[0]); // 42
console.log(float64.length); // 2
console.log(float64.BYTES_PER_ELEMENT); // 8

// From an array
var arr = new Float64Array([21,31]);
console.log(arr[1]); // 31

// From another TypedArray
var x = new Float64Array([21, 31]);
var y = new Float64Array(x);
console.log(y[0]); // 21

// From an ArrayBuffer
var buffer = new ArrayBuffer(32);
var z = new Float64Array(buffer, 0, 4);

// From an iterable
var iterable = function*(){ yield* [1,2,3]; }();
var float64 = new Float64Array(iterable);
// Float64Array[1, 2, 3]
```
