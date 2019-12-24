TOPICS: Math
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Math 对象: `Math`

**`Math`** 是一个**内置对象**，它具有*数学常数*和*函数*的属性和方法。不是一个**函数对象**。

`Math` 适用于 [`Number`](/zh-hans/webfrontend/Number) 类型。它不支持 [`BigInt`](/zh-hans/webfrontend/BigInt)。

## 描述

与其他*全局对象*不同的是，`Math` 不是一个构造器。 `Math` 的所有属性与方法都是静态的。引用圆周率的写法是 `Math.PI`，调用正余弦函数的写法是 `Math.sin(x)`，`x`
是要传入的参数。`Math` 的常量是使用 JavaScript 中的全精度浮点数来定义的。

## 拓展 `Math` 对象

与JavaScript中的大多数内置对象一样，可以使用自定义属性和方法扩展`Math`对象。要扩展`Math`对象，请不要使用原型。相反，您直接扩展数学：

```javascript
Math.propName = propValue;
Math.methodName = methodRef;
```

例如，下面的示例将一个方法添加到`Math`对象中，用于计算参数列表的最大公约数。

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

试试运行下面的代码：

```javascript
console.log(Math.gcd(20, 30, 15, 70, 40)); // `5`
```

## 属性

### `Math.E`

**`Math.E`** 属性表示自然对数的底数（或称为基数），`e`，约等于 `2.718`。

$$
\mathtt{{Math.E}} = e \approx 2.718
$$

由于 `E` 是 `Math` 对象的静态属性，所以应该像这样使用：`Math.E`，而不是作为你创建的 `Math` 实例对象的属性（`Math` 不是构造函数）。

### `Math.LN10`

**`Math.LN10`** 属性表示 `10` 的自然对数，约为 `2.302`：

$$
\mathtt{{Math.LN10}} = \ln(10) \approx 2.302
$$

由于 `LN10` 是 `Math` 的静态属性，所以应该像这样使用：`Math.LN10`，而不是作为你创建的 `Math` 实例的属性（`Math` 不是构造函数）。

### `Math.LN2`

**`Math.LN2`** 属性表示 `2` 的自然对数，约为 `0.69`3：

$$
\mathtt{{Math.LN2}} = \ln(2) \approx 0.693
$$

由于 `LN2` 是 `Math` 的静态属性，所以应该像这样使用：`Math.LN2`，而不是作为你创建的 `Math` 实例的属性（`Math` 不是构造函数）。

### `Math.LOG10E`

**`Math.LOG10E`** 属性表示以 `10` 为底数，`e` 的对数，约为 `0.434`：

$$
\mathtt{{Math.LOG10E}} = \log_{10}(e) \approx 0.434
$$

由于 `LOG10E` 是 `Math` 的静态属性，所以应该像这样使用：`Math.LOG10E`，而不是作为你创建的 `Math` 实例的属性（`Math` 不是一个构造函数）。

### `Math.LOG2E`

**`Math.LOG2E`** 属性表示以 `2` 为底数，`e` 的对数，约为 `1.442`：

$$
\mathtt{{Math.LOG2E}} = \log_2(e) \approx 1.442
$$

由于 `LOG2E` 是 `Math` 的静态属性，所以应该像这样使用：`Math.LOG2E`，而不是作为你创建的 `Math` 对象的属性（`Math` 不是一个构造函数）。

### `Math.PI`

**`Math.PI`** 表示一个圆的周长与直径的比例，约为 `3.14159`：

$$
\mathtt{{Math.PI}} = \pi \approx 3.14159
$$

由于 `PI` 是 `Math` 的静态属性，所以应该像这样使用：`Math.PI`，而不是作为你创建的 `Math` 实例的属性（`Math` 不是构造函数）。

### `Math.SQRT1_2`

**`Math.SQRT1_2`** 属性表示 `1/2` 的平方根，约为 `0.707`：

$$
\mathtt{{Math.SQRT1\_2}} = \frac{\sqrt{1}}{2} = \frac{1}{\sqrt{2}} \approx 0.707
$$

由于 `SQRT1_2` 是 `Math` 对象的静态属性，所以应该像这样使用：`Math.SQRT1_2`，而不是作为你创建的 `Math` 实例的属性（`Math` 不是构造函数）。

### `Math.SQRT2`

**`Math.SQRT2`** 属性表示 `2` 的平方根，约为 `1.414`：

$$
\mathtt{{Math.SQRT2}} = \sqrt{2} \approx 1.414
$$

由于 `SQRT2` 是 `Math` 的静态属性，所以应该像这样使用：`Math.SQRT2`，而不是作为你创建的 `Math` 实例的属性（`Math` 不是构造函数）

## 示例

### 使用 `Math.E`

下面的函数返回 `e`：

```javascript
function getNapier() {
   return Math.E
}

getNapier() // 2.718281828459045
```

### 使用 `Math.LN10`

下面的函数返回 `10` 的自然对数：

```javascript
function getNatLog10() {
   return Math.LN10
}

getNatLog10() // 2.302585092994046
```

### 使用 `Math.LN2`

下面的函数返回 `2` 的自然对数：

```javascript
function getNatLog2() {
   return Math.LN2
}

getNatLog2() // 0.6931471805599453
```

### 使用 `Math.LOG10E`

下面的函数返回以 `10` 为底数，E的对数：

```javascript
function getLog10e() {
   return Math.LOG10E
}

getLog10e() // 0.4342944819032518
```

### 使用 `Math.LOG2E`

下面的函数返回以 `2` 为底数，`E` 的对数：

```javascript
function getLog2e() {
   return Math.LOG2E
}

getLog2e() // 1.4426950408889634
```

### 使用 `Math.PI`

下面的函数使用 `Math.PI` 计算给定半径的圆周长：

```javascript
function calculateCircumference (radius) {
  return 2 * Math.PI * radius;
}

calculateCircumference(1);  // 6.283185307179586
```

### 使用 `Math.SQRT1_2`

下面的函数返回 `1/2` 的平方根：

```javascript
function getRoot1_2() {
   return Math.SQRT1_2
}

getRoot1_2() // 0.7071067811865476
```

### 使用 `Math.SQRT2`

下面的函数返回 2 的平方根：

```javascript
function getRoot2() {
   return Math.SQRT2;
}

getRoot2(); // 1.4142135623730951
```
