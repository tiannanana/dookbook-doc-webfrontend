TOPICS: Object.toString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Object.toString()`

The **`toString()`** method returns a string representing the object.

## Syntax

```javascript
obj.toString()
```

**parameter**: No parameters

**Return value**: A string representing the object.

## Description

Every object has a `toString()` method that is automatically called when the object is to be
represented as a text value or when an object is referred to in a manner in which a string is
expected. By default, the `toString()` method is inherited by every object descended from `Object`.
If this method is not overridden in a custom object, `toString()` returns "`[object type]`",
where `type` is the object type. The following code illustrates this:

```javascript
var o = new Object();
o.toString(); // returns [object Object]
```

!!! warn "Note"
    Starting in JavaScript 1.8.5, `toString()` called on `null` returns `[object Null]`, and
    `undefined` returns `[object Undefined]`, as defined in the 5th Edition of ECMAScript and a
    subsequent Errata. See Using `toString()` to detect object class.

## Examples

### Overriding the default toString method

You can create a function to be called in place of the default `toString()` method. The `toString()`
method takes no arguments and should return a string. The `toString()` method you create can be any
value you want, but it will be most useful if it carries information about the object.

The following code defines the `Dog` object type and creates `theDog`, an object of type `Dog`:

```javascript
function Dog(name, breed, color, sex) {
  this.name = name;
  this.breed = breed;
  this.color = color;
  this.sex = sex;
}

theDog = new Dog('Gabby', 'Lab', 'chocolate', 'female');
```

If you call the `toString()` method on this custom object, it returns the default value inherited
from `Object`:

```javascript
theDog.toString(); // returns [object Object]
```

The following code creates and assigns `dogToString()` to override the default `toString()` method.
This function generates a string containing the name, breed, color, and sex of the object,
in the form "`property = value;`".

```javascript
Dog.prototype.toString = function dogToString() {
  var ret = 'Dog ' + this.name + ' is a ' + this.sex + ' ' + this.color + ' ' + this.breed;
  return ret;
}
```

or

```javascript
Dog.prototype.toString = function dogToString() {
  return `Dog ${this.name} is a ${this.sex} ${this.color} ${this.breed}`;
}
```

With the preceding code in place, any time `theDog` is used in a string context, JavaScript
automatically calls the `dogToString()` function, which returns the following string:

```javascript
"Dog Gabby is a female chocolate Lab"
```

### Using `toString()` to detect object class

`toString()` can be used with every object and allows you to get its class. To use the
`Object.toString()` with every object, you need to call [`Function.call()`](/en/webfrontend/Function.call)
or [`Function.apply()`](/en/webfrontend/Function.apply) on it, passing the object you want to
inspect as the first parameter called `thisArg`.

```javascript
var toString = Object.prototype.toString;

toString.call(new Date);    // [object Date]
toString.call(new String);  // [object String]
toString.call(Math);        // [object Math]

// Since JavaScript 1.8.5
toString.call(undefined);   // [object Undefined]
toString.call(null);        // [object Null]
```
