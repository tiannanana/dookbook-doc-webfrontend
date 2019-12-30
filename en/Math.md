TOPICS: Math
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript `Math` object

**`Math`** is a built-in object that has properties and methods for mathematical constants
and functions. Not a function object.

`Math` works with the [`Number`](/en/webfrontend/Number) type. It doesn't work with [`BigInt`](/en/webfrontend/BigInt).

## Description

Unlike the other global objects, `Math` is not a constructor. All properties and methods of `Math`
are static. You refer to the constant pi as `Math.PI` and you call the sine function as `Math.sin(x)`,
where x is the method's argument. Constants are defined with the full precision of real numbers in JavaScript.

## Extending the `Math` object

As with most of the built-in objects in JavaScript, the `Math` object can be extended with custom
properties and methods. To extend the `Math` object, you cannot use prototype. Instead,
you directly extend `Math`:

```javascript
Math.propName = propValue;
Math.methodName = methodRef;
```

For instance, the following example adds a method to the `Math` object for calculating the greatest
common divisor of a list of arguments.

```javascript
/* Variadic function -- Returns the greatest common divisor of a list of arguments */
Math.gcd = function() {
  if (arguments.length == 2) {
    if (arguments[1] == 0)
      return arguments[0];
    else
      return Math.gcd(arguments[1], arguments[0] % arguments[1]);
  } else if (arguments.length > 2) {
    var result = Math.gcd(arguments[0], arguments[1]);
    for (var i = 2; i < arguments.length; i++)
      result = Math.gcd(result, arguments[i]);
    return result;
  }
};
```

Try it:

```javascript
console.log(Math.gcd(20, 30, 15, 70, 40)); // `5`
```

## Properties

### `Math.E`

The **`Math.E`** property represents the base of natural logarithms, e, approximately `2.718`.

$$
\mathtt{{Math.E}} = e \approx 2.718
$$

Because `E` is a static property of `Math`, you always use it as `Math.E`, rather than as a
property of a `Math` object you created (`Math` is not a constructor).

### `Math.LN10`

The **`Math.LN10`** property represents the natural logarithm of `10`, approximately `2.302`:

$$
\mathtt{{Math.LN10}} = \ln(10) \approx 2.302
$$

Because `LN10` is a static property of `Math`, you always use it as `Math.LN10`, rather than as a
property of a `Math` object you created (`Math` is not a constructor).

### `Math.LN2`

The **`Math.LN2`** property represents the natural logarithm of `2`, approximately `0.693`:

$$
\mathtt{{Math.LN2}} = \ln(2) \approx 0.693
$$

Because `LN2` is a static property of `Math`, you always use it as `Math.LN2`, rather than as a
property of a `Math` object you created (`Math` is not a constructor).

### `Math.LOG10E`

The **`Math.LOG10E`** property represents the base `10` logarithm of `e`, approximately `0.434`:

$$
\mathtt{{Math.LOG10E}} = \log_{10}(e) \approx 0.434
$$

Because `LOG10E` is a static property of `Math`, you always use it as `Math.LOG10E`, rather than as
a property of a `Math` object you created (`Math` is not a constructor).

### `Math.LOG2E`

The **`Math.LOG2E`** property represents the base 2 logarithm of `e`, approximately `1.442`:

$$
\mathtt{{Math.LOG2E}} = \log_2(e) \approx 1.442
$$

Because `LOG2E` is a static property of `Math`, you always use it as `Math.LOG2E`, rather than as a
property of a `Math` object you created (`Math` is not a constructor).

### `Math.PI`

The **`Math.PI`** property represents the ratio of the circumference of a circle to its diameter,
approximately 3.14159:

$$
\mathtt{{Math.PI}} = \pi \approx 3.14159
$$

Because `PI` is a static property of `Math`, you always use it as `Math.PI`, rather than as a
property of a `Math` object you created (`Math` is not a constructor).

### `Math.SQRT1_2`

The **`Math.SQRT1_2`** property represents the square root of `1/2` which is approximately `0.707`:

$$
\mathtt{{Math.SQRT1\_2}} = \frac{\sqrt{1}}{2} = \frac{1}{\sqrt{2}} \approx 0.707
$$

Because `SQRT1_2` is a static property of `Math`, you always use it as `Math.SQRT1_2`, rather than
as a property of a `Math` object you created (`Math` is not a constructor).

### `Math.SQRT2`

The **`Math.SQRT2`** property represents the square root of `2`, approximately `1.414`:

$$
\mathtt{{Math.SQRT2}} = \sqrt{2} \approx 1.414
$$

Because `SQRT2` is a static property of `Math`, you always use it as `Math.SQRT2`, rather than as a
property of a `Math` object you created (`Math` is not a constructor).

## Examples

### Using `Math.E`

The following function returns `e`:

```javascript
function getNapier() {
   return Math.E
}

getNapier() // 2.718281828459045
```

### Using `Math.LN10`

The following function returns the natural log of `10`:

```javascript
function getNatLog10() {
   return Math.LN10
}

getNatLog10() // 2.302585092994046
```

### Using `Math.LN2`

The following function returns the natural log of `2`:

```javascript
function getNatLog2() {
   return Math.LN2
}

getNatLog2() // 0.6931471805599453
```

### Using `Math.LOG10E`

The following function returns the base `10` logarithm of `e`:

```javascript
function getLog10e() {
   return Math.LOG10E
}

getLog10e() // 0.4342944819032518
```

### Using `Math.LOG2E`

The following function returns the base `2` logarithm of `e`:

```javascript
function getLog2e() {
   return Math.LOG2E
}

getLog2e() // 1.4426950408889634
```

### Using `Math.PI`

The following function uses `Math.PI` to calculate the circumference of a circle with a passed radius.

```javascript
function calculateCircumference (radius) {
  return 2 * Math.PI * radius;
}

calculateCircumference(1);  // 6.283185307179586
```

### Using `Math.SQRT1_2`

The following function returns `1` over the square root of `2`:

```javascript
function getRoot1_2() {
   return Math.SQRT1_2
}

getRoot1_2() // 0.7071067811865476
```

### Using `Math.SQRT2`

The following function returns the square root of `2`:

```javascript
function getRoot2() {
   return Math.SQRT2;
}

getRoot2(); // 1.4142135623730951
```
