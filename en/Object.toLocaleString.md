TOPICS: Object.toLocaleString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.toLocaleString()`

The **`toLocaleString()`** method returns a string representing the object. This method is meant
to be overridden by derived objects for locale-specific purposes.

## Syntax

```javascript
obj.toLocaleString()
```

**parameter**: No parameters

**Return value**: A string representing the object.

## Description

[`Object`](/en/webfrontend/Object)'s `toLocaleString` returns the result of calling [`toString()`](/en/webfrontend/Object.toString).

This function is provided to give objects a generic `toLocaleString` method, even though not all
may use it. See the list below.

### Objects overriding `toLocaleString`

- [`Array`](/en/webfrontend/Array): [`Array.toLocaleString()`](/en/webfrontend/Array.toLocaleString)
- [`Number`](/en/webfrontend/Number): [`Number.toLocaleString()`](/en/webfrontend/Number.toLocaleString)
- [`Date`](/en/webfrontend/Date): [`Date.toLocaleString()`](/en/webfrontend/Date.toLocaleString)
