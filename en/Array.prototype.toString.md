TOPICS: Array.prototype.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.prototype.toString()`

The `toString()` method returns a string representing the specified array and its elements.

## Syntax

```javascript
arr.toString()
```

**parameter**: No parameters

**Return value**: A string representing the elements of the array.

## Description

The [`Array`](/en/webfrontend/Array_Object) object overrides the `toString` method of [`Object`](/en/webfrontend/Object).
For Array objects, the `toString` method joins the array and returns one string containing each
array element separated by commas.

JavaScript calls the `toString` method automatically when an array is to be represented as a text
value or when an array is referred to in a string concatenation.

### ECMAScript 5 semantics

Starting in JavaScript 1.8.5 (Firefox 4), and consistent with ECMAScript 5th edition semantics,
the `toString()` method is generic and can be used with any object. [`Object.prototype.toString()`](/en/webfrontend/Object.prototype.toString)
will be called, and the resulting value will be returned.
