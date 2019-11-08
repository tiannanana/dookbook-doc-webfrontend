TOPICS: <html>
        HTML html element
        HTML root element
        HTML html tag
        <head>
        HTML head element
        HTML head tag

# 根元素

**HTML元素 `<html>`**表示一个[[HTML]]文档的根（顶级元素），所以它也被称为**根元素**。所有其他元素必须是此元素的后代(子元素)。

## `<html>` 元数据

|  |  |
| :-- | :-- |
| **内容类别** | 无 |
| **允许内容** | 一个 `<head>` 元素，后跟一个 `<body>` 元素。|
| **允许的父元素** | 作为文档的根元素，或是在复合文档中任意允许的子文档片段。|
| **DOM接口** | `HTMLHtmlElement` |

## `<head>`

**HTML `head` 元素** 规定文档相关的配置信息（元数据），包括文档的标题，引用的文档样式和脚本等。

### `<head>` 元数据

|  |  |
| :-- | :-- |
| **内容类别** | 无 |
| **允许内容** | 至少包含一个`<title>` 元素来指定文档的标题信息，除非标题已经从更高等级协议中指定（`<iframe>` ）。|
| **允许父元素** | `<html>`元素，并作为其第一个子元素 |
| **DOM接口** | `HTMLHeadElement` |

## 属性

元素包含 全局属性。

| 属性 | 描述 |
| --- | --- |
| `xmlns` | 指派文档的 XML 命名空间。默认的值是`"http://www.w3.org/1999/xhtml"`。这在 XHTML 中是必要的，而在 HTML 中则是可选的。 |

## `<title>`

**HTML `<title>` 元素** 定义文档的标题，显示在浏览器的标题栏或标签页上。它只可以包含文本，若是包含有标签，则包含的任何标签都不会被解释。

|  |  |
| -- | -- |
| 内容分类 | 元数据内容。|
| 允许内容 | 非空字符或特殊字符（inter-element whitespace）的文本 |
| 标签遗漏 | 同时需要开标签和闭标签。注意：遗漏 `</title>` 标签会导致浏览器忽略掉页面的剩余部分。|
| 允许的父标签 | 一个 `<head>` 元素只能包含一个 `<title>` 元素 |
| DOM 接口 | HTMLTitleElement |

## `<body>`

**HTML `body` 元素**表示文档的内容。document.body 属性提供了可以轻松访问文档的 body 元素的脚本。

|  |  |
| -- | -- |
| 内容分类 | Sectioning root |
| 允许的内容 | Flow content |
| Tag omission | The start tag may be omitted if the first thing inside it is not a space character, comment, `<script>` element or `<style>` element. The end tag may be omitted if the `<body>` element has contents or has a start tag, and is not immediately followed by a comment |
| 允许的父元素 | 它必须是 html 元素的直接子元素 |
| Permitted ARIA roles | None |
| DOM 接口 | HTMLBodyElement<br>body 元素接口 HTMLBodyElement.<br>你可以通过 document.body 属性访问 body 元素。|

| 属性 | 描述 |
| --- | --- |
| `onafterprint` | 用户完成文档打印之后调用的函数。 |
| `onbeforeprint` | 用户要求打印文档之前调用的函数。 |
| `onbeforeunload` | 文档即将被关闭之前调用的函数。 |
| `onblur` | 文档失去焦点时调用的函数。 |
| `onerror` | 文档加载失败时调用的函数。 |
| `onfocus` | 文档获得焦点时调用的函数。 |
| `onhashchange` | 文档当前地址的片段标识部分（以('#')开始的部分）发生改变时调用的函数。 |
| `onlanguagechange` | 用户选择的语言发生改变时调用的函数。 |
| `onload` | 文档完成加载时调用的函数。 |
| `onmessage` | 文档接收到消息时调用的函数。 |
| `onoffline` | 网络连接失败时调用的函数。 |
| `ononline` | 网络连接恢复时调用的函数。 |
| `onpopstate` | 用户回退历史记录时调用的函数。 |
| `onredo` | 用户重做操作时调用的函数。 |
| `onresize` | 文档尺寸发生改变时调用的函数。 |
| `onstorage` | 存储内容（`localStorage` / `sessionStorage`）发生改变时调用的函数。 |
| `onundo` | 用户撤销操作时调用的函数。 |
| `onunload` | 文档关闭时调用的函数。 |

## 示例

```html
<!DOCTYPE html>
<html lang="zh">
  <head>
    <title>Document title</title>
  </head>
  <body>
    <p>This is a paragraph</p>
  </body>
</html>
```

## 可访问性

在`html`元素上提供具有有效IETF标识语言标记的`lang`属性，将有助于屏幕阅读技术确定要陈述的正确语言。标识语言标签应描述页面大部分内容使用的语言。没有它，屏幕阅读器通常会默认使用操作系统的设置语言，这可能会导致错误陈述。
