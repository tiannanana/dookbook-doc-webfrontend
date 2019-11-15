TOPICS: <html>
        <html> lang attribute
        <html> Accessibility Concerns
        <head>
        HTML head element
        HTML head tag
        HTML5 Bone

# 根元素: `<html>`

**HTML`<html>`元素**表示一个[[HTML]]文档的根（顶级元素），所以它也被称为**根元素**。所有其他元素必须是此元素的后代(子元素)。

## `<html>` 元数据

|  |  |
| :-- | :-- |
| **内容类别** | 无 |
| **允许内容** | 一个`<head>`元素，后跟一个[`<body>`](/zh-hans/webfrontend/<body>/)元素。|
| **允许的父元素** | 作为文档的根元素，或是在复合文档中任意允许的子文档片段。|
| **DOM接口** | `HTMLHtmlElement` |

## HTML5骨架

```html
<!DOCTYPE html>
<html lang="zh-Hans">
<head>
  <meta charset="utf-8">
  <title>网页标题</title>
</head>
<body>
  网页内容
</body>
</html>
```

## `<html>`属性

| 属性 | 描述 |
| --- | --- |
| `xmlns` | 指派文档的 XML 命名空间。默认的值是`"http://www.w3.org/1999/xhtml"`。这在 XHTML 中是必要的，而在 HTML 中则是可选的。 |

## `<html>`可访问性

在`html`元素上提供具有有效IETF标识语言标记的`lang`属性，将有助于屏幕阅读技术确定要陈述的正确语言。标识语言标签应描述页面大部分内容使用的语言。
没有它，屏幕阅读器通常会默认使用操作系统的设置语言，这可能会导致错误陈述。

## `<head>`

**HTML`<head>` 元素**规定文档相关的配置信息（**元数据**），包括文档的*标题*、*作者*、*描述*、以及引用的*文档样式（CSS）*和*脚本（JavaScript）*等。

### `<head>` 元数据

|  |  |
| :-- | :-- |
| **内容类别** | 无 |
| **允许内容** | 至少包含一个[`<title>`](/zh-hans/webfrontend/<title>/)元素来指定文档的标题信息，除非标题已经从更高等级协议中指定（`<iframe>` ）。|
| **允许父元素** | `<html>`元素，并作为其第一个子元素 |
| **DOM接口** | `HTMLHeadElement` |
