TOPICS: <meta>

# HTML元数据元素：`<meta>`

HTML的`<meta>`元素表示**元数据**，而其他HTML的与元相关的元素不能表示这些元数据，例如[`<base>`](/zh-hans/webfrontend/<base>)、[`<link>`](/zh-hans/webfrontend/<link>)、[`<script>`](/zh-hans/webfrontend/<script>)、[`<style>`](/zh-hans/webfrontend/<style>)或[`<title>`](/zh-hans/webfrontend/<title>)。

## 元数据

|  |  |
| :-- | :-- |
| **内容分类** | 元数据内容。 如果存在`itemprop`属性：流程内容，短语内容. |
| **允许的内容** | 无，这是一个空元素. |
| **标签遗漏** | 由于它是一个void元素，因此必须存在开始标签，而不能存在结束标签. |
| **允许的父元素** | [`<meta charset>`](/zh-hans/webfrontend/<meta>_charset_attribute)，[`<meta http-equiv>`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)：一个[`<head>`](/zh-hans/webfrontend/<head>)元素。 如果[`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)不是编码声明，则它也可以位于[`<noscript>`](/zh-hans/webfrontend/<noscript>)元素内部，本身也位于[`<head>`](/zh-hans/webfrontend/<head>)元素内部. |
| **允许的 ARIA 角色** | 没有 |
| **DOM 接口** | `HTMLMetaElement` |

## 属性

此元素包括[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).

!!! warn "注意"
    属性[`name`](/zh-hans/webfrontend/<meta>_name_attribute)对`<meta>`元素具有特定的含义，并且`itemprop`属性不能用在已经存在
    [`name`](/zh-hans/webfrontend/<meta>_name_attribute), [`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)或[`charset`](/zh-hans/webfrontend/<meta>_charset_attribute)属性的同一个`<meta>`元素上。

| 属性 | 描述 |
| :-- | :-- |
| **[`charset`](/zh-hans/webfrontend/<meta>_charset_attribute)** | 此属性声明页面的 **[字符编码](/zh-hans/glossary/Character_Set)**。|
| **[`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)** | 定义一个**编译指示**。该属性被命名为"*http-equiv(alent)*"，因为所有允许的值都是特定**HTTP头部**的名称。 |
| **[`name`](/zh-hans/webfrontend/<meta>_name_attribute)** | 该属性定义了一段文档级**元数据的名称**。如果还设置了属性`itemprop`，[`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)或[`charset`](/zh-hans/webfrontend/<meta>_charset_attribute)之一，则不应设置此属性。 |
| **`content`** | 此属性包含[`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)或[`name`](/zh-hans/webfrontend/<meta>_name_attribute)属性的值，具体取决于所使用的属性。|

- `theme-color`，指示用户代理用来自定义页面或周围用户界面显示的建议颜色。`content`属性包含有效的CSS`color`.
- `color-scheme`: 指定与文档兼容的一种或多种配色方案。 浏览器将与用户的浏览器或设备设置一起使用此信息，以确定从背景和前景到窗体控件和滚动条，什么颜色用于所有内容。 `<meta name="color-scheme">`的主要用途是指示与浅色和深色模式的兼容性以及优先顺序.

`color-scheme`的`content`属性的值可以是以下之一：

### 正常

该文档不了解配色方案，应仅使用默认调色板进行渲染.

### 轻型| 黑暗] +

文档支持的一种或多种配色方案。 多次指定相同的配色方案与仅指定一次的效果相同。 指示多种配色方案表示文档首选第一种方案，但如果用户喜欢第二种指定方案，则可以接受.

### 只有光

表示文档仅支持浅色背景，浅色背景和深色前景色。 根据规范，“仅深色”是无效的，因为在与文档不真正兼容时强迫文档以深色模式呈现可能导致无法读取的内容； 如果未进行其他配置，则所有主要浏览器均默认为“亮”模式。

例如，要表明文档更喜欢暗模式，但在功能上也确实以亮模式呈现：

```html
<meta name="color-scheme" content="dark light">
```

这在文档级别上的工作方式与CSS`color-scheme`属性允许单个元素指定其首选和可接受的配色方案的方式相同。 您的样式可以使用`prefers-color-scheme` CSS媒体功能来适应当前的配色方案。

## 注意事项

根据属性集，元数据的类型可以是以下之一：

- 如果设置了[`name`](/zh-hans/webfrontend/<meta>_name_attribute)，则它是文档级元数据，适用于整个页面。
- 如果设置了[`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)，则它是一个编译指示，即Web服务器通常提供的有关如何提供网页的信息。
- 如果设置了[`charset`](/zh-hans/webfrontend/<meta>_charset_attribute)，则它是一个字符集声明-网页使用的字符编码。
- 如果设置了`itemprop`，则它是用户定义的元数据-对用户代理而言是透明的，因为元数据的语义是特定于用户的。
