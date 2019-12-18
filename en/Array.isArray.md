TOPICS: Array.isArray
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Array.isArray()`

The `Array.isArray()` method determines whether the passed value is an Array.

```javascript
Array.isArray([1, 2, 3]);  // true
Array.isArray({foo: 123}); // false
Array.isArray('foobar');   // false
Array.isArray(undefined);  // false
```

## Syntax

```javascript
Array.isArray(value)
```

| parameter | Description |
| :-- | :-- |
| `value` | The value to be checked. |

**Return value**: true if the value is an `Array`; otherwise, `false`.

## Description

If the value is an [`Array`](/en/webfrontend/Array), `true` is returned; otherwise, `false` is.

See the article [“Determining with absolute accuracy whether or not a JavaScript object is an array”](http://web.mit.edu/jwalden/www/isArray.html)
for more details. Given a [`TypedArray`](/en/webfrontend/TypedArray) instance, false is always returned.

## Examples

```javascript
// all following calls return true
Array.isArray([]);
Array.isArray([1]);
Array.isArray(new Array());
Array.isArray(new Array('a', 'b', 'c', 'd'));
Array.isArray(new Array(3));
// Little known fact: Array.prototype itself is an array:
Array.isArray(Array.prototype);

// all following calls return false
Array.isArray();
Array.isArray({});
Array.isArray(null);
Array.isArray(undefined);
Array.isArray(17);
Array.isArray('Array');
Array.isArray(true);
Array.isArray(false);
Array.isArray(new Uint8Array(32));
Array.isArray({ __proto__: Array.prototype });
```

### `instanceof` vs `isArray`

When checking for `Array` instance, `Array.isArray` is preferred over `instanceof` because it works
through `iframes`.

```javascript
var iframe = document.createElement('iframe');
document.body.appendChild(iframe);
xArray = window.frames[window.frames.length-1].Array;
var arr = new xArray(1,2,3); // [1,2,3]

// Correctly checking for Array
Array.isArray(arr);  // true
// Considered harmful, because doesn't work through iframes
arr instanceof Array; // false
```

## Polyfill

Running the following code before any other code will create `Array.isArray()` if it's not natively available.

```javascript
if (!Array.isArray) {
  Array.isArray = function(arg) {
    return Object.prototype.toString.call(arg) === '[object Array]';
  };
}
```
