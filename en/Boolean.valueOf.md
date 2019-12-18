TOPICS: Boolean.valueOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Boolean.valueOf()`

The `valueOf()` method returns the primitive value of a [`Boolean`](/en/webfrontend/Boolean) object.

## Syntax

```javascript
bool.valueOf()
```

**parameter**: No parameters

**Return value**: The primitive value of the given `Boolean` object

## Description

The `valueOf` method of [`Boolean`](/en/webfrontend/Boolean) returns the primitive value of a
[`Boolean`](/en/webfrontend/Boolean) object or literal
[`Boolean`](/en/webfrontend/Boolean) as a [`Boolean`](/en/webfrontend/Boolean) data type.

This method is usually called internally by JavaScript and not explicitly in code.

## Examples

### Using `valueOf`

```javascript
x = new Boolean();
myVar = x.valueOf(); // assigns false to myVar
```
