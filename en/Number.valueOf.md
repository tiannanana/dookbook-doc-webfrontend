TOPICS: Number.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Number.valueOf()`

The **`valueOf()`** method returns the wrapped primitive value of a [`Number`](/en/webfrontend/Number)
object.

## Syntax

```javascript
numObj.valueOf()
```

**parameter**: No parameters

**Return value**: A number representing the primitive value of the specified `Number` object.

## Description

This method is usually called internally by JavaScript and not explicitly in web code.

## Examples

### Using `valueOf`

```javascript
var numObj = new Number(10);
console.log(typeof numObj); // object

var num = numObj.valueOf();
console.log(num);           // 10
console.log(typeof num);    // number
```
