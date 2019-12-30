TOPICS: Object.isExtensible
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.isExtensible()`

The **`Object.isExtensible()`** method determines if an object is extensible (whether it can have
new properties added to it).

## Syntax

```javascript
Object.isExtensible(obj)
```

| parameter | Description |
| :-- | :-- |
| `obj` | The object which should be checked. |

**Return value**: A `Boolean` indicating whether or not the given object is extensible.

## Description

Objects are extensible by default: they can have new properties added to them, and (in engines that
support `__proto__`  their `__proto__ property`) can be modified. An object can be marked as
non-extensible using [`Object.preventExtensions()`](/en/webfrontend/Object.preventExtensions),
[`Object.seal()`](/en/webfrontend/Object.seal), or [`Object.freeze()`](/en/webfrontend/Object.freeze).

## Examples

```javascript
// New objects are extensible.
var empty = {};
Object.isExtensible(empty); // === true

// ...but that can be changed.
Object.preventExtensions(empty);
Object.isExtensible(empty); // === false

// Sealed objects are by definition non-extensible.
var sealed = Object.seal({});
Object.isExtensible(sealed); // === false

// Frozen objects are also by definition non-extensible.
var frozen = Object.freeze({});
Object.isExtensible(frozen); // === false
```

## Notes

In ES5, if the argument to this method is not an object (a primitive), then it will cause a
`TypeError`. In ES2015, a non-object argument will be treated as if it was a non-extensible
ordinary object, simply return `false`.

```javascript
Object.isExtensible(1);
// TypeError: 1 is not an object (ES5 code)

Object.isExtensible(1);
// false                         (ES2015 code)
```
