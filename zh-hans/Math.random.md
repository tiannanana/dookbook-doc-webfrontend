TOPICS: Math.random
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Math.random()`

`Math.random()` 函数返回一个浮点,  伪随机数在范围 **`[0，1)`** ，也就是说，从`0`（包括`0`）往上，但是不包括`1`（排除`1`），然后您可以缩放到所需的范围。实现将初始种子选择到随机数生成算法;它不能被用户选择或重置。

!!! warn ""
    `[0，1) ===` [即从`0`（包含`0`）到`...1`但不包括`1`（排除1）。
    `[0，1) ===` 左闭右开区间

!!! warn ""
    `Math.random()` 不能提供像密码一样安全的随机数字
    不能使用它们来处理有关安全的事情。使用Web Crypto API 来代替, 和更精确的`window.crypto.getRandomValues(`) 方法.

## 语法

```javascript
Math.random()
```

**参数**: 没有参数

**返回值**: 一个浮点型伪随机数字，在`0`（包括`0`）和`1`（不包括）之间。

## 示例

请注意，由于JavaScript中的数字是IEEE 754浮点数，具有从近似到最接近的行为，因此以下函数所声明的范围（不包括 `Math.random()`本身的范围）不准确。
如果选择了极大的界限（2^^53^^或更高），则在极少数情况下可以计算通常排除的上限。 （注：舍入至最近平均采用最近舍入的去偶数舍入的方式，对.5的舍入上，采用取偶数的方式）

请注意，由于JavaScript中的数字是IEEE 754浮点数字，具有最近舍入（round-to-nearest-even）的行为，因此以下函数的范围（不包括`Math.random()`本身）并不准确。如果选择了非常大的边界（2^^53^^或更高），在极少数的情况下会计算通常-排除（通常除外）的上界。

IEEE 754标准的最小模式是最近舍入（舍入为最接近的偶数），它与四舍五入不同的是，对.5的舍入上采用取偶数的方式，即舍入为最接近的偶数，如：

四舍五入到最接近的偶数：`Round(0.5)=0;`回合`(1.5)=2;`圆角`(2.5)=2;`圆角`(3.5)=4;`

即：“四舍六入五取偶”

“五取偶”的规则：当小数部分恰为0.5时，若个位是奇数则入，若个位是偶数则舍，总之让个位变成偶数。

### 得到一个大于等于0，小于1之间的随机数

```javascript
function getRandom() {
  return Math.random();
}
```

### 得到一个两数之间的随机数

这个例子返回了一个在指定值之间的随机数。这个值不小于 `min`（有可能等于），并且小于（不等于）`max`。

```javascript
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
```

### 得到一个两数之间的随机整数

这个例子返回了一个在指定值之间的随机整数。这个值不小于 `min` （如果 `min` 不是整数，则不小于 `min` 的向上取整数），且小于（不等于）`max`。

```javascript
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; //不含最大值，含最小值
}
```

!!! warn ""
    也许很容易想到用 `Math.round()` 来实现，但是这会导致你的随机数处于一个不均匀的分布，这可能不符合你的需求。

### 得到一个两数之间的随机整数，包括两个数在内

上一个例子提到的函数 `getRandomInt()` 结果范围包含了最小值，但不含最大值。如果你的随机结果需要同时包含最小值和最大值，怎么办呢? `getRandomIntInclusive()` 函数可以实现。

```javascript
function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1)) + min; //含最大值，含最小值
}
```
