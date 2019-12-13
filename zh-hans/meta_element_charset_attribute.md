TOPICS: <meta> charset attribute

# `<meta>`元素的`charset`属性

此属性声明页面的 **[字符编码](/zh-hans/glossary/Character_Set)**。它必须包含用于字符编码的标准[[IANA]] [[MIME]]名称。尽管该标准不要求特定的编码，但建议：

- **鼓励**使用**`UTF-8`**。
- **不应使用**不兼容ASCII的编码来避免安全风险：不支持它们的浏览器可能会将有害内容解释为HTML。
  与ASCII不兼容的`JIS_C6226-1983`，`JIS_X0212-1990`，`HZ-GB-2312`，`JOHAB`，`ISO-2022`系列和`EBCDIC`系列会发生这种情况。
- **不得使用**`CESU-8`，`UTF-7`，`BOCU-1`和或`SCSU`编码，会导致*跨站点脚本攻击*(*cross-site scripting attacks*)。
- **不应该**使用`UTF-32`，因为并非所有HTML5编码算法都能将其与`UTF-16`区别开。
- 声明的字符编码必须与保存页面时使用的字符编码相匹配，以避免出现乱码和安全漏洞。
  声明编码的[`<meta>`](/zh-hans/webfrontend/<meta>)元素必须位于[`<head>`](/zh-hans/webfrontend/<head>)元素之内并且**在HTML的前1024个字节之内**，
  因为某些浏览器在选择编码之前仅查看这些字节。[`<meta>`](/zh-hans/webfrontend/<meta>)元素只是确定页面字符集的算法的一部分。HTTP头部`Content-Type`和所有字节顺序标记都将覆盖此元素。

**强烈建议定义字符编码**。如果页面的编码未定义，则可以使用跨脚本技术，例如`UTF-7`后备交叉脚本技术。

## 示例

```html
<head>
  <meta charset="utf-8">

  <!-- 以下字符集声明，已经在HTML5中废弃。用charset属性代替。 -->
  <meta http-equiv="Content-Type" content="text/html"; charset="IANAcharset">
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">

  <!-- 其他元数据声明 ... -->
</head>
```
