TOPICS: Array.prototype.entries
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.prototype.entries()`

The `entries()` method returns a new **`Array Iterator`** object that contains the key/value pairs
for each index in the array.

## Syntax

```javascript
arr.entries()
```

**parameter**: No parameters

**Return value**：Array

## Examples

### Iterating with index and element

```javascript
const a = ['a', 'b', 'c'];

for (const [index, element] of a.entries())
  console.log(index, element);

// 0 'a'
// 1 'b'
// 2 'c'
```

### Using a for…of loop

```javascript
Using a for…of loop
```
