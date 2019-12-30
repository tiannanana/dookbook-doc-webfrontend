TOPICS: <blockquote>

# HTML 块级引用元素: `<blockquote>`

**HTML `<blockquote>` 元素**（或者 HTML 块级引用元素），代表其中的文字是引用内容。通常在渲染时，这部分的内容会有一定的缩进（注 中说明了如何更改）。
若引文来源于网络，则可以将原内容的出处 URL 地址设置到 cite 特性上，若要以文本的形式告知读者引文的出处时，
可以通过[`<cite>`](/zh-hans/webfrontend/<cite>) 元素。

## 元数据

|  |  |
| :-- | :-- |
| **内容分类** | `流式内容`, sectioning root, palpable content.|
| **Permitted content** | Flow content. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLQuoteElement` |

## 属性

此元素的属性包含[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

| 属性 | 描述 |
| :-- | :-- |
| `cite` | 是一个标注引用的信息的来源文档或者相关信息的URL。通常用来描述能够解释引文的上下文或者引用的信息。 |

## 使用备注

若要修改被引用内容的缩进距离，可以使用 CSS `margin-left` 和/或 `margin-right` 属性，或使用 `margin` 缩写属性。

若想使用在行内引用较短的内容而非创建一个单独的引用块，可使用 [`<q>`](/zh-hans/webfrontend/<q>)（Quotation）元素。

如果想要使用短引用（行间引用），可以使用 [`<q>`](/zh-hans/webfrontend/<q>) 标签。

## 示例

下面的这个例子演示了使用 `<blockquote>` 元素引用一段来自 [RFC 1149](https://tools.ietf.org/html/rfc1149) 的内容，以禽类作为载体的IP 数据包传输标准。

```html
<blockquote cite="https://tools.ietf.org/html/rfc1149">
  <p>Avian carriers can provide high delay, low
  throughput, and low altitude service.  The
  connection topology is limited to a single
  point-to-point path for each carrier, used with
  standard carriers, but many carriers can be used
  without significant interference with each other,
  outside of early spring.  This is because of the 3D
  ether space available to the carriers, in contrast
  to the 1D ether used by IEEE802.3.  The carriers
  have an intrinsic collision avoidance system, which
  increases availability.</p>
</blockquote>
```
