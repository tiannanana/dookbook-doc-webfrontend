TOPICS: DataView
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript DataView Object

The `DataView` view provides a low-level interface for reading and writing multiple number types in
a binary [ArrayBuffer](/en/webfrontend/ArrayBuffer), without having to care about the platform's [[endianness]].

```JavaScript
// create an ArrayBuffer with a size in bytes
const buffer = new ArrayBuffer(16);

// Create a couple of views
const view1 = new DataView(buffer);
const view2 = new DataView(buffer,12,4); //from byte 12 for the next 4 bytes
view1.setInt8(12, 42); // put 42 in slot 12

console.log(view2.getInt8(0));
// expected output: 42
```

## Syntax

```JavaScript
new DataView(buffer [, byteOffset [, byteLength]])
```

### Parameters

| Parameters | Description |
| :-- | :-- |
|**`buffer`**|An existing [ArrayBuffer](/en/webfrontend/ArrayBuffer) or [SharedArrayBuffer](/en/webfrontend/SharedArrayBuffer) to use as the storage backing the new `DataView` object.|
|**`byteOffset`** (*Optional*)|The offset, in bytes, to the first byte in the above buffer for the new view to reference. If unspecified, the buffer view starts with the first byte.|
|**`byteLength`** (*Optional*)|The number of elements in the byte array. If unspecified, the view's length will match the buffer's length.|

### Return value

A new `DataView` object representing the specified data buffer.
(That probably wasn't a very helpful description.)

You can think of the returned object as an "interpreter" of the array buffer of bytes — it knows
how to convert numbers to fit within the buffer correctly, both when reading and writing to it.
This means handling integer and float conversion, endianness,
and other details of representing numbers in binary form.

### Exceptions

| Exceptions | Description |
| :-- | :-- |
|**[`RangeError`](/en/webfrontend/RangeError)**| Thrown if the `byteOffset` or `byteLength` parameter values result in the view extending past the end ofthe `buffer`.For example, if the `buffer` is `16` bytes long, the `byteOffset` is `8`, and the `byteLength` is `10`,this error is thrown because the resulting view tries to extend `2` bytes past the total length of the `buffer`.|

## Description

### Endianness

Multi-byte number formats are represented in memory differently depending on machine architecture —
see [[Endianness]] for an explanation. `DataView`accessors provide explicit control of how data
is accessed, regardless of the executing computer's endianness.

```JavaScript
var littleEndian = (function() {
  var buffer = new ArrayBuffer(2);
  new DataView(buffer).setInt16(0, 256, true /* littleEndian */);
  // Int16Array uses the platform's endianness.
  return new Int16Array(buffer)[0] === 256;
})();
console.log(littleEndian); // true or false
```

### 64-bit Integer Values

Because JavaScript does not currently include standard support for 64-bit integer values,
DataView does not offer native 64-bit operations. As a workaround,
you could implement your own `getUint64()` function to obtain a value with precision up to
[Number.MAX_SAFE_INTEGER](/en/webfrontend/Number.MAX_SAFE_INTEGER),
which could suffice for certain cases.

```JavaScript
function getUint64(dataview, byteOffset, littleEndian) {
  // split 64-bit number into two 32-bit (4-byte) parts
  const left =  dataview.getUint32(byteOffset, littleEndian);
  const right = dataview.getUint32(byteOffset+4, littleEndian);

  // combine the two 32-bit values
  const combined = littleEndian? left + 2**32*right : 2**32*left + right;

  if (!Number.isSafeInteger(combined))
    console.warn(combined, 'exceeds MAX_SAFE_INTEGER. Precision may be lost');

  return combined;
}
```

Alternatively, if you need full 64-bit range, you can create a [BigInt](/en/webfrontend/BigInt). Further,
although native BigInts are much faster than user-land library equivalents,
BigInts will always be much slower than 32-bit integers in JavaScript due to
the nature of their variable size.

```JavaScript
const BigInt = window.BigInt, bigThirtyTwo = BigInt(32), bigZero = BigInt(0);
function getUint64BigInt(dataview, byteOffset, littleEndian) {
  // split 64-bit number into two 32-bit (4-byte) parts
  const left = BigInt(dataview.getUint32(byteOffset|0, !!littleEndian)>>>0);
  const right = BigInt(dataview.getUint32((byteOffset|0) + 4|0, !!littleEndian)>>>0);

  // combine the two 32-bit values and return
  return littleEndian ? (right<<bigThirtyTwo)|left : (left<<bigThirtyTwo)|right;
}
```

## Properties

All `DataView` instances inherit from [DataView.prototype](/en/webfrontend/DataView.prototype) and
allows the addition of properties to all DataView objects.

| Properties| Description |
| :-- | :-- |
|**DataView.prototype.constructor**|Specifies the function that creates an object's prototype. The initial value is the standard built-in DataView constructor.|
|**[DataView.prototype.buffer](/en/webfrontend/DataView.prototype.buffer)** *(Read only)*|The [ArrayBuffer](/en/webfrontend/ArrayBuffer) referenced by this view. Fixed at construction time and thus read only.|
|**[DataView.prototype.byteLength](/en/webfrontend/DataView.prototype.byteLength)** *(Read only)*|The length (in bytes) of this view from the start of its [ArrayBuffer](/en/webfrontend/ArrayBuffer). Fixed at construction time and thus read only.|
|**[DataView.prototype.byteOffset](/en/webfrontend/DataView.prototype.byteOffset)** *(Read only)*|The offset (in bytes) of this view from the start of its [ArrayBuffer](/en/webfrontend/ArrayBuffer). Fixed at construction time and thus read only.|

## Methods

### Read

| Methods | Description |
| :-- | :-- |
|**[`DataView.prototype.getInt8()`](/en/webfrontend/DataView.prototype.getInt8)**|Gets a signed 8-bit integer (byte) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getUint8()`](/en/webfrontend/DataView.prototype.getUint8)**|Gets an unsigned 8-bit integer (unsigned byte) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getInt16()`](/en/webfrontend/DataView.prototype.getInt16)**|Gets a signed 16-bit integer (short) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getUint16()`](/en/webfrontend/DataView.prototype.getUint16)**|Gets an unsigned 16-bit integer (unsigned short) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getInt32()`](/en/webfrontend/DataView.prototype.getInt32)**|Gets a signed 32-bit integer (long) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getUint32()`](/en/webfrontend/DataView.prototype.getUint32)**|Gets an unsigned 32-bit integer (unsigned long) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getFloat32()`](/en/webfrontend/DataView.prototype.getFloat32)**|Gets a signed 32-bit float (float) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getFloat64()`](/en/webfrontend/DataView.prototype.getFloat64)**|Gets a signed 64-bit float (double) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getBigInt64()`](/en/webfrontend/DataView.prototype.getBigInt64)**|Gets a signed 64-bit integer (long long) at the specified byte offset from the start of the view.|
|**[`DataView.prototype.getBigUint64()`](/en/webfrontend/DataView.prototype.getBigUint64)**|Gets an unsigned 64-bit integer (unsigned long long) at the specified byte offset from the start of the view.|

### Write

| Methods | Description |
| :-- | :-- |
|**[`DataView.prototype.setInt8()`](/en/webfrontend/DataView.prototype.setInt8)**|Stores a signed 8-bit integer (byte) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setUint8()`](/en/webfrontend/DataView.prototype.setUint8)**|Stores an unsigned 8-bit integer (unsigned byte) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setInt16()`](/en/webfrontend/DataView.prototype.setInt16)**|Stores a signed 16-bit integer (short) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setUint16()`](/en/webfrontend/DataView.prototype.setUint16)**|Stores an unsigned 16-bit integer (unsigned short) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setInt32()`](/en/webfrontend/DataView.prototype.setInt32)**|Stores a signed 32-bit integer (long) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setUint32()`](/en/webfrontend/DataView.prototype.setUint32)**|Stores an unsigned 32-bit integer (unsigned long) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setFloat32()`](/en/webfrontend/DataView.prototype.setFloat32)**|Stores a signed 32-bit float (float) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setFloat64()`](/en/webfrontend/DataView.prototype.setFloat64)**|Stores a signed 64-bit float (double) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setBigInt64()`](/en/webfrontend/DataView.prototype.setBigInt64)**|Stores a signed 64-bit integer (long long) value at the specified byte offset from the start of the view.|
|**[`DataView.prototype.setBigUint64()`](/en/webfrontend/DataView.prototype.setBigUint64)**|Stores an unsigned 64-bit integer (unsigned long long) value at the specified byte offset from the start of the view.|

## Example

```JavaScript
var buffer = new ArrayBuffer(16);
var view = new DataView(buffer, 0);

view.setInt16(1, 42);
view.getInt16(1); // 42
```
