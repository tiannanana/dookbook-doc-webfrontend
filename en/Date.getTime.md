TOPICS: Date.getTime
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.getTime()`

The **`getTime()`** method returns the number of milliseconds since the Unix Epoch.

JavaScript uses milliseconds as the unit of measurement, whereas Unix Time is in seconds.

`getTime()` always uses UTC for time representation. For example, a client browser in one timezone,
`getTime()` will be the same as a client browser in any other timezone.

You can use this method to help assign a date and time to another [`Date`](/en/webfrontend/Date)
object. This method is functionally equivalent to the [`valueOf()`](/en/webfrontend/Date.valueOf) method.

## Syntax

```javascript
dateObj.getTime()
```

**parameter**: No parameters

**Return value**: A number representing the milliseconds elapsed between `1` January
`1970 00:00:00 UTC` and the given date.

## Examples

### Using `getTime()` for copying dates

Constructing a `date` object with the identical time value.

```javascript
// Since month is zero based, birthday will be January 10, 1995
var birthday = new Date(1994, 12, 10);
var copy = new Date();
copy.setTime(birthday.getTime());
```

### Measuring execution time

Subtracting two subsequent `getTime()` calls on newly generated [`Date`](/en/webfrontend/Date)
objects, give the time span between these two calls. This can be used to calculate the executing
time of some operations. See also [`Date.now()`](/en/webfrontend/Date.now) to prevent instantiating
unnecessary [`Date`](/en/webfrontend/Date) objects.

```javascript
var end, start;

start = new Date();
for (var i = 0; i < 1000; i++) {
  Math.sqrt(i);
}
end = new Date();

console.log('Operation took ' + (end.getTime() - start.getTime()) + ' msec');
```

## Reduced time precision

To offer protection against timing attacks and fingerprinting, the precision of `new Date().getTime()`
might get rounded depending on browser settings. In Firefox, the `privacy.reduceTimerPrecision`
preference is enabled by default and defaults to `20µs` in Firefox 59; in `60` it will be `2ms`.

```javascript
// reduced time precision (2ms) in Firefox 60
new Date().getTime();
// 1519211809934
// 1519211810362
// 1519211811670
// ...


// reduced time precision with `privacy.resistFingerprinting` enabled
new Date().getTime();
// 1519129853500
// 1519129858900
// 1519129864400
// ...
```

In Firefox, you can also enable `privacy.resistFingerprinting`, the precision will be 100ms or
the value of `privacy.resistFingerprinting.reduceTimerPrecision.microseconds`, whichever is larger.
