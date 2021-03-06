TOPICS: BigInt

# JavaScript `BigInt` Object

`BigInt` is a built-in object that provides a way to represent whole numbers larger than `253 - 1`,
which is the largest number JavaScript can reliably represent with the
[`Number`](/en/webfrontend/Number) primitive. `BigInt` can be used for arbitrarily large integers.

## Description

A `BigInt` is created by appending `n` to the end of an integer literal — `10n` — or by calling the
function `BigInt()`.

```JavaScript
const theBiggestInt = 9007199254740991n;

const alsoHuge = BigInt(9007199254740991);
// ↪ 9007199254740991n

const hugeString = BigInt("9007199254740991");
// ↪ 9007199254740991n

const hugeHex = BigInt("0x1fffffffffffff");
// ↪ 9007199254740991n

const hugeBin = BigInt("0b11111111111111111111111111111111111111111111111111111");
// ↪ 9007199254740991n
```

`BigInt` is similar to [`Number`](/en/webfrontend/Number) in some ways,
but also differs in a few key matters — it cannot be used with methods in the built-in
[`Math`](/en/webfrontend/Math) object and cannot be mixed with instances of
[`Number`](/en/webfrontend/Number) in operations; they must be coerced to the same type.
Be careful coercing values back and forth, however,
as the precision of a `BigInt` may be lost when it is coerced to a [`Number`](/en/webfrontend/Number).

### Type information

When tested against `typeof`, a `BigInt` will give `"bigint"`:

```JavaScript
typeof 1n === 'bigint'; // true
typeof BigInt('1') === 'bigint'; // true
```

When wrapped in an `Object`, a `BigInt` will be considered as a normal "object" type:

```JavaScript
typeof Object(1n) === 'object'; // true
```

### Operators

The following operators may be used with BigInts (or object-wrapped BigInts): `+`, `*`, `-`, `**`, `%`.
 [`Bitwise` operators](/en/webfrontend/Bitwise) are supported as well,
 except `>>>` (zero-fill right shift) as all BigInts are signed.
 Also unsupported is the unary operator (`+`), in order to not break [asm.js](https://github.com/tc39/proposal-bigint/blob/master/ADVANCED.md#dont-break-asmjs).

```JavaScript
const previousMaxSafe = BigInt(Number.MAX_SAFE_INTEGER);
// ↪ 9007199254740991

const maxPlusOne = previousMaxSafe + 1n;
// ↪ 9007199254740992n

const theFuture = previousMaxSafe + 2n;
// ↪ 9007199254740993n, this works now!

const multi = previousMaxSafe * 2n;
// ↪ 18014398509481982n

const subtr = multi – 10n;
// ↪ 18014398509481972n

const mod = multi % 10n;
// ↪ 2n

const bigN = 2n ** 54n;
// ↪ 18014398509481984n

bigN * -1n
// ↪ –18014398509481984n
```

The `/` operator also works as expected with whole numbers. However,
since these are `BigInts` and not `BigDecimals`, this operation will round towards `0`,
 which is to say, it will not return any fractional digits.

!!! warn ""
    An operation with a fractional result will be truncated when used with a `BigInt`.

```JavaScript
const expected = 4n / 2n;
// ↪ 2n

const rounded = 5n / 2n;
// ↪ 2n, not 2.5n
```

### Comparisons

A `BigInt` is not strictly equal to a [`Number`](/en/webfrontend/Number), but it is loosely so:

```JavaScript
0n === 0
// ↪ false

0n == 0
// ↪ true
```

A [`Number`](/en/webfrontend/Number) and a `BigInt` may be compared as usual:

```JavaScript
1n < 2
// ↪ true

2n > 1
// ↪ true

2 > 2
// ↪ false

2n > 2
// ↪ false

2n >= 2
// ↪ true
```

They may be mixed in arrays and sorted:

```JavaScript
const mixed = [4n, 6, -12n, 10, 4, 0, 0n];
// ↪  [4n, 6, -12n, 10, 4, 0, 0n]

mixed.sort();
// ↪ [-12n, 0, 0n, 10, 4n, 4, 6]
```

Note that comparisons with Object-wrapped BigInts act as with other objects,
only indicating equality when the same object instance is compared:

```JavaScript
0n === Object(0n); // false
Object(0n) === Object(0n); // false

const o = Object(0n);
o === o // true
```

### Conditionals

A `BigInt` behaves like a [`Number`](/en/webfrontend/Number) in cases where it is converted to
a [`Boolean`](/en/webfrontend/Boolean): via the [`Boolean`](/en/webfrontend/Boolean) function;
when used with [logical operators](/en/webfrontend/Logical_Operator) `||`, `&&`, and `!`;
or within a conditional test like an [`if statement`](/en/webfrontend/if_else_statement).

```JavaScript
if (0n) {
  console.log('Hello from the if!');
} else {
  console.log('Hello from the else!');
}

// ↪ "Hello from the else!"

0n || 12n
// ↪ 12n

0n && 12n
// ↪ 0n

Boolean(0n)
// ↪ false

Boolean(12n)
// ↪ true

!12n
// ↪ false

!0n
// ↪ true
```

## Constructor

| methods | description |
| :-- | :--|
|**`BigInt()`**| Creates `BigInt` objects.|

## Static methods

| methods | description |
| :-- | :--|
<<<<<<< HEAD
|**`BigInt.asIntN()`**| Wraps a BigInt value to a signed integer between `-2^^width-1^^` and `2^^width-1^^-1`.|
|**`BigInt.asUintN()`**| Wraps a BigInt value to an unsigned integer between `0` and `2^^width^^-1`.|
=======
|**`BigInt.asIntN()`**| Wraps a BigInt value to a signed integer between \\(-2^{width-1}\\) and \\(2^{width-1}-1\\). |
|**`BigInt.asUintN()`**| Wraps a BigInt value to an unsigned integer between `0` and \\(2^{width}-1\\).|
>>>>>>> 9223abf1b37fe361717e657f3948966a0521739b

## Instance methods

| methods | description |
| :-- | :-- |
|**`BigInt.toLocaleString()`**|Returns a string with a language-sensitive representation of this number. Overrides the [`Object.toLocaleString()`](/en/webfrontend/Object.toLocaleString) method.|
|**`BigInt.toString()`**|Returns a string representing the specified object in the specified radix (base). Overrides the [`Object.toString()`](/en/webfrontend/Object.toString) method.|
|**`BigInt.valueOf()`**| Returns the primitive value of the specified object. Overrides the [`Object.valueOf()`](/en/webfrontend/Object.valueOf) method.|

## Usage recommendations

### Coercion

<<<<<<< HEAD
Because coercing between [`Number`](/en/webfrontend/Number) and `BigInt` can lead to loss of precision,
it is recommended to only use `BigInt` when values greater than `2^^53^^` are reasonably expected
=======
Because coercing between [Number](/en/webfrontend/Number) and `BigInt` can lead to loss of precision,
it is recommended to only use `BigInt` when values greater than \((2^{53}\\) are reasonably expected
>>>>>>> 9223abf1b37fe361717e657f3948966a0521739b
and not to coerce between the two types.

### Cryptography

The operations supported on `BigInts` are not constant time.
`BigInt` is therefore unsuitable for use in cryptography.

### Use within JSON

<<<<<<< HEAD
Using [`JSON.stringify()`](/en/webfrontend/JSON.stringify) with any `BigInt` value will raise a `TypeError`
as `BigInt` values aren't serialized in [`JSON`]((/en/webfrontend/JSON)) by default.
=======
Using [`JSON.stringify()`](/en/glossary/JSON) with any `BigInt` value will raise a `TypeError`
as `BigInt` values aren't serialized in [[JSON]] by default.
>>>>>>> 9223abf1b37fe361717e657f3948966a0521739b
However, you can implement your own `toJSON` method if needed:

```JavaScript
BigInt.prototype.toJSON = function() { return this.toString(); }
```

Instead of throwing, `JSON.stringify` now produces a string like this:

```JavaScript
JSON.stringify(BigInt(1));
// '"1"'
```

## Examples

### Calculating Primes

```JavaScript
// Returns true if passed BigInt is a prime number
function isPrime(p) {
  for (let i = 2n; i * i <= p; i++) {
    if (p % i === 0n) return false;
  }
  return true;
}

// Takes a BigInt as an argument, returns nth prime number as BigInt
function nthPrime(nth) {
  let maybePrime = 2n;
  let prime = 0n;
  
  while (nth >= 0n) {
    if (isPrime(maybePrime)) {
      nth--;
      prime = maybePrime;
    }
    maybePrime++;
  }
  
  return prime;
}

nthPrime(20n)
// ↪ 73n
```
