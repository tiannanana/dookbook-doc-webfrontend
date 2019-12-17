TOPICS: Boolean.prototype.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Boolean.prototype.toString()`

The `toString()` method returns a string representing the specified [`Boolean`](/en/webfrontend/Boolean_Object)
object.

## Syntax

```javascript
bool.toString()
```

**parameter**: No parameters

**Return value**: A string representing the specified `Boolean` object.

## Description

The [`Boolean`](/en/webfrontend/Boolean_Object) object overrides the `toString` method of the
[Object](/en/webfrontend/Object) object; it does not inherit [`Object.prototype.toString()`](/en/webfrontend/Object.prototype.toString).
For Boolean objects, the `toString` method returns a string representation of the object.

JavaScript calls the `toString` method automatically when a [`Boolean`](/en/webfrontend/Boolean_Object)
is to be represented as a text value or when a Boolean is referred to in a string concatenation.

For [`Boolean`](/en/webfrontend/Boolean_Object) objects and values, the built-in `toString` method
returns the string "`true`" or "`false`" depending on the value of the
[`boolean`](/en/webfrontend/Boolean_Object) object.

## Examples

### Using `toString`

In the following code, `flag.toString()` returns "`true`":

```javascript
var flag = new Boolean(true);
var myVar = flag.toString();
```
