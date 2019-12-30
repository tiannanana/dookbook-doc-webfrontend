TOPICS: Object.hasOwnProperty
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.hasOwnProperty()`

The **`hasOwnProperty()`** method returns a boolean indicating whether the object has the specified
property as its own property (as opposed to inheriting it).

## Syntax

```javascript
obj.hasOwnProperty(prop)
```

| parameter | Description |
| :-- | :-- |
| `prop` | The `String` name or Symbol of the property to test. |

**Return value**: A `Boolean` indicating whether or not the object has the specified
property as own property.

## Description

All descendents of [`Object`](/en/webfrontend/Object) inherit the `hasOwnProperty` method.
This method can be used to determine whether an object has the specified property as a direct
property of that object; unlike the `in` operator, this method does not check for a property in
the object's prototype chain. If an [`Object`](/en/webfrontend/Object) is an
[`Array`](/en/webfrontend/Array), `hasOwnProperty`  method can check whether an index exists.

## Note

`hasOwnProperty` returns true even if the value of the property is `null` or `undefined`.

```javascript
o = new Object();
o.propOne = null;
o.hasOwnProperty('propOne');   // returns true
o.propTwo = undefined;  
o.hasOwnProperty('propTwo');   // returns true
```

## Examples

### Using `hasOwnProperty` to test for a property's existence

The following example determines whether the `o` object contains a property named `prop`:

```javascript
o = new Object();
o.hasOwnProperty('prop');   // returns false
o.prop = 'exists';  
o.hasOwnProperty('prop');   // returns true
```

### Direct vs. inherited properties

The following example differentiates between direct properties and properties inherited through
the prototype chain:

```javascript
o = new Object();
o.prop = 'exists';
o.hasOwnProperty('prop');             // returns true
o.hasOwnProperty('toString');         // returns false
o.hasOwnProperty('hasOwnProperty');   // returns false
```

### Iterating over the properties of an object

The following example shows how to iterate over the properties of an object without executing on
inherited properties. Note that the `for...in` loop is already only iterating enumerable items,
so one should not assume based on the lack of non-enumerable properties shown in the loop that
`hasOwnProperty` itself is confined strictly to enumerable items (as with [`Object.getOwnPropertyNames()`](/en/webfrontend/Object.getOwnPropertyNames)).

```javascript
var buz = {
  fog: 'stack'
};

for (var name in buz) {
  if (buz.hasOwnProperty(name)) {
    console.log('this is fog (' +
      name + ') for sure. Value: ' + buz[name]);
  }
  else {
    console.log(name); // toString or something else
  }
}
```

### Using hasOwnProperty as a property name

JavaScript does not protect the property name `hasOwnProperty`; thus, if the possibility exists
that an object might have a property with this name, it is necessary to use an external
`hasOwnProperty` to get correct results:

```javascript
var foo = {
  hasOwnProperty: function() {
    return false;
  },
  bar: 'Here be dragons'
};

foo.hasOwnProperty('bar'); // always returns false

// Use another Object's hasOwnProperty
// and call it with 'this' set to foo
({}).hasOwnProperty.call(foo, 'bar'); // true

// It's also possible to use the hasOwnProperty property
// from the Object prototype for this purpose
Object.prototype.hasOwnProperty.call(foo, 'bar'); // true
```

Note that in the last case there are no newly created objects.
