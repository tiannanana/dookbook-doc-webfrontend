TOPICS: Date.toJSON
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toJSON()`

The **`toJSON()`** method returns a string representation of the [`Date`](/en/webfrontend/Date) object.

## Syntax

```javascript
dateObj.toJSON()
```

**parameter**: No parameters

**Return value**: String

## Description

[`Date`](/en/webfrontend/Date) instances refer to a specific point in time. Calling `toJSON()`
returns a string (using [`toISOString()`](/en/webfrontend/Date.toISOString)) representing the
[`Date`](/en/webfrontend/Date) object's value. This method is generally intended to, by default,
usefully serialize [`Date`](/en/webfrontend/Date) objects during JSON serialization.

## Examples

### Using `toJSON()`

```javascript
var jsonDate = (new Date()).toJSON();
var backToDate = new Date(jsonDate);

console.log(jsonDate); //2015-10-26T07:46:36.611Z
```
