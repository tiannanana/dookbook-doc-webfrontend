TOPICS: BigInt64Array
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript `BigInt64Array` Object

The `BigInt64Array` typed array represents an array of 64-bit signed integers in the platform byte order.
If control over byte order is needed, use [`DataView`](/en/webfrontend/DataView) instead.
The contents are initialized to `0n`.
Once established, you can reference elements in the array using the object's methods,
or by using standard array index syntax (that is, using bracket notation).

## Syntax

```JavaScript
new BigInt64Array();
new BigInt64Array(length);
new BigInt64Array(typedArray);
new BigInt64Array(object);
new BigInt64Array(buffer [, byteOffset [, length]]);
```

For more information about the constructor syntax and parameters, see [`TypedArray`](/en/webfrontend/TypedArray).

## Properties

| Properties| Description |
| :-- | :-- |
|**[`BigInt64Array.BYTES_PER_ELEMENT`](/en/webfrontend/TypedArray.BYTES_PER_ELEMENT)** | Returns a number value of the element size. `8` in the case of a `BigInt64Array`.|
|**`BigInt64Array.length`**|Static length property whose value is `3`. For the actual length (number of elements), see `BigInt64Array.prototype.length`.|
|**[`BigInt64Array.name`](/en/webfrontend/BigInt64Array.name)**|Returns the string value of the constructor name. In the case of the BigInt64Array type, this is `"BigInt64Array"`.|
|**`BigInt64Array.prototype`**|Prototype for the `TypedArray` objects.|

## Methods

| Methods| Description |
| :-- | :-- |
|**[`BigInt64Array.from()`](/en/webfrontend/TypedArray.from)**|Creates a new BigInt64Array from an array-like or iterable object. See also [`Array.from()`](/en/webfrontend/Array.from).|
|**[`BigInt64Array.of()`](/en/webfrontend/TypedArray.of)**|Creates a new BigInt64Array with a variable number of arguments. See also [`Array.of()`](/en/webfrontend/Array.of).|

## BigInt64Array prototype

All `BigInt64Array` objects inherit from `TypedArray.prototype`.

### prototype Properties

| Properties| Description |
| :-- | :-- |
|**`BigInt64Array.prototype.constructor`**|Returns the function that created an instance's prototype. This is the `BigInt64Array` constructor by default.|
|**[`BigInt64Array.buffer`](/en/webfrontend/TypedArray.buffer)** (*Read only*)|Returns the [`ArrayBuffer`](/en/webfrontend/ArrayBuffer) referenced by the `BigInt64Array`.This is fixed at construction time and thus read only.|
|**[`BigInt64Array.byteLength`](/en/webfrontend/TypedArray.byteLength)** (*Read only*)|Returns the length (in bytes) of the `BigInt64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). This is fixed at construction time and thus read only.|
|**[`BigInt64Array.byteOffset`](/en/webfrontend/TypedArray.byteOffset)** (*Read only*)|Returns the offset (in bytes) of the `BigInt64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). This is fixed at construction time and thus read only.|
|**[`BigInt64Array.length`](/en/webfrontend/TypedArray.length)** (*Read only*)|Returns the number of elements hold in the `BigInt64Array`. This is fixed at construction time and thus read only.|

### prototype Methods

| Methods | Description |
| :-- | :-- |
|**[`BigInt64Array.copyWithin()`](/en/webfrontend/TypedArray.copyWithin)**|Copies a sequence of array elements within the array. See also [`Array.copyWithin()`](/en/webfrontend/Array.copyWithin).|
|**[`BigInt64Array.entries()`](/en/webfrontend/TypedArray.entries)**|Returns a new Array Iterator object that contains the key/value pairs for each index in the array.See also [`Array.entries()`](/en/webfrontend/Array.entries).|
|**[`BigInt64Array.every()`](/en/webfrontend/TypedArray.every)**|Tests whether all elements in the array pass the test provided by a function. See also [`Array.every()`](/en/webfrontend/Array.every).|
|**[`BigInt64Array.fill()`](/en/webfrontend/TypedArray.fill)**|Fills all the elements of an array from a start index to an end index with a static value. See also [`Array.fill()`](/en/webfrontend/Array.fill).|
|**[`BigInt64Array.filter()`](/en/webfrontend/TypedArray.filter)**|Creates a new array with all of the elements of this array for which the provided filtering function returns `true` .See also [`Array.filter()`](/en/webfrontend/Array.filter).|
|**[`BigInt64Array.find()`](/en/webfrontend/TypedArray.find)**|Returns the found value in the array if an element in the array satisfies the provided testing function, or `undefined` if not found. See also [`Array.find()`](/en/webfrontend/Array.find).|
|**[`BigInt64Array.findIndex()`](/en/webfrontend/TypedArray.findIndex)**|Returns the found index in the array if an element in the array satisfies the provided testing function,or `-1` if not found. See also [`Array.findIndex()`](/en/webfrontend/Array.findIndex).|
|**[`BigInt64Array.forEach()`](/en/webfrontend/TypedArray.forEach)**|Calls a function for each element in the array. See also [`Array.forEach()`](/en/webfrontend/Array.forEach).|
|**[`BigInt64Array.includes()`](/en/webfrontend/TypedArray.includes)**|Determines whether a typed array includes a certain element, returning `true` or `false` as appropriate.See also [`Array.includes()`](/en/webfrontend/Array.includes).|
|**[`BigInt64Array.indexOf()`](/en/webfrontend/TypedArray.indexOf)**|Returns the first (least) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.indexOf()`](/en/webfrontend/Array.indexOf).|
|**[`BigInt64Array.join()`](/en/webfrontend/TypedArray.join)**|Joins all elements of an array into a string. See also [`Array.join()`](/en/webfrontend/Array.join).|
|**[`BigInt64Array.keys()`](/en/webfrontend/TypedArray.keys)**|Returns a new Array Iterator that contains the keys for each index in the array. See also [`Array.keys()`](/en/webfrontend/Array.keys).|
|**[`BigInt64Array.lastIndexOf()`](/en/webfrontend/TypedArray.lastIndexOf)**|Returns the last (greatest) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.lastIndexOf()`](/en/webfrontend/Array.lastIndexOf).|
|**[`BigInt64Array.map()`](/en/webfrontend/TypedArray.map)**|Creates a new array with the results of calling a provided function on every element in this array. See also [`Array.map()`](/en/webfrontend/Array.map).|
|**[`BigInt64Array.reduce()`](/en/webfrontend/TypedArray.reduce)**|Applies a function against an accumulator and each value of the array (from left-to-right) so as to reduce it to a single value. See also [`Array.reduce()`](/en/webfrontend/Array.reduce).|
|**[`BigInt64Array.reduceRight()`](/en/webfrontend/TypedArray.reduceRight)**|Applies a function against an accumulator and each value of the array (from right-to-left) so as to reduce it to a single value. See also [`Array.reduceRight()`](/en/webfrontend/Array.reduceRight).|
|**[`BigInt64Array.reverse()`](/en/webfrontend/TypedArray.reverse)**|Reverses the order of the elements of an array — the first becomes the last, and the last becomes the first. See also [`Array.reverse()`](/en/webfrontend/Array.reverse).|
|**[`BigInt64Array.set()`](/en/webfrontend/TypedArray.set)**|Stores multiple values in the typed array, reading input values from a specified array.|
|**[`BigInt64Array.slice()`](/en/webfrontend/TypedArray.slice)**|Extracts a section of an array and returns a new array. See also [`Array.slice()`](/en/webfrontend/Array.slice).|
|**[`BigInt64Array.some()`](/en/webfrontend/TypedArray.some)**|Returns true if at least one element in this array satisfies the provided testing function. See also [`Array.some()`](/en/webfrontend/Array.some).|
|**[`BigInt64Array.sort()`](/en/webfrontend/TypedArray.sort)**|Sorts the elements of an array in place and returns the array. See also [`Array.sort()`](/en/webfrontend/Array.sort).|
|**[`BigInt64Array.subarray()`](/en/webfrontend/TypedArray.subarray)**|Returns a new `BigUint64Array` from the given start and end element index.|
|**[`BigInt64Array.values()`](/en/webfrontend/TypedArray.values)**|Returns a new Array Iterator object that contains the values for each index in the array. See also [`Array.values()`](/en/webfrontend/Array.values).|
|**[`BigInt64Array.toLocaleString()`](/en/webfrontend/TypedArray.toLocaleString)**|Returns a localized string representing the array and its elements. See also [`Array.toLocaleString()`](/en/webfrontend/Array.toLocaleString).|
|**[`BigInt64Array.toString()`](/en/webfrontend/TypedArray.toString)**|Returns a string representing the array and its elements. See also [`Array.toString()`](/en/webfrontend/Array.toString).|
|**[`BigInt64Array[@@iterator]()`](/en/webfrontend/TypedArray[@@iterator])**|Returns a new Array Iterator object that contains the values for each index in the array.|

## Examples

Different ways to create a `BigInt64Array`:

```JavaScript
// From a length
var bigint64 = new BigInt64Array(2);
bigint64[0] = 42n;
console.log(bigint64[0]); // 42n
console.log(bigint64.length); // 2
console.log(bigint64.BYTES_PER_ELEMENT); // 8

// From an array
var arr = new BigInt64Array([21n,31n]);
console.log(arr[1]); // 31n

// From another TypedArray
var x = new BigInt64Array([21n, 31n]);
var y = new BigInt64Array(x);
console.log(y[0]); // 21n

// From an ArrayBuffer
var buffer = new ArrayBuffer(32);
var z = new BigInt64Array(buffer, 0, 4);

// From an iterable
var iterable = function*(){ yield* [1n, 2n, 3n]; }();
var bigint64 = new BigInt64Array(iterable);
// BigInt64Array[1n, 2n, 3n]
```
