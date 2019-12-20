TOPICS: BigInt64Array
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript BigInt64Array Object

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
|**[`BigInt64Array.BYTES_PER_ELEMENT`](/en/webfrontend/TypedArray.BYTES_PER_ELEMENT)** | Returns a number value of the element size. `8` in the case of a BigInt64Array.|
|**`BigInt64Array.length`**|Static length property whose value is `3`. For the actual length (number of elements), see [`BigInt64Array.prototype.length`](/en/webfrontend/BigInt64Array.prototype.length).|
|**[`BigInt64Array.name`](/en/webfrontend/BigInt64Array.name)**|Returns the string value of the constructor name. In the case of the BigInt64Array type, this is `"BigInt64Array"`.|
|**[`BigInt64Array.prototype`](/en/webfrontend/BigInt64Array.prototype)**|Prototype for the TypedArray objects.|

## Methods

| Methods| Description |
| :-- | :-- |
|**[`BigInt64Array.from()`](/en/webfrontend/TypedArray.from)**|Creates a new BigInt64Array from an array-like or iterable object. See also [`Array.from()`](/en/webfrontend/Array.from).|
|**[`BigInt64Array.of()`](/en/webfrontend/TypedArray.of)**|Creates a new BigInt64Array with a variable number of arguments. See also [`Array.of()`](/en/webfrontend/Array.of).|

## BigInt64Array prototype

All `BigInt64Array` objects inherit from [`TypedArray.prototype`](/en/webfrontend/TypedArray.prototype).

### prototype Properties

| Properties| Description |
| :-- | :-- |
|**`BigInt64Array.prototype.constructor`**|Returns the function that created an instance's prototype. This is the `BigInt64Array` constructor by default.|
|**[`BigInt64Array.prototype.buffer`](/en/webfrontend/TypedArray.prototype.buffer)** (*Read only*)|Returns the [`ArrayBuffer`](/en/webfrontend/ArrayBuffer) referenced by the `BigInt64Array`.This is fixed at construction time and thus read only.|
|**[`BigInt64Array.prototype.byteLength`](/en/webfrontend/TypedArray.prototype.byteLength)** (*Read only*)|Returns the length (in bytes) of the `BigInt64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). This is fixed at construction time and thus read only.|
|**[`BigInt64Array.prototype.byteOffset`](/en/webfrontend/TypedArray.prototype.byteOffset)** (*Read only*)|Returns the offset (in bytes) of the `BigInt64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). This is fixed at construction time and thus read only.|
|**[`BigInt64Array.prototype.length`](/en/webfrontend/TypedArray.prototype.length)** (*Read only*)|Returns the number of elements hold in the `BigInt64Array`. This is fixed at construction time and thus read only.|

### prototype Methods

| Methods | Description |
| :-- | :-- |
|**[`BigInt64Array.prototype.copyWithin()`](/en/webfrontend/TypedArray.prototype.copyWithin)**|Copies a sequence of array elements within the array. See also [`Array.prototype.copyWithin()`](/en/webfrontend/Array.prototype.copyWithin).|
|**[`BigInt64Array.prototype.entries()`](/en/webfrontend/TypedArray.prototype.entries)**|Returns a new Array Iterator object that contains the key/value pairs for each index in the array.See also [`Array.prototype.entries()`](/en/webfrontend/Array.prototype.entries).|
|**[`BigInt64Array.prototype.every()`](/en/webfrontend/TypedArray.prototype.every)**|Tests whether all elements in the array pass the test provided by a function. See also [`Array.prototype.every()`](/en/webfrontend/Array.prototype.every).|
|**[`BigInt64Array.prototype.fill()`](/en/webfrontend/TypedArray.prototype.fill)**|Fills all the elements of an array from a start index to an end index with a static value. See also [`Array.prototype.fill()`](/en/webfrontend/Array.prototype.fill).|
|**[`BigInt64Array.prototype.filter()`](/en/webfrontend/TypedArray.prototype.filter)**|Creates a new array with all of the elements of this array for which the provided filtering function returns `true` .See also [`Array.prototype.filter()`](/en/webfrontend/Array.prototype.filter).|
|**[`BigInt64Array.prototype.find()`](/en/webfrontend/TypedArray.prototype.find)**|Returns the found value in the array if an element in the array satisfies the provided testing function, or `undefined` if not found. See also [`Array.prototype.find()`](/en/webfrontend/Array.prototype.find).|
|**[`BigInt64Array.prototype.findIndex()`](/en/webfrontend/TypedArray.prototype.findIndex)**|Returns the found index in the array if an element in the array satisfies the provided testing function,or `-1` if not found. See also [`Array.prototype.findIndex()`](/en/webfrontend/Array.prototype.findIndex).|
|**[`BigInt64Array.prototype.forEach()`](/en/webfrontend/TypedArray.prototype.forEach)**|Calls a function for each element in the array. See also [`Array.prototype.forEach()`](/en/webfrontend/Array.prototype.forEach).|
|**[`BigInt64Array.prototype.includes()`](/en/webfrontend/TypedArray.prototype.includes)**|Determines whether a typed array includes a certain element, returning `true` or `false` as appropriate.See also [`Array.prototype.includes()`](/en/webfrontend/Array.prototype.includes).|
|**[`BigInt64Array.prototype.indexOf()`](/en/webfrontend/TypedArray.prototype.indexOf)**|Returns the first (least) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.prototype.indexOf()`](/en/webfrontend/Array.prototype.indexOf).|
|**[`BigInt64Array.prototype.join()`](/en/webfrontend/TypedArray.prototype.join)**|Joins all elements of an array into a string. See also [`Array.prototype.join()`](/en/webfrontend/Array.prototype.join).|
|**[`BigInt64Array.prototype.keys()`](/en/webfrontend/TypedArray.prototype.keys)**|Returns a new Array Iterator that contains the keys for each index in the array. See also [`Array.prototype.keys()`](/en/webfrontend/Array.prototype.keys).|
|**[`BigInt64Array.prototype.lastIndexOf()`](/en/webfrontend/TypedArray.prototype.lastIndexOf)**|Returns the last (greatest) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.prototype.lastIndexOf()`](/en/webfrontend/Array.prototype.lastIndexOf).|
|**[`BigInt64Array.prototype.map()`](/en/webfrontend/TypedArray.prototype.map)**|Creates a new array with the results of calling a provided function on every element in this array. See also [`Array.prototype.map()`](/en/webfrontend/Array.prototype.map).|
|**[`BigInt64Array.prototype.reduce()`](/en/webfrontend/TypedArray.prototype.reduce)**|Applies a function against an accumulator and each value of the array (from left-to-right) so as to reduce it to a single value. See also [`Array.prototype.reduce()`](/en/webfrontend/Array.prototype.reduce).|
|**[`BigInt64Array.prototype.reduceRight()`](/en/webfrontend/TypedArray.prototype.reduceRight)**|Applies a function against an accumulator and each value of the array (from right-to-left) so as to reduce it to a single value. See also [`Array.prototype.reduceRight()`](/en/webfrontend/Array.prototype.reduceRight).|
|**[`BigInt64Array.prototype.reverse()`](/en/webfrontend/TypedArray.prototype.reverse)**|Reverses the order of the elements of an array — the first becomes the last, and the last becomes the first. See also [`Array.prototype.reverse()`](/en/webfrontend/Array.prototype.reverse).|
|**[`BigInt64Array.prototype.set()`](/en/webfrontend/TypedArray.prototype.set)**|Stores multiple values in the typed array, reading input values from a specified array.|
|**[`BigInt64Array.prototype.slice()`](/en/webfrontend/TypedArray.prototype.slice)**|Extracts a section of an array and returns a new array. See also [`Array.prototype.slice()`](/en/webfrontend/Array.prototype.slice).|
|**[`BigInt64Array.prototype.some()`](/en/webfrontend/TypedArray.prototype.some)**|Returns true if at least one element in this array satisfies the provided testing function. See also [`Array.prototype.some()`](/en/webfrontend/Array.prototype.some).|
|**[`BigInt64Array.prototype.sort()`](/en/webfrontend/TypedArray.prototype.sort)**|Sorts the elements of an array in place and returns the array. See also [`Array.prototype.sort()`](/en/webfrontend/Array.prototype.sort).|
|**[`BigInt64Array.prototype.subarray()`](/en/webfrontend/TypedArray.prototype.subarray)**|Returns a new `BigUint64Array` from the given start and end element index.|
|**[`BigInt64Array.prototype.values()`](/en/webfrontend/TypedArray.prototype.values)**|Returns a new Array Iterator object that contains the values for each index in the array. See also [`Array.prototype.values()`](/en/webfrontend/Array.prototype.values).|
|**[`BigInt64Array.prototype.toLocaleString()`](/en/webfrontend/TypedArray.prototype.toLocaleString)**|Returns a localized string representing the array and its elements. See also [`Array.prototype.toLocaleString()`](/en/webfrontend/Array.prototype.toLocaleString).|
|**[`BigInt64Array.prototype.toString()`](/en/webfrontend/TypedArray.prototype.toString)**|Returns a string representing the array and its elements. See also [`Array.prototype.toString()`](/en/webfrontend/Array.prototype.toString).|
|**[`BigInt64Array.prototype[@@iterator]()`](/en/webfrontend/TypedArray.prototype[@@iterator])**|Returns a new Array Iterator object that contains the values for each index in the array.|

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
