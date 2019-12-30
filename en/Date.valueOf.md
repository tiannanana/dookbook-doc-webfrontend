TOPICS: Date.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.valueOf()`

The **`valueOf()`** method returns the primitive value of a [`Date`](/en/webfrontend/Date) object.

## Syntax

```javascript
dateObj.valueOf()
```

**parameter**: No parameters

**Return value**: Number

## Description

The `valueOf()` method returns the primitive value of a [`Date`](/en/webfrontend/Date) object as a
number data type, the number of milliseconds since midnight 01 January, 1970 UTC.

This method is functionally equivalent to the [`Date.getTime()`](/en/webfrontend/Date.getTime) method.

This method is usually called internally by JavaScript and not explicitly in code.

## Examples

### Using `valueOf()`

```javascript
var x = new Date(56, 6, 17);
var myVar = x.valueOf();      // assigns -424713600000 to myVar
```
