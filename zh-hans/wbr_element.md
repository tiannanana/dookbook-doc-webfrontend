TOPICS: <wbr>

# `<wbr>`

**HTML `<wbr>` 元素**  — 一个文本中的位置，其中浏览器可以选择来换行，虽然它的换行规则可能不会在这里换行。

|  |  |
| :-- | :-- |
| **内容分类** | 流程内容，措辞内容. |
| **允许的内容** | 空的 |
| **标签遗漏** | 它是一个空元素； 它必须具有开始标签，但不能具有结束标签. |
| **允许的父元素** | 任何接受短语内容的元素. |
| **允许的 ARIA 角色** | 任何 |
| **DOM 接口** | `HTMLElement` |

## 属性

这个元素仅仅包含[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)

## 笔记

在 UTF-8 编码的页面中， `<wbr>` 表现为 `U+200B ZERO-WIDTH SPACE` （零宽空格）代码点。特别是，它表现为 Unicode bidi BN 代码点，也就是说，它对
bidi-ordering 没有影响：`<div dir=rtl>123,<wbr>456</div>` 展示 `123,456` 而不是 `456,123`，当不拆成的两行时候。

出于相同原因， `<wbr>`元素不会在换行的地方引入连字符。为了使连字符仅仅在行尾出现，使用连字符软实体 (`&shy;`) 来代替。

这个元素首先在 Internet Explorer 5.5 中实现，并且在 HTML5 中官方定义。

## 示例

Yahoo 代码规范 推荐 在标点之前为 URL 换行，以便避免将标点符号留在行尾，这会让读者将 URL 的末尾搞错。

```html
<p>http://this<wbr>.is<wbr>.a<wbr>.really<wbr>.long<wbr>.example<wbr>.com/With<wbr>/deeper<wbr>/level<wbr>/pages<wbr>/deeper<wbr>/level<wbr>/pages<wbr>/deeper<wbr>/level<wbr>/pages<wbr>/deeper<wbr>/level<wbr>/pages<wbr>/deeper<wbr>/level<wbr>/pages</p>
```
