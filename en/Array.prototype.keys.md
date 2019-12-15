TOPICS: Array.prototype.keys
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.keys()`

The `keys()` method returns a new Array Iterator object that contains the `keys` for each index in
the array.

## Syntax

```javascript
arr.keys()
```

**parameter**: No parameters

**Return value**: A new Array iterator object.

## Examples

### Key iterator doesn't ignore holes

```javascript
var arr = ['a', , 'c'];
var sparseKeys = Object.keys(arr);
var denseKeys = [...arr.keys()];
console.log(sparseKeys); // ['0', '2']
console.log(denseKeys);  // [0, 1, 2]
```
