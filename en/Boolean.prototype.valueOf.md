TOPICS: Boolean.prototype.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Boolean.prototype.valueOf()`

The `valueOf()` method returns the primitive value of a [`Boolean`](/en/webfrontend/Boolean_Object) object.

## Syntax

```javascript
bool.valueOf()
```

**parameter**: No parameters

**Return value**: The primitive value of the given `Boolean` object

## Description

The `valueOf` method of [`Boolean`](/en/webfrontend/Boolean_Object) returns the primitive value of a
[`Boolean`](/en/webfrontend/Boolean_Object) object or literal
[`Boolean`](/en/webfrontend/Boolean_Object) as a [`Boolean`](/en/webfrontend/Boolean_Object) data type.

This method is usually called internally by JavaScript and not explicitly in code.

## Examples

### Using `valueOf`

```javascript
x = new Boolean();
myVar = x.valueOf(); // assigns false to myVar
```
