TOPICS: null

# JavaScript Null Object: `null`

The value `null` represents the **intentional absence of any object value**.
It is one of *[[JavaScript]]*'s *primitive values* and is treated as **falsy** for boolean operations.

## Syntax

```javascript
null
```

## Description

The value `null` is written with a literal: `null`. `null` is not an identifier for a property of the
global object, like [`undefined`](/en/webfrontend/undefined) can be. Instead, `null` expresses a
lack of identification, indicating
that a variable points to no object. In APIs, `null` is often retrieved in a place where an object
can be expected but no object is relevant.

```javascript
// foo does not exist. It is not defined and has never been initialized:
foo;
"ReferenceError: foo is not defined"

// foo is known to exist now but it has no type or value:
var foo = null;
foo;
"null"
```

## Difference Between `null` And `undefined`

When checking for `null` or `undefined`, beware of the differences between equality (`==`) and identity
(`===`) operators, as the former performs type-conversion.

```javascript
typeof null          // "object" (not "null" for legacy reasons)
typeof undefined     // "undefined"
null === undefined   // false
null  == undefined   // true
null === null        // true
null == null         // true
!null                // true
isNaN(1 + null)      // false
isNaN(1 + undefined) // true
```

## More

- [Null Glossary](/en/glossary/Null)
