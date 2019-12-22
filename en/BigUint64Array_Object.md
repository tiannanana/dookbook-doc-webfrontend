TOPICS: BigUint64Array
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript BigUint64Array Obejct

The `BigUint64Array` typed array represents an array of 64-bit unsigned integers in the platform byte
order. If control over byte order is needed, use [`DataView`](/en/webfrontend/DataView) instead.
The contents are initialized to `0n`.
Once established, you can reference elements in the array using the object's methods,
or by using standard array index syntax (that is, using bracket notation).

## Syntax

```JavaScript
new BigUint64Array();
new BigUint64Array(length);
new BigUint64Array(typedArray);
new BigUint64Array(object);
new BigUint64Array(buffer [, byteOffset [, length]]);
```

For more information about the constructor syntax and parameters, see [`TypedArray`](/en/webfrontend/TypedArray).

## Properties

| Properties| Description |
| :-- | :-- |
|**[`BigUint64Array.BYTES_PER_ELEMENT`](/en/webfrontend/TypedArray.BYTES_PER_ELEMENT)** | Returns a number value of the element size. `8` in the case of a `BigUint64Array`.|
|**`BigUint64Array.length`**|Static length property whose value is `3`. For the actual length (number of elements), see [`BigUint64Array.prototype.length`](/en/webfrontend/BigUint64Array.prototype.length).|
|**[`BigUint64Array.name`](/en/webfrontend/BigUint64Array.name)**|Returns the string value of the constructor name. In the case of the BigUint64Array type, this is `"BigUint64Array"`.|
|**[`BigUint64Array.prototype`](/en/webfrontend/BigUint64Array.prototype)**|Prototype for the TypedArray objects.|

## Methods

| Methods| Description |
| :-- | :-- |
|**[`BigUint64Array.from()`](/en/webfrontend/TypedArray.from)**|Creates a new BigUint64Array from an array-like or iterable object. See also [`Array.from()`](/en/webfrontend/Array.from).|
|**[`BigUint64Array.of()`](/en/webfrontend/TypedArray.of)**|Creates a new BigUint64Array with a variable number of arguments. See also [`Array.of()`](/en/webfrontend/Array.of).|

## BigUint64Array prototype

All `BigUint64Array` objects inherit from [`TypedArray.prototype`](/en/webfrontend/TypedArray.prototype).

### prototype Properties

| Properties| Description |
| :-- | :-- |
|**`BigUint64Array.prototype.constructor`**|Returns the function that created an instance's prototype. This is the `BigUint64Array` constructor by default.|
|**[`BigUint64Array.prototype.buffer`](/en/webfrontend/TypedArray.prototype.buffer)** (*Read only*)|Returns the [`ArrayBuffer`](/en/webfrontend/ArrayBuffer) referenced by the `BigUint64Array`.This is fixed at construction time and thus read only.|
|**[`BigUint64Array.prototype.byteLength`](/en/webfrontend/TypedArray.prototype.byteLength)** (*Read only*)|Returns the length (in bytes) of the `BigUint64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). This is fixed at construction time and thus read only.|
|**[`BigUint64Array.prototype.byteOffset`](/en/webfrontend/TypedArray.prototype.byteOffset)** (*Read only*)|Returns the offset (in bytes) of the `BigUint64Array` from the start of its [`ArrayBuffer`](/en/webfrontend/ArrayBuffer). This is fixed at construction time and thus read only.|
|**[`BigUint64Array.prototype.length`](/en/webfrontend/TypedArray.prototype.length)** (*Read only*)|Returns the number of elements hold in the `BigUint64Array`. This is fixed at construction time and thus read only.|

### prototype Methods

| Methods | Description |
| :-- | :-- |
|**[`BigUint64Array.prototype.copyWithin()`](/en/webfrontend/TypedArray.prototype.copyWithin)**|Copies a sequence of array elements within the array. See also [`Array.prototype.copyWithin()`](/en/webfrontend/Array.prototype.copyWithin).|
|**[`BigUint64Array.prototype.entries()`](/en/webfrontend/TypedArray.prototype.entries)**|Returns a new Array Iterator object that contains the key/value pairs for each index in the array.See also [`Array.prototype.entries()`](/en/webfrontend/Array.prototype.entries).|
|**[`BigUint64Array.prototype.every()`](/en/webfrontend/TypedArray.prototype.every)**|Tests whether all elements in the array pass the test provided by a function. See also [`Array.prototype.every()`](/en/webfrontend/Array.prototype.every).|
|**[`BigUint64Array.prototype.fill()`](/en/webfrontend/TypedArray.prototype.fill)**|Fills all the elements of an array from a start index to an end index with a static value. See also [`Array.prototype.fill()`](/en/webfrontend/Array.prototype.fill).|
|**[`BigUint64Array.prototype.filter()`](/en/webfrontend/TypedArray.prototype.filter)**|Creates a new array with all of the elements of this array for which the provided filtering function returns `true` .See also [`Array.prototype.filter()`](/en/webfrontend/Array.prototype.filter).|
|**[`BigUint64Array.prototype.find()`](/en/webfrontend/TypedArray.prototype.find)**|Returns the found value in the array if an element in the array satisfies the provided testing function, or `undefined` if not found. See also [`Array.prototype.find()`](/en/webfrontend/Array.prototype.find).|
|**[`BigUint64Array.prototype.findIndex()`](/en/webfrontend/TypedArray.prototype.findIndex)**|Returns the found index in the array if an element in the array satisfies the provided testing function,or `-1` if not found. See also [`Array.prototype.findIndex()`](/en/webfrontend/Array.prototype.findIndex).|
|**[`BigUint64Array.prototype.forEach()`](/en/webfrontend/TypedArray.prototype.forEach)**|Calls a function for each element in the array. See also [`Array.prototype.forEach()`](/en/webfrontend/Array.prototype.forEach).|
|**[`BigUint64Array.prototype.includes()`](/en/webfrontend/TypedArray.prototype.includes)**|Determines whether a typed array includes a certain element, returning `true` or `false` as appropriate.See also [`Array.prototype.includes()`](/en/webfrontend/Array.prototype.includes).|
|**[`BigUint64Array.prototype.indexOf()`](/en/webfrontend/TypedArray.prototype.indexOf)**|Returns the first (least) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.prototype.indexOf()`](/en/webfrontend/Array.prototype.indexOf).|
|**[`BigUint64Array.prototype.join()`](/en/webfrontend/TypedArray.prototype.join)**|Joins all elements of an array into a string. See also [`Array.prototype.join()`](/en/webfrontend/Array.prototype.join).|
|**[`BigUint64Array.prototype.keys()`](/en/webfrontend/TypedArray.prototype.keys)**|Returns a new Array Iterator that contains the keys for each index in the array. See also [`Array.prototype.keys()`](/en/webfrontend/Array.prototype.keys).|
|**[`BigUint64Array.prototype.lastIndexOf()`](/en/webfrontend/TypedArray.prototype.lastIndexOf)**|Returns the last (greatest) index of an element within the array equal to the specified value, or `-1` if none is found. See also [`Array.prototype.lastIndexOf()`](/en/webfrontend/Array.prototype.lastIndexOf).|
|**[`BigUint64Array.prototype.map()`](/en/webfrontend/TypedArray.prototype.map)**|Creates a new array with the results of calling a provided function on every element in this array. See also [`Array.prototype.map()`](/en/webfrontend/Array.prototype.map).|
|**[`BigUint64Array.prototype.reduce()`](/en/webfrontend/TypedArray.prototype.reduce)**|Applies a function against an accumulator and each value of the array (from left-to-right) so as to reduce it to a single value. See also [`Array.prototype.reduce()`](/en/webfrontend/Array.prototype.reduce).|
|**[`BigUint64Array.prototype.reduceRight()`](/en/webfrontend/TypedArray.prototype.reduceRight)**|Applies a function against an accumulator and each value of the array (from right-to-left) so as to reduce it to a single value. See also [`Array.prototype.reduceRight()`](/en/webfrontend/Array.prototype.reduceRight).|
|**[`BigUint64Array.prototype.reverse()`](/en/webfrontend/TypedArray.prototype.reverse)**|Reverses the order of the elements of an array — the first becomes the last, and the last becomes the first. See also [`Array.prototype.reverse()`](/en/webfrontend/Array.prototype.reverse).|
|**[`BigUint64Array.prototype.set()`](/en/webfrontend/TypedArray.prototype.set)**|Stores multiple values in the typed array, reading input values from a specified array.|
|**[`BigUint64Array.prototype.slice()`](/en/webfrontend/TypedArray.prototype.slice)**|Extracts a section of an array and returns a new array. See also [`Array.prototype.slice()`](/en/webfrontend/Array.prototype.slice).|
|**[`BigUint64Array.prototype.some()`](/en/webfrontend/TypedArray.prototype.some)**|Returns true if at least one element in this array satisfies the provided testing function. See also [`Array.prototype.some()`](/en/webfrontend/Array.prototype.some).|
|**[`BigUint64Array.prototype.sort()`](/en/webfrontend/TypedArray.prototype.sort)**|Sorts the elements of an array in place and returns the array. See also [`Array.prototype.sort()`](/en/webfrontend/Array.prototype.sort).|
|**[`BigUint64Array.prototype.subarray()`](/en/webfrontend/TypedArray.prototype.subarray)**|Returns a new `BigUint64Array` from the given start and end element index.|
|**[`BigUint64Array.prototype.values()`](/en/webfrontend/TypedArray.prototype.values)**|Returns a new Array Iterator object that contains the values for each index in the array. See also [`Array.prototype.values()`](/en/webfrontend/Array.prototype.values).|
|**[`BigUint64Array.prototype.toLocaleString()`](/en/webfrontend/TypedArray.prototype.toLocaleString)**|Returns a localized string representing the array and its elements. See also [`Array.prototype.toLocaleString()`](/en/webfrontend/Array.prototype.toLocaleString).|
|**[`BigUint64Array.prototype.toString()`](/en/webfrontend/TypedArray.prototype.toString)**|Returns a string representing the array and its elements. See also [`Array.prototype.toString()`](/en/webfrontend/Array.prototype.toString).|
|**[`BigUint64Array.prototype[@@iterator]()`](/en/webfrontend/TypedArray.prototype[@@iterator])**|Returns a new Array Iterator object that contains the values for each index in the array.|

## Examples

Different ways to create a `BigUint64Array`:

```JavaScript
// From a length
var biguint64 = new BigUint64Array(2);
biguint64[0] = 42n;
console.log(biguint64[0]); // 42n
console.log(biguint64.length); // 2
console.log(biguint64.BYTES_PER_ELEMENT); // 8

// From an array
var arr = new BigUint64Array([21n,31n]);
console.log(arr[1]); // 31n

// From another TypedArray
var x = new BigUint64Array([21n, 31n]);
var y = new BigUint64Array(x);
console.log(y[0]); // 21n

// From an ArrayBuffer
var buffer = new ArrayBuffer(32);
var z = new BigUint64Array(buffer, 0, 4);

// From an iterable
var iterable = function*(){ yield* [1n, 2n, 3n]; }();
var biguint64 = new BigUint64Array(iterable);
// BigUint64Array[1n, 2n, 3n]
```
