TOPICS: Date.toISOString
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# `Date.toISOString()`

**`toISOString()`** 方法返回一个 ISO（ISO 8601 Extended Format）格式的字符串：**YYYY-MM-DDTHH:mm:ss.sssZ**。时区总是UTC（协调世界时），加一个后缀“**Z**”标识。

## 语法

```javascript
dateObj.toISOString()
```

**参数**: 没有参数

**返回值**: String

## 示例

```javascript
var today = new Date("05 October 2011 14:48 UTC");
alert(today.toISOString()); // 返回2011-10-05T14:48:00.000Z
```

上例使用了非标准字符串的解析，该字符串在某些旧的浏览器（如IE）中可能无法被正确解析。

## Polyfill

该方法在ECMA-262第5版中被标准化。对于那些不支持此方法的JS引擎可以通过加上下面的代码实现：

```javascript
if ( !Date.prototype.toISOString ) {
  ( function() {

    function pad(number) {
      if ( number < 10 ) {
        return '0' + number;
      }
      return number;
    }

    Date.prototype.toISOString = function() {
      return this.getUTCFullYear() +
        '-' + pad( this.getUTCMonth() + 1 ) +
        '-' + pad( this.getUTCDate() ) +
        'T' + pad( this.getUTCHours() ) +
        ':' + pad( this.getUTCMinutes() ) +
        ':' + pad( this.getUTCSeconds() ) +
        '.' + (this.getUTCMilliseconds() / 1000).toFixed(3).slice(2, 5) +
        'Z';
    };
  
  }() );
}
```
