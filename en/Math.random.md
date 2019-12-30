TOPICS: Math.random
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.random()`

The **`Math.random()`** function returns a floating-point, pseudo-random number in the range `0`–`1`
(inclusive of `0`, but not `1`) with approximately uniform distribution over that range — which
you can then scale to your desired range. The implementation selects the initial seed to the
random number generation algorithm; it cannot be chosen or reset by the user.

!!! warn ""
    `Math.random()` does not provide cryptographically secure random numbers. Do not use them for
    anything related to security. Use the Web Crypto API instead, and more precisely the
    `window.crypto.getRandomValues()` method.

## Syntax

```javascript
Math.random()
```

**parameter**: No parameters

**Return value**: A floating-point, pseudo-random number between `0` (inclusive) and `1` (exclusive).

## Examples

Note that as numbers in JavaScript are IEEE 754 floating point numbers with round-to-nearest-even
behavior, the ranges claimed for the functions below (excluding the one for `Math.random()` itself)
aren't exact. If extremely large bounds are chosen (2^^53^^ or higher), it's possible in extremely rare
cases to calculate the usually-excluded upper bound.

### Getting a random number between 0 (inclusive) and 1 (exclusive)

```javascript
function getRandom() {
  return Math.random();
}
```

### Getting a random number between two values

This example returns a random number between the specified values. The returned value is no lower
than (and may possibly equal) `min`, and is less than (and not equal) `max`.

```javascript
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
```

### Getting a random integer between two values

This example returns a random integer between the specified values. The value is no lower than
`min` (or the next integer greater than min if `min` isn't an integer), and is less than
(but not equal to) `max`.

```javascript
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; //The maximum is exclusive and the minimum is inclusive
}
```

!!! warn ""
    It might be tempting to use `Math.round()` to accomplish that, but doing so would cause your random
    numbers to follow a non-uniform distribution, which may not be acceptable for your needs.

### Getting a random integer between two values, inclusive

While the `getRandomInt()` function above is inclusive at the `minimum`, it's exclusive at the maximum.
What if you need the results to be inclusive at both the `minimum` and the maximum? The
`getRandomIntInclusive()` function below accomplishes that.

```javascript
function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min; //The maximum is inclusive and the minimum is inclusive
}
```
