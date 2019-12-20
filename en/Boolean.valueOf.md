TOPICS: Boolean.valueOf

# `Boolean.valueOf()`

The `valueOf()` method returns the primitive value of a [`Boolean` object](/en/webfrontend/Boolean).

## Syntax

```javascript
bool.valueOf()
```

**parameter**: No parameters

**Return value**: The primitive value of the given `Boolean` object

## Description

The `valueOf` method of [`Boolean`](/en/webfrontend/Boolean) returns the primitive value of a
[`Boolean` object](/en/webfrontend/Boolean) or literal
[`Boolean`](/en/webfrontend/Boolean) as a [`Boolean` data type](/en/glossary/Boolean).

This method is usually called internally by JavaScript and not explicitly in code.

## Examples

```javascript
x = new Boolean();
myVar = x.valueOf(); // assigns false to myVar
```
