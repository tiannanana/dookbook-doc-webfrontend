TOPICS: String.concat
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `String.concat()`

**`concat()`** 方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。

## 语法

```javascript
str.concat(string2, string3[, ..., stringN])
```

| 参数 | 说明 |
| :-- | :-- |
| `string2...stringN` | 和原字符串连接的多个字符串 |

**返回值**: String

## 描述

`concat` 方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。`concat` 方法并不影响原字符串。。

## 示例

### 使用 `concat`

下面的例子演示如何将多个字符串与原字符串合并为一个新字符串

```javascript
var hello = "Hello, ";
console.log(hello.concat("Kevin", " have a nice day.")); /* Hello, Kevin have a nice day. */
```

## 性能

强烈建议使用 赋值操作符（`+`, `+=`）代替 `concat` 方法。参看 性能测试（perfomance test）。
