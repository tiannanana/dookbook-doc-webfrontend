TOPICS: Date.now
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.now`

The `Date.now()` method returns the number of milliseconds elapsed since January `1`,
`1970 00:00:00 UTC`.

## Syntax

```javascript
var timeInMs = Date.now();
```

**parameter**: No parameters

## Description

Because `now()` is a static method of [`Date`](/en/webfrontend/Date), you always use it as `Date.now()`.

## Reduced time precision

To offer protection against timing attacks and fingerprinting, the precision of `Date.now()`
might get rounded depending on browser settings.

In Firefox, the `privacy.reduceTimerPrecision`  preference is enabled by default and defaults to
`20µs` in Firefox `59`; in `60` it will be `2ms`.

```javascript
// reduced time precision (2ms) in Firefox 60
Date.now()
// 1519211809934
// 1519211810362
// 1519211811670
// ...


// reduced time precision with `privacy.resistFingerprinting` enabled
Date.now();
// 1519129853500
// 1519129858900
// 1519129864400
// ...
```

In Firefox, you can also enable `privacy.resistFingerprinting`, the precision will be 100ms or the
value of `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`, whichever is larger.

## PolyfillSection

This method was standardized in ECMA-262 5^th^ edition. Engines which have not been updated to
support this method can work around the absence of this method using the following shim:

```javascript
if (!Date.now) {
  Date.now = function now() {
    return new Date().getTime();
  };
}
```
