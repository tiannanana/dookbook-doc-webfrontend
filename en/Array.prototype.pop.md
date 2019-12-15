TOPICS: Array.prototype.pop
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.pop()`

The `pop()` method removes the last element from an array and returns that element. This method
changes the length of the array.

## Syntax

```html
arr.pop()
```

**parameter**: No parameters

**Return value**: The removed element from the array; undefined if the array is empty.

## Description

The `pop` method removes the last element from an array and returns that value to the caller.

`pop` is intentionally generic; this method can be [`called`](/en/webfrontend/Function.prototype.call)
or [`applied`](/en/webfrontend/Function.prototype.apply) to objects resembling arrays. Objects which
do not contain a length property reflecting the last in a series of consecutive, zero-based numerical
properties may not behave in any meaningful manner.

If you call `pop()` on an empty array, it returns [`undefined`](/en/webfrontend/undefined).

[`Array.prototype.shift()`](/en/webfrontend/Array.prototype.shift) has similar behavior to `pop`, but
applied to the first element in an array.

## Examples

## Removing the last element of an array

The following code creates the myFish array containing four elements, then removes its last element.

```javascript
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];

var popped = myFish.pop();

console.log(myFish); // ['angel', 'clown', 'mandarin' ]

console.log(popped); // 'sturgeon'
```

### Using apply( ) or call ( ) on array-like objects

The following code creates the myFish array-like object containing four elements and a length
parameter, then removes its last element and decrements the length parameter.

```javascript
var myFish = {0:'angel', 1:'clown', 2:'mandarin', 3:'sturgeon', length: 4};

var popped = Array.prototype.pop.call(myFish); //same syntax for using apply( )

console.log(myFish); // {0:'angel', 1:'clown', 2:'mandarin', length: 3}

console.log(popped); // 'sturgeon'
```
