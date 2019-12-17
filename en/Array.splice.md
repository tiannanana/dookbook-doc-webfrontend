TOPICS: Array.splice
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.splice()`

The `splice()` method changes the contents of an array by removing or replacing existing
elements and/or adding new elements in place.

## Syntax

```javascript
var arrDeletedItems = array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

| parameter | Description |
| :-- | :-- |
| `start` | The index at which to `start` changing the array. If greater than the length of the array, `start` will be set to the length of the array. If negative, it will begin that many elements from the end of the array (with origin `-1`, meaning `-n` is the index of the nth last element and is therefore equivalent to the index of `array.length - n`). If `array.length + start` is less than `0`, it will begin from index `0`.
| `deleteCount` Optional | An integer indicating the number of elements in the array to remove from start.<br>If deleteCount is omitted, or if its value is equal to or larger than `array.length - start` (that is, if it is equal to or greater than the number of elements left in the array, starting at `start`), then all the elements from `start` to the end of the array will be deleted. (It won't delete all under IE8 when `deleteCount` is omitted.)<br>If deleteCount is `0` or negative, no elements are `removed`. In this case, you should specify at least one new element (see below). |
| `item1, item2, ...` Optional | The elements to add to the array, beginning from `start`. If you do not specify any elements, `splice()` will only remove elements from the array. |

**Return value**: An array containing the `deleted` elements. If only one element is `removed`, an
array of one element is returned. If no elements are `removed`, an empty array is returned.

## Description

If the specified number of elements to insert differs from the number of elements being removed, the
array's length will be different at the end of the call.

## Examples

### Remove `0` (zero) elements from index `2`, and insert "drum"

```javascript
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum');

// myFish is ["angel", "clown", "drum", "mandarin", "sturgeon"]
// removed is [], no elements removed
```

Remove `0` (zero) elements from index `2`, and insert "drum" and "guitar"

```javascript
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2, 0, 'drum', 'guitar');

// myFish is ["angel", "clown", "drum", "guitar", "mandarin", "sturgeon"]
// removed is [], no elements removed
```

### Remove `1` element from index `3`

```javascript
var myFish = ['angel', 'clown', 'drum', 'mandarin', 'sturgeon'];
var removed = myFish.splice(3, 1);

// removed is ["mandarin"]
// myFish is ["angel", "clown", "drum", "sturgeon"]
```

### Remove `1` element from index `2`, and insert "trumpet"

```javascript
var myFish = ['angel', 'clown', 'drum', 'sturgeon'];
var removed = myFish.splice(2, 1, 'trumpet');

// myFish is ["angel", "clown", "trumpet", "sturgeon"]
// removed is ["drum"]
```

Remove `2` elements from index `0`, and insert "parrot", "anemone" and "blue"

```javascript
var myFish = ['angel', 'clown', 'trumpet', 'sturgeon'];
var removed = myFish.splice(0, 2, 'parrot', 'anemone', 'blue');

// myFish is ["parrot", "anemone", "blue", "trumpet", "sturgeon"]
// removed is ["angel", "clown"]
```

### Remove `2` elements from index `2`

```javascript
var myFish = ['parrot', 'anemone', 'blue', 'trumpet', 'sturgeon'];
var removed = myFish.splice(2, 2);

// myFish is ["parrot", "anemone", "sturgeon"]
// removed is ["blue", "trumpet"]
```

### Remove `1` element from index `-2`

```javascript
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(-2, 1);

// myFish is ["angel", "clown", "sturgeon"]
// removed is ["mandarin"]
```

### Remove all elements after index `2` (incl.)

```javascript
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];
var removed = myFish.splice(2);

// myFish is ["angel", "clown"]
// removed is ["mandarin", "sturgeon"]
```
