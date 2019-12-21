TOPICS: EvalError
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript EvalError Object

The `EvalError` object indicates an error regarding the global [`eval()`](/en/webfrontend/eval) function.
This exception is not thrown by JavaScript anymore, however the `EvalError` object remains for compatibility.

## Syntax

```JavaScript
new EvalError([message[, fileName[, lineNumber]]])
```

### Parameters

| Parameters | Description |
| :-- | :-- |
|**`message`***(Optional)*|Human-readable description of the [`Error`](/en/webfronted/EvalError).|
|**`fileName`***(Optional)*| The name of the file containing the code that caused the exception.*(This API has not been standardized.)*|
|**`lineNumber`***(Optional)*| The line number of the code that caused the exception.*(This API has not been standardized.)*|

## Properties

| Properties | Description |
| :-- | :-- |
|**[`EvalError.prototype`](/en/webfrontend/EvalError.prototype)**|Allows the addition of properties to an `EvalError` object.|

## Methods

The global `EvalError` contains no methods of its own, however,
it does inherit some methods through the prototype chain.

## EvalError instances

### Instances Properties

| Properties | Description |
| :-- | :-- |
|**[`EvalError.prototype.constructor`](/en/webfrontend/EvalError.prototype)**|Specifies the function that created an instance's prototype.|
|**[`EvalError.prototype.message`](/en/webfrontend/EvalError.prototype)**|Error message. Although ECMA-262 specifies that [`EvalError`](ens/webfrontend/EvalError) should provide its own `message` property, in [SpiderMonkey](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/SpiderMonkey), it inherits [`Error.prototype.message`](/en/webfrontend/Error.prototype.message).|
|**[`EvalError.prototype.name`](/en/webfrontend/EvalError.prototype)**|Error name. Inherited from Error`](/en/webfronted/EvalError).|
|**[`EvalError.prototype.fileName`](/en/webfrontend/EvalError.prototype)**|Path to file that raised this Error. Inherited from [`Error`](/en/webfronted/EvalError).|
|**[`EvalError.prototype.lineNumber`](/en/webfrontend/EvalError.prototype)**|Line number in file that raised this Error. Inherited from [`Error`](/en/webfronted/EvalError).|
|**[`EvalError.prototype.columnNumber`](/en/webfrontend/EvalError.prototype)**|Column number in line that raised this Error. Inherited from [`Error`](/en/webfronted/EvalError).|
|**[`EvalError.prototype.stack`](/en/webfrontend/EvalError.prototype)**|Stack trace. Inherited from [`Error`](/en/webfronted/EvalError).|

### Instances Methods

Although the `EvalError` prototype object does not contain any methods of its own,
`EvalError` instances do inherit some methods through the prototype chain.

## Examples

`EvalError` is not used in the current ECMAScript specification and will thus not be thrown by the runtime.
However, the object itself remains for backwards compatibility with earlier versions of the specification.

### Creating an EvalError

```JavaScript
try {
  throw new EvalError('Hello', 'someFile.js', 10);
} catch (e) {
  console.log(e instanceof EvalError); // true
  console.log(e.message);              // "Hello"
  console.log(e.name);                 // "EvalError"
  console.log(e.fileName);             // "someFile.js"
  console.log(e.lineNumber);           // 10
  console.log(e.columnNumber);         // 0
  console.log(e.stack);                // "@Scratchpad/2:2:9\n"
}
```
