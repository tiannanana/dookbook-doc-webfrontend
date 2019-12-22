TOPICS: Number
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Number Object

The **`Number`** JavaScript object is a wrapper object allowing you to work with numerical values.
A `Number` object is created using the **`Number()`** **constructor**. A primitive type object
**number** is created using the **`Number()` function**.

The JavaScript `Number` type is double-precision 64-bit binary format IEEE 754 value. In more recent
implementations, JavaScript also supports integers with arbitrary precision using the
[`BigInt`](/en/webfrontend/BigInt) type.

## Syntax

```javascript
new Number(value)
let a = new Number('123') // a === 123 is false
let b = Number('123') // b === 123 is true
a instanceof Number // is true
b instanceof Number // is false
```

| parameter | Description |
| :-- | :-- |
| `value` | The numeric value of the object being created. |

## Description

The primary uses of the `Number` object are:

- If the argument cannot be converted into a number, it returns `NaN`.
- In a non-constructor context (i.e., without the [`new`](/en/webfrontend/new) operator),
Number can be used to perform a type conversion.

## Attributes

### `Number.EPSILON`

The **`Number.EPSILON`** property represents the difference between `1` and the smallest floating point
`number` greater than `1`.

You do not have to create a `Number` object to access this static property (use `Number.EPSILON`).

The `EPSILON` property has a value of approximately `2.2204460492503130808472633361816E-16`, or `2-^52^`.

### `Number.MAX_SAFE_INTEGER`

The **`Number.MAX_SAFE_INTEGER`** constant represents the maximum safe integer in JavaScript
(`2^53^ - 1`).

For larger integers, consider using [`BigInt`](/en/webfrontend/BigInt).

The `MAX_SAFE_INTEGER` constant has a value of `9007199254740991` (9,007,199,254,740,991 or ~9
quadrillion). The reasoning behind that number is that JavaScript uses double-precision
floating-point format numbers as specified in IEEE 754 and can only safely represent
numbers between `-(2^53^ - 1)` and `2^53^ - 1`.

Safe in this context refers to the ability to represent integers exactly and to correctly compare
them. For example, `Number.MAX_SAFE_INTEGER + 1 === Number.MAX_SAFE_INTEGER + 2` will evaluate
to `true`, which is mathematically incorrect. See
[`Number.isSafeInteger()`](/en/webfrontend/Number.isSafeInteger) for more information.

This field does not exist in old browsers. Using it without checking its existence, such as
`Math.max(Number.MAX_SAFE_INTEGER, 2)`, will yield undesired results such as NaN.

Because `MAX_SAFE_INTEGER` is a static property of `Number`, you always use it as
`Number.MAX_SAFE_INTEGER`, rather than as a property of a `Number` object you created.

### `Number.MAX_VALUE`

The **`Number.MAX_VALUE`** property represents the maximum numeric value representable in JavaScript.

The `MAX_VALUE` property has a value of approximately `1.79E+308`, or 2^1024^. Values larger than
`MAX_VALUE` are represented as `Infinity`.

Because `MAX_VALUE` is a static property of `Number`, you always use it as `Number.MAX_VALUE`, rather
than as a property of a `Number` object you created.

### `Number.MIN_SAFE_INTEGER`

The **`Number.MIN_SAFE_INTEGER`** constant represents the minimum safe integer in JavaScript
(`-(2^53^ - 1)`).

To represent integers smaller than this, consider using [`BigInt`](/en/webfrontend/BigInt).

The `MIN_SAFE_INTEGER` constant has a value of `-9007199254740991` (-9,007,199,254,740,991 or about
-9 quadrillion). The reasoning behind that number is that JavaScript uses double-precision
floating-point format numbers as specified in IEEE 754 and can only safely represent numbers between
`-(2^53^ - 1)` and `2^53^ - 1`.  See [`Number.isSafeInteger()`](/en/webfrontend/Number.isSafeInteger)
for more information.

Because `MIN_SAFE_INTEGER` is a static property of `Number`, you always use it as
`Number.MIN_SAFE_INTEGER`, rather than as a property of a `Number` object you created.

### `Number.MIN_VALUE`

The **`Number.MIN_VALUE`** property represents the smallest positive numeric value representable in JavaScript.

The `MIN_VALUE` property is the number closest to `0`, not the most negative number, that JavaScript
can represent.

`MIN_VALUE` has a value of approximately `5e-324`. Values smaller than `MIN_VALUE`
("underflow values") are converted to `0`.

Because `MIN_VALUE` is a static property of `Number`, you always use it as `Number.MIN_VALUE`,
rather than as a property of a `Number` object you created.

### `Number.NEGATIVE_INFINITY`

The **`Number.NEGATIVE_INFINITY`** property represents the negative `Infinity` value.

The value of `Number.NEGATIVE_INFINITY` is the same as the negative value of the global object's
`Infinity` property.

This value behaves slightly differently than mathematical `infinity`:

- Any positive value, including `POSITIVE_INFINITY`, multiplied by `NEGATIVE_INFINITY` is `NEGATIVE_INFINITY`.
- Any negative value, including `NEGATIVE_INFINITY`, multiplied by `NEGATIVE_INFINITY` is `POSITIVE_INFINITY`.
- Any positive value divided by `NEGATIVE_INFINITY` is negative zero.
- Any negative value divided by `NEGATIVE_INFINITY` is positive zero.
- Zero multiplied by `NEGATIVE_INFINITY` is `NaN`.
- `NaN` multiplied by `NEGATIVE_INFINITY` is `NaN`.
- `NEGATIVE_INFINITY`, divided by any negative value except `NEGATIVE_INFINITY`, is `POSITIVE_INFINITY`.
- `NEGATIVE_INFINITY`, divided by any positive value except `POSITIVE_INFINITY`, is `NEGATIVE_INFINITY`.
- `NEGATIVE_INFINITY`, divided by either `NEGATIVE_INFINITY` or `POSITIVE_INFINITY`, is `NaN`.

You might use the `Number.NEGATIVE_INFINITY` property to indicate an error condition that returns a
finite number in case of success. Note, however, that [`isFinite`](/en/webfrontend/Number.isFinite)
would be more appropriate in such a case.

Because `NEGATIVE_INFINITY` is a static property of `Number`, you always use it as
`Number.NEGATIVE_INFINITY`, rather than as a property of a `Number` object you created.

### `Number.NaN`

The **`Number.NaN`** property represents Not-A-Number. Equivalent of `NaN`.

You do not have to create a `Number` object to access this static property (use `Number.NaN`).

### `Number.POSITIVE_INFINITY`

The **`Number.POSITIVE_INFINITY`** property represents the positive `Infinity` value.

The value of `Number.POSITIVE_INFINITY` is the same as the value of the global object's `Infinity` property.

This value behaves slightly differently than mathematical `infinity`:

- Any positive value, including `POSITIVE_INFINITY`, multiplied by `POSITIVE_INFINITY` is `POSITIVE_INFINITY`.
- Any negative value, including `NEGATIVE_INFINITY`, multiplied by `POSITIVE_INFINITY` is `NEGATIVE_INFINITY`.
- Any positive number divided by `POSITIVE_INFINITY` is positive Zero.
- Any negative number divided by `POSITIVE_INFINITY` is negative Zero.
- Zero multiplied by `POSITIVE_INFINITY` is `NaN`.
- `NaN` multiplied by `POSITIVE_INFINITY` is `NaN`.
- `POSITIVE_INFINITY`, divided by any negative value except `NEGATIVE_INFINITY`, is `NEGATIVE_INFINITY`.
- `POSITIVE_INFINITY`, divided by any positive value except `POSITIVE_INFINITY`, is `POSITIVE_INFINITY`.
- `POSITIVE_INFINITY`, divided by either `NEGATIVE_INFINITY` or `POSITIVE_INFINITY`, is `NaN`.

You might use the `Number.POSITIVE_INFINITY` property to indicate an error condition that returns a
finite number in case of success. Note, however, that isFinite would be more appropriate in such a case.

Because `POSITIVE_INFINITY` is a static property of `Number`, you always use it as
`Number.POSITIVE_INFINITY`, rather than as a property of a `Number` object you created.

### `Number.prototype`

The **`Number.prototype`** property represents the prototype for the `Number` constructor.

All `Number` instances inherit from `Number.prototype`. The prototype object of the `Number`
constructor can be modified to affect all `Number` instances.

## Examples

### Using `getFullYear()`

The following example assigns the four-digit value of the current year to the variable `year`.

```javascript
var today = new Date();
var year = today.getFullYear();
```
