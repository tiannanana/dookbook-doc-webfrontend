TOPICS: NaN

# JavaScript Global Property: `NaN`

The global **`NaN`** property is a value representing **Not-A-Number**.

## Syntax

```javascript
NaN
```

## Description

`NaN` is a property of the *global object*.

The initial value of `NaN` is *Not-A-Number* — the same as the value of `Number.NaN`.
In modern browsers, `NaN` is a non-configurable, non-writable property. Even when this is not
the case, avoid overriding it.

It is rather rare to use `NaN` in a program. It is the returned value when [`Math`](/en/webfrontend/Math)
functions fail (`Math.sqrt(-1)`) or when a function trying to parse a number fails (`parseInt("blabla")`).

### Testing against NaN

NaN compares unequal (via `==`, `!=`, `===`, and `!==`) to any other value -- including to another
`NaN` value. Use [`Number.isNaN()`](/en/webfrontend/Number.isNaN) or
[`isNaN()`](/en/webfrontend/isNaN) to most clearly determine whether a value is `NaN`.
Or perform a self-comparison: `NaN`, and only `NaN`, will compare unequal to itself.

```javascript
NaN === NaN;        // false
Number.NaN === NaN; // false
isNaN(NaN);         // true
isNaN(Number.NaN);  // true

function valueIsNaN(v) { return v !== v; }
valueIsNaN(1);          // false
valueIsNaN(NaN);        // true
valueIsNaN(Number.NaN); // true
```

However, do note the difference between [`isNaN()`](/en/webfrontend/isNaN) and
[`Number.isNaN()`](/en/webfrontend/Number.isNaN): the former will return `true` if the value is
currently `NaN`, or if it is going to be `NaN` after it is coerced to a number, while the latter
will return `true` only if the value is currently `NaN`:

```javascript
isNaN('hello world');        // true
Number.isNaN('hello world'); // false
```
