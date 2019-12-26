TOPICS: Float64Array
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# JavaScript Float64Array Object

`Float64Array` 类型数组代表的是平台字节顺序为64位的浮点数型数组(对应于 C 浮点数据类型) 。
如果需要控制字节顺序， 使用 [`DataView`](/zh-hans/webfrontend/DataView) 替代。其内容初始化为`0`。
一旦建立起来，你可以使用这个对象的方法对其元素进行操作，或者使用标准数组索引语法 (使用方括号)。

## 语法

```JavaScript
new Float64Array(length);
new Float64Array(typedArray);
new Float64Array(object);
new Float64Array(buffer [, byteOffset [, length]]);
```

更多的语法信息和参数，参见 [`TypedArray`](/zh-hans/webfrontend/TypedArray)。

## 属性

| 属性 | 说明 |
| :-- | :-- |
|**[`Float64Array.BYTES_PER_ELEMENT`](/zh-hans/webfrontend/Float64Array.BYTES_PER_ELEMENT)**|返回元素字节数。 在 `Float64Array` 的情况下返回 `4`。|
|**`Float64Array.length`**|长度属性的值为 `3`。关于其实际长度(元素数量)，参见[`Float64Array.prototype.length`](/zh-hans/webfrontend/Float64Array.prototype.length)。|
|**[`Float64Array.name`](/zh-hans/webfrontend/Float64Array.name)**|返回构造函数名字的字符串值。在 `Float64Array` 类型的情况下为：`"Float64Array"`。|
|**[`Float64Array.prototype`](/zh-hans/webfrontend/Float64Array.prototype)**|[`TypedArray`](/zh-hans/webfrontend/TypedArray)对象的原型。|

## 方法

| 方法 | 说明 |
| :-- | :-- |
|**[`Float64Array.from()`](/zh-hans/webfrontend/Float64Array.from)**|从一个类数组对象或可遍历对象创建一个新的`Float64Array`。参见 [`Array.from()`](/zh-hans/webfrontend/Array.from)。|
|**[`Float64Array.of()`](/zh-hans/webfrontend/Float64Array.of)**|用可变数量的参数创建一个新的`Float64Array`。 参见 [`Array.of()`](/zh-hans/webfrontend/Array.from)。|

## Float64Array 原型

所有的`Float64Array`对象都继承自 [`TypedArray.prototype`](/zh-hans/webfrontend/TypedArray.prototype)。

### 原型属性

| 属性 | 说明 |
| :-- | :-- |
|**`Float64Array.prototype.constructor`**|返回创建这个实例原型的函数。 这是 `Float64Array` 默认的构造函数。|
|**[`Float64Array.prototype.buffer`](/zh-hans/webfrontend/TypedArray.prototype.buffer)** *(只读)*|返回这个`Float64Array`引用的[`ArrayBuffer`](/zh-hans/webfrontend/ArrayBuffer)。构造时已固定，所以是只读的。|
|**[`Float64Array.prototype.byteLength`](/zh-hans/webfrontend/TypedArray.prototype.byteLength)** *(只读)*|返回从`Float64Array`的[`ArrayBuffer`](/zh-hans/webfrontend/ArrayBuffer)开头开始的长度 (以字节为单位) 。构造时已固定，所以是只读的。|
|**[`Float64Array.prototype.byteOffset`](/zh-hans/webfrontend/TypedArray.prototype.byteOffset)** *(只读)*|返回从`Float64Array`的[`ArrayBuffer`](/zh-hans/webfrontend/ArrayBuffer)开头开始的偏移量 (以字节为单位) 。构造时已固定，所以是只读的。|
|**[`Float64Array.prototype.length`](/zh-hans/webfrontend/TypedArray.prototype.length)** *(只读)*|返回`Float64Array`中的元素个数。构造时已固定，所以是只读的。|

### 原型方法

| 方法 | 说明 |
| :-- | :-- |
|**[`Float64Array.prototype.copyWithin()`](/zh-hans/webfrontend/TypedArray.prototype.copyWithin)**|从数组复制元素。参见[`Array.prototype.copyWithin()`](/zh-hans/webfrontend/Array.prototype.copyWithin)。|
|**[`Float64Array.prototype.entries()`](/zh-hans/webfrontend/TypedArray.prototype.entries)**|返回一个包含数组中每个元素键值对的数组遍历器对象。参见[`Array.prototype.entries()`](/zh-hans/webfrontend/Array.prototype.entries)。|
|**[`Float64Array.prototype.every()`](/zh-hans/webfrontend/TypedArray.prototype.every)**|检测是否所有元素都能通过给定函数的测试。参见[`Array.prototype.every()`](/zh-hans/webfrontend/Array.prototype.every)。|
|**[`Float64Array.prototype.fill()`](/zh-hans/webfrontend/TypedArray.prototype.fill)**|用一个静态值填充给定的起始位置。 参见[`Array.prototype.fill()`](/zh-hans/webfrontend/Array.prototype.fill)。|
|**[`Float64Array.prototype.filter()`](/zh-hans/webfrontend/TypedArray.prototype.filter)**|创建一个新数组，数据为原数组中所有能让给入函数返回`true`的元素。参见[`Array.prototype.filter()`](/zh-hans/webfrontend/Array.prototype.filter)。|
|**[`Float64Array.prototype.find()`](/zh-hans/webfrontend/TypedArray.prototype.find)**|返回满足测试函数的值，如果没有找到，返回`undefined`。 参见[`Array.prototype.find()`](/zh-hans/webfrontend/Array.prototype.find)。|
|**[`Float64Array.prototype.findIndex()`](/zh-hans/webfrontend/TypedArray.prototype.findIndex)**|返回满足测试函数的值的位置，如果没有找到，返回`-1`。参见[`Array.prototype.findIndex()`](/zh-hans/webfrontend/Array.prototype.findIndex)。|
|**[`Float64Array.prototype.forEach()`](/zh-hans/webfrontend/TypedArray.prototype.forEach)**|以每个元素为参数各调用一次函数。参见[`Array.prototype.forEach()`](/zh-hans/webfrontend/Float64Array.prototype.forEach)。|
|**[`Float64Array.prototype.includes()`](/zh-hans/webfrontend/TypedArray.prototype.includes)**|判断是否包含某个元素，返回 `true` 或 `false`。参见[`Array.prototype.includes()`](/zh-hans/webfrontend/Array.prototype.includes)。*(这是一个实验性的API,请不要在生产环境中使用它)*|
|**[`Float64Array.prototype.indexOf()`](/zh-hans/webfrontend/TypedArray.prototype.indexOf)**|返回数组中等于给定值的元素的第一个（最小）位置， 没有找到则返回`-1`。参见[`Array.prototype.indexOf()`](/zh-hans/webfrontend/Array.prototype.indexOf)。|
|**[`Float64Array.prototype.join()`](/zh-hans/webfrontend/TypedArray.prototype.join)**|合并所有数组元素到一个字符串中。 参见[`Array.prototype.join()`](/zh-hans/webfrontend/Array.prototype.join)。|
|**[`Float64Array.prototype.keys()`](/zh-hans/webfrontend/TypedArray.prototype.keys)**|返回一个包含数组中所有索引的数组遍历器。 参见[`Array.prototype.keys()`](/zh-hans/webfrontend/Array.prototype.keys)。|
|**[`Float64Array.prototype.lastIndexOf()`](/zh-hans/webfrontend/TypedArray.prototype.lastIndexOf)**|返回数组中等于给定值的元素的最后（最大）位置， 没有找到则返回`-1`。参见[`Array.prototype.lastIndexOf()`](/zh-hans/webfrontend/Array.prototype.lastIndexOf)。|
|**[`Float64Array.prototype.map()`](/zh-hans/webfrontend/TypedArray.prototype.map)**|创建一个新的数组，数据由原数组每个元素依次传入给定函数后返回的值组成。参见[`Array.prototype.map()`](/zh-hans/webfrontend/TypedArray.prototype.map)。|
|**[`Float64Array.prototype.move()`](/zh-hans/webfrontend/TypedArray.prototype.move)**| 未实现 |
|**[`Float64Array.prototype.reduce()`](/zh-hans/webfrontend/TypedArray.prototype.reduce)**|传入一个函数作为累加器，从左到右遍历，最终得到一个值。 参见[`Array.prototype.reduce()`](/zh-hans/webfrontend/Array.prototype.reduce)。|
|**[`Float64Array.prototype.reduceRight()`](/zh-hans/webfrontend/TypedArray.prototype.reduceRight)**|传入一个函数作为累加器，从右到左遍历，最终得到一个值。参见[`Array.prototype.reduceRight()`](/zh-hans/webfrontend/Array.prototype.reduceRight)。|
|**[`Float64Array.prototype.reverse()`](/zh-hans/webfrontend/TypedArray.prototype.reverse)**|反转数组元素的顺序 — 第一个变为最后一个， 最后一个变为第一个。参见 [`Array.prototype.reverse()`](/zh-hans/webfrontend/Array.prototype.reverse)。|
|**[`Float64Array.prototype.set()`](/zh-hans/webfrontend/TypedArray.prototype.set)**|从给定的数组存入多个数值。|
|**[`Float64Array.prototype.slice()`](/zh-hans/webfrontend/TypedArray.prototype.slice)**|提取数组的一部分并且返回一个新数组。参见[`Array.prototype.slice()`](/zh-hans/webfrontend/Array.prototype.slice)。|
|**[`Float64Array.prototype.some()`](/zh-hans/webfrontend/TypedArray.prototype.some)**|如果数组中至少有一个元素满足测试函数的要求则返回`true`。参见[`Array.prototype.some()`](/zh-hans/webfrontend/Array.prototype.some)。|
|**[`Float64Array.prototype.sort()`](/zh-hans/webfrontend/TypedArray.prototype.sort)**|对数组元素进行排序并返回数组。参见[`Array.prototype.sort()`](/zh-hans/webfrontend/Array.prototype.sort)。|
|**[`Float64Array.prototype.subarray()`](/zh-hans/webfrontend/TypedArray.prototype.subarray)**|从给定的起始位置返回一个新的`Float64Array`。|
|**[`Float64Array.prototype.values()`](/zh-hans/webfrontend/TypedArray.prototype.values)**|返回一个包含所有数组元素的数组遍历器对象。 参见[`Array.prototype.values()`](/zh-hans/webfrontend/Array.prototype.values)。|
|**[`Float64Array.prototype.toLocaleString()`](/zh-hans/webfrontend/TypedArray.prototype.toLocaleString)**|返回一个代表数组和其元素的本地化格式字符串。参见[`Array.prototype.toLocaleString()`](/zh-hans/webfrontend/Array.prototype.toLocaleString)。|
|**[`Float64Array.prototype.toString()`](/zh-hans/webfrontend/TypedArray.prototype.toString)**|返回一个代表数组和它的元素的字符串。参见[`Array.prototype.toString()`](/zh-hans/webfrontend/Array.prototype.toString)。|
|**[`Float64Array.prototype[@@iterator]()`](/zh-hans/webfrontend/TypedArray.prototype[@@iterator])**|返回一个新的包含数组元素的数组迭代器对象。|

## 示例

```JavaScript
// From a length
var float64 = new Float64Array(2);
float64[0] = 42;
console.log(float64[0]); // 42
console.log(float64.length); // 2
console.log(float64.BYTES_PER_ELEMENT); // 8

// From an array
var arr = new Float64Array([21,31]);
console.log(arr[1]); // 31

// From another TypedArray
var x = new Float64Array([21, 31]);
var y = new Float64Array(x);
console.log(y[0]); // 21

// From an ArrayBuffer
var buffer = new ArrayBuffer(32);
var z = new Float64Array(buffer, 0, 4);
```
