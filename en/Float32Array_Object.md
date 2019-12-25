TOPICS: Float32Array
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Float32Array Object

The `Float32Array` typed array represents an array of 32-bit floating point numbers
(corresponding to the C float data type) in the platform byte order.
If control over byte order is needed, use [`DataView`](/en/webfrontend/DataView) instead.
The contents are initialized to `0`.
Once established, you can reference elements in the array using the object's methods,
or using standard array index syntax (that is, using bracket notation).

## Syntax

```JavaScript
new Float32Array(length);
new Float32Array(typedArray);
new Float32Array(object);
new Float32Array(buffer [, byteOffset [, length]]);
```

For more information about the constructor syntax and the parameters, see [`TypedArray`](/en/webfrontend/TypedArray).

## Properties

| Properties | Description |
| :-- | :-- |
|**[`Float32Array.BYTES_PER_ELEMENT`](/en/webfrontend/TypedArray.BYTES_PER_ELEMENT)**|Returns a number value of the element size. `4` in the case of an `Float32Array`.|
|**`Float32Array.length`**|Static length property whose value is `3`. For the actual length (number of elements), see [`Float32Array.prototype.length`](ens/webfrontend/TypedArray.prototype.length).|
|**[`Float32Array.name`](/en/webfrontend/TypedArray.name)**|Returns the string value of the constructor name. In the case of the `Float32Array` type: `"Float32Array"`.|
|**[`Float32Array.prototype`](/en/webfrontend/TypedArray.prototype)**|Prototype for the [`TypedArray`](/en/webfrontend/TypedArray) objects.|

## Methods

| Methods | Description |
| :-- | :-- |
|**[`Float32Array.from()`](/en/webfrontend/TypedArray.from)**|Creates a new `Float32Array` from an array-like or iterable object. See also [`Array.from()`](/en/webfrontend/Array.from).|
|**[`Float32Array.of()`](/en/webfrontend/TypedArray.of)**|Creates a new `Float32Array` with a variable number of arguments. See also [`Array.of()`](/en/webfrontend/Array.from).|

## Float32Array prototype

All `Float32Array` objects inherit from [`TypedArray.prototype`](/en/webfrontend/TypedArray.prototype).

### Prototype Properties

| Properties | Description |
| :-- | :-- |
|**`Float32Array.prototype.constructor`**|Returns the function that created an instance's prototype. This is the `Float32Array` constructor by default.|
|**[`Float32Array.prototype.buffer`](/en/webfrontend/TypedArray.prototype.buffer)** *(read only)*|Returns the [`ArrayBuffer`](/en/webfrontend/ArrayBuffer) referenced by the `Float32Array` Fixed at construction time and thus read only.|
|**[`Float32Array.prototype.byteLength`](/en/webfrontend/TypedArray.prototype.byteLength)** *(read only)*|Returns the length (in bytes) of the `Float32Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). Fixed at construction time and thus read only.|
|**[`Float32Array.prototype.byteOffset`](/en/webfrontend/TypedArray.prototype.byteOffset)** *(read only)*|Returns the offset (in bytes) of the `Float32Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). Fixed at construction time and thus read only.|
|**[`Float32Array.prototype.length`](/en/webfrontend/TypedArray.prototype.length)** *(read only)*|Returns the number of elements hold in the `Float32Array`. Fixed at construction time and thus read only.|

### Prototype Methods

| Methods | Description |
| :-- | :-- |
|**[`Float32Array.prototype.copyWithin()`](/en/webfrontend/TypedArray.prototype.copyWithin)**|Copies a sequence of array elements within the array. See also[`Array.prototype.copyWithin()`](/en/webfrontend/Array.prototype.copyWithin)。|
|**[`Float32Array.prototype.entries()`](/en/webfrontend/TypedArray.prototype.entries)**|Returns a new `Array Iterator` object that contains the key/value pairs for each index in the array. See also[`Array.prototype.entries()`](/en/webfrontend/Array.prototype.entries)。|
|**[`Float32Array.prototype.every()`](/en/webfrontend/TypedArray.prototype.every)**|Tests whether all elements in the array pass the test provided by a function. See also[`Array.prototype.every()`](/en/webfrontend/Array.prototype.every)。|
|**[`Float32Array.prototype.fill()`](/en/webfrontend/TypedArray.prototype.fill)**|Fills all the elements of an array from a start index to an end index with a static value. See also[`Array.prototype.fill()`](/en/webfrontend/Array.prototype.fill)。|
|**[`Float32Array.prototype.filter()`](/en/webfrontend/TypedArray.prototype.filter)**|Creates a new array with all of the elements of this array for which the provided filtering function returns true. See also[`Array.prototype.filter()`](/en/webfrontend/Array.prototype.filter)。|
|**[`Float32Array.prototype.find()`](/en/webfrontend/TypedArray.prototype.find)**|Returns the found value in the array, if an element in the array satisfies the provided testing function or `undefined` if not found. See also [`Array.prototype.find()`](/en/webfrontend/Array.prototype.find)。|
|**[`Float32Array.prototype.findIndex()`](/en/webfrontend/TypedArray.prototype.findIndex)**|Returns the found index in the array, if an element in the array satisfies the provided testing function or `-1` if not found. See also [`Array.prototype.findIndex()`](/en/webfrontend/Array.prototype.findIndex)。|
|**[`Float32Array.prototype.forEach()`](/en/webfrontend/TypedArray.prototype.forEach)**|Calls a function for each element in the array. See also [`Array.prototype.forEach()`](/en/webfrontend/Array.prototype.forEach)。|
|**[`Float32Array.prototype.includes()`](/en/webfrontend/TypedArray.prototype.includes)**|Determines whether a typed array includes a certain element, returning `true` or `false` as appropriate. See also[`Array.prototype.includes()`](/en/webfrontend/Array.prototype.includes)。|
|**[`Float32Array.prototype.indexOf()`](/en/webfrontend/TypedArray.prototype.indexOf)**|Returns the first (least) index of an element within the array equal to the specified value, or `-1` if none is found. See also[`Array.prototype.indexOf()`](/en/webfrontend/Array.prototype.indexOf)。|
|**[`Float32Array.prototype.join()`](/en/webfrontend/TypedArray.prototype.join)**|Joins all elements of an array into a string. See also [`Array.prototype.join()`](/en/webfrontend/Array.prototype.join)。|
|**[`Float32Array.prototype.keys()`](/en/webfrontend/TypedArray.prototype.keys)**|Returns a new Array Iterator that contains the keys for each index in the array. See also[`Array.prototype.keys()`](/en/webfrontend/Array.prototype.keys)。|
|**[`Float32Array.prototype.lastIndexOf()`](/en/webfrontend/TypedArray.prototype.lastIndexOf)**|Returns the last (greatest) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.prototype.lastIndexOf()`](/en/webfrontend/Array.prototype.lastIndexOf)。|
|**[`Float32Array.prototype.map()`](/en/webfrontend/TypedArray.prototype.map)**|Creates a new array with the results of calling a provided function on every element in this array. See also [`Array.prototype.map()`](/en/webfrontend/Array.prototype.map)。|
|**[`Float32Array.prototype.move()`](/en/webfrontend/TypedArray.prototype.move)**| Former non-standard version of [`Float32Array.prototype.copyWithin()`](/en/webfrontend/TypedArray.prototype.copyWithin). |
|**[`Float32Array.prototype.reduce()`](/en/webfrontend/TypedArray.prototype.reduce)**|Apply a function against an accumulator and each value of the array (from left-to-right) as to reduce it to a single value. See also [`Array.prototype.reduce()`](/en/webfrontend/Array.prototype.reduce)。|
|**[`Float32Array.prototype.reduceRight()`](/en/webfrontend/TypedArray.prototype.reduceRight)**|Apply a function against an accumulator and each value of the array (from right-to-left) as to reduce it to a single value. See also [`Array.prototype.reduceRight()`](/en/webfrontend/Array.prototype.reduceRight)。|
|**[`Float32Array.prototype.reverse()`](/en/webfrontend/TypedArray.prototype.reverse)**|Reverses the order of the elements of an array — the first becomes the last, and the last becomes the first. See also  [`Array.prototype.reverse()`](/en/webfrontend/Array.prototype.reverse)。|
|**[`Float32Array.prototype.set()`](/en/webfrontend/TypedArray.prototype.set)**|Stores multiple values in the typed array, reading input values from a specified array.|
|**[`Float32Array.prototype.slice()`](/en/webfrontend/TypedArray.prototype.slice)**|Extracts a section of an array and returns a new array. See also [`Array.prototype.slice()`](/en/webfrontend/Array.prototype.slice)。|
|**[`Float32Array.prototype.some()`](/en/webfrontend/TypedArray.prototype.some)**|Returns `true` if at least one element in this array satisfies the provided testing function. See also [`Array.prototype.some()`](/en/webfrontend/Array.prototype.some)。|
|**[`Float32Array.prototype.sort()`](/en/webfrontend/TypedArray.prototype.sort)**|Sorts the elements of an array in place and returns the array. See also [`Array.prototype.sort()`](/en/webfrontend/Array.prototype.sort)。|
|**[`Float32Array.prototype.subarray()`](/en/webfrontend/TypedArray.prototype.subarray)**|Returns a new `Float32Array` from the given start and end element index.|
|**[`Float32Array.prototype.values()`](/en/webfrontend/TypedArray.prototype.values)**|Returns a new Array Iterator object that contains the values for each index in the array. See also [`Array.prototype.values()`](/en/webfrontend/Array.prototype.values)。|
|**[`Float32Array.prototype.toLocaleString()`](/en/webfrontend/TypedArray.prototype.toLocaleString)**|Returns a localized string representing the array and its elements. See also [`Array.prototype.toLocaleString()`](/en/webfrontend/Array.prototype.toLocaleString)。|
|**[`Float32Array.prototype.toString()`](/en/webfrontend/TypedArray.prototype.toString)**|Returns a string representing the array and its elements. See also [`Array.prototype.toString()`](/en/webfrontend/Array.prototype.toString)。|
|**[`Float32Array.prototype[@@iterator]()`](/en/webfrontend/TypedArray.prototype[@@iterator])**|Returns a new Array Iterator object that contains the values for each index in the array.|

## Examples

Different ways to create a `Float32Array`:

```JavaScript
// From a length
var float32 = new Float32Array(2);
float32[0] = 42;
console.log(float32[0]); // 42
console.log(float32.length); // 2
console.log(float32.BYTES_PER_ELEMENT); // 4

// From an array
var arr = new Float32Array([21,31]);
console.log(arr[1]); // 31

// From another TypedArray
var x = new Float32Array([21, 31]);
var y = new Float32Array(x);
console.log(y[0]); // 21

// From an ArrayBuffer
var buffer = new ArrayBuffer(16);
var z = new Float32Array(buffer, 0, 4);
```
