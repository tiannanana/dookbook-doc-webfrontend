TOPICS: Object.getOwnPropertyDescriptors
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.getOwnPropertyDescriptors()`

The **`Object.getOwnPropertyDescriptors()`** method returns all own property descriptors of a given object.

## Syntax

```javascript
Object.getOwnPropertyDescriptors(obj)
```

| parameter | Description |
| :-- | :-- |
| `obj` | The object for which to get all own property descriptors. |

**Return value**: An object containing all own property descriptors of an object. Might be an
empty object, if there are no properties.

## Description

This method permits examination of the precise description of all own properties of an object.
A property in JavaScript consists of either a string-valued name or a `Symbol` and a property descriptor.
Further information about property descriptor types and their attributes can be found in [`Object.defineProperty()`](/en/webfrontend/Object.defineProperty).

A property descriptor is a record with some of the following attributes:

| Attributes | Description |
| :-- | :-- |
| **`value`** | The value associated with the property (data descriptors only).
| **`writable`** | true if and only if the value associated with the property may be changed (data descriptors only).
| **`get`** | A function which serves as a getter for the property, or `undefined` if there is no getter (accessor descriptors only).
| **`set`** | A function which serves as a setter for the property, or `undefined` if there is no setter (accessor descriptors only).
| **`configurable`** | `true` if and only if the type of this property descriptor may be changed and if the property may be deleted from the corresponding object.
| **`enumerable`** | `true` if and only if this property shows up during enumeration of the properties on the corresponding object.

## Examples

### Creating a shallow clone

Whereas the [`Object.assign()`](/en/webfrontend/Object.assign) method will only copy enumerable
and own properties from a source object to a target object, you are able to use this method and
[`Object.create()`](/en/webfrontend/Object.create) for a shallow copy between two unknown objects:

```javascript
Object.create(
  Object.getPrototypeOf(obj),
  Object.getOwnPropertyDescriptors(obj)
);
```

### Creating a subclass

A typical way of creating a subclass is to define the subclass, set its prototype to an instance of
the superclass, and then define properties on that instance. This can get awkward especially
for getters and setters. Instead, you can use this code to set the prototype:

```javascript
function superclass() {}
superclass.prototype = {
  // Define your methods and properties here
};
function subclass() {}
subclass.prototype = Object.create(
  superclass.prototype,
  {
    // Define your methods and properties here
  }
);
```
