TOPICS: Object.getPrototypeOf
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.getPrototypeOf()`

The **`Object.getPrototypeOf()`** method returns the prototype (i.e. the value of the internal
`[[Prototype]]` property) of the specified object.

## Syntax

```javascript
Object.getPrototypeOf(obj)
```

| parameter | Description |
| :-- | :-- |
| `obj` | The object whose prototype is to be returned. |

**Return value**: The prototype of the given object. If there are no inherited properties,
`null` is returned.

## Examples

```javascript
var proto = {};
var obj = Object.create(proto);
Object.getPrototypeOf(obj) === proto; // true
```

## Notes

In ES5, it will throw a `TypeError` exception if the obj parameter isn't an object. In ES2015,
the parameter will be coerced to an [`Object`](/en/webfrontend/Object).

```javascript
Object.getPrototypeOf('foo');
// TypeError: "foo" is not an object (ES5 code)
Object.getPrototypeOf('foo');
// String.prototype                  (ES2015 code)
```
