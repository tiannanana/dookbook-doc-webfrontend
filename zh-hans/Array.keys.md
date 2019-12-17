TOPICS: Array.keys
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

## `Array.keys()`

`keys()` 方法返回一个包含数组中每个索引键的 **`Array Iterator`** 对象。

## 语法

```javascript
arr.keys()
```

**参数**: 没有参数

**返回类型**: 一个新的 [`Array`](/zh-hans/webfrontend/Array) 迭代器对象。

## 示例

### 索引迭代器会包含那些没有对应元素的索引

```javascript
var arr = ["a", , "c"];
var sparseKeys = Object.keys(arr);
var denseKeys = [...arr.keys()];
console.log(sparseKeys); // ['0', '2']
console.log(denseKeys);  // [0, 1, 2]
```
