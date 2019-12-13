TOPICS: <meta>

# `<meta>`

HTML的`<meta>`元素表示**元数据**，而其他HTML的与元相关的元素不能表示这些元数据，例如[`<base>`](/zh-hans/webfrontend/<base>)、[`<link>`](/zh-hans/webfrontend/<link>)、[`<script>`](/zh-hans/webfrontend/<script>)、[`<style>`](/zh-hans/webfrontend/<style>)或[`<title>`](/zh-hans/webfrontend/<title>)。

## 元数据

|  |  |
| :-- | :-- |
| **内容分类** | 元数据内容。 如果存在`itemprop`属性：流程内容，短语内容. |
| **允许的内容** | 无，这是一个空元素. |
| **标签遗漏** | 由于它是一个void元素，因此必须存在开始标签，而不能存在结束标签. |
| **允许的父元素** | `<meta charset>`，`<meta http-equiv>`：一个[`<head>`](/zh-hans/webfrontend/<head>)元素。 如果`http-equiv`不是编码声明，则它也可以位于[`<noscript>`](/zh-hans/webfrontend/<noscript>)元素内部，本身也位于[`<head>`](/zh-hans/webfrontend/<head>)元素内部. |
| **允许的 ARIA 角色** | 没有 |
| **DOM 接口** | `HTMLMetaElement` |

## 属性

此元素包括[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).

!!! warn "注意"
    属性`name`对`<meta>`元素具有特定的含义，并且`itemprop`属性不能用在已经存在`name`, `http-equiv`或`charset`属性的同一个`<meta>`元素上。

| 属性 | 描述 |
| :-- | :-- |
| **[`charset`]((/zh-hans/webfrontend/<meta>_charset_attribute))** | 此属性声明页面的 **[字符编码](/zh-hans/glossary/Character_Set)**。|
| **`http-equiv`** | 定义一个**编译指示**。该属性被命名为"*http-equiv(alent)*"，因为所有允许的值都是特定**HTTP头部**的名称：<br><br>**`content-language`**<br>**已过时废弃**。请在`<html>`元素上使用`lang`属性替代。<br><br>**`content-security-policy`**<br>允许页面作者为当前页面定义**内容策略**。内容策略主要指定允许的服务器来源和脚本端点，以帮助防止跨站点脚本攻击。<br><br>**`content-type`**<br>**已过时废弃**。请在`<meta>`元素上使用`charset`属性来替代。<br><br>**`refresh`**<br>此指令指定：<br>1. **重新加载当前页面的间隔时间（单位：秒）** - 仅在`content`属性包含*正整数*的情况下。<br>2. **重定向到另一页面的时间间隔**（单位：秒) - 仅在`content`属性包含*正整数*后跟字符串 `;url=`和有效URL的情况下。<br><br>**`set-cookie`**<br>**错误：** 不要使用此指令，因为它**已过时废弃**。请改用HTTP标头`Set-Cookie`。 |
| **`name`** | 该属性定义了一段文档级**元数据的名称**。如果还设置了属性`itemprop`，`http-equiv`或`charset`之一，则不应设置此属性。<br>此元数据名称与`content`属性所包含的值相关。<br>可能的值用于`name`属性的有：<br><br>**`application-name`**，用于定义在网页中运行的**应用程序的名称**。<br> **注意：** 浏览器可以使用它来标识该应用程序。它与通常包含应用程序名称的[`<title>`](/zh-hans/webfrontend/<title>)元素不同，但也可能包含文档名称或状态之类的信息。<br>简单的网页不应定义应用程序名称。<br><br>**`author`**定义文档作者姓名的“作者”。<描述>“描述”包含页面内容的简短准确摘要。一些浏览器，例如Firefox和Opera，都将其用作添加了书签的页面的默认描述。<br><br>**`generator`**包含生成页面的**软件的标识符**。<br><br>**`keywords`**包含与**页面内容相关的单词**，用逗号隔开。<br><br>**`referrer`**控制附加到文档发送的请求的`Referer` HTTP标头 |
| **`content`** | 此属性包含`http-equiv`或`name`属性的值，具体取决于所使用的属性。|

### `<meta name="referrer">`的`content`属性值

| 值 | 描述 |
| :-- | :-- |
| `no-referrer` | 不发送HTTP Referer标头. |
| `origin` | 发送文件原点. |
| `no-referrer-when-downgrade` | 将来源作为引荐来源发送到与当前页面一样安全的URL（https→https），但不将引荐来源发送给安全程度较低的URL（https→http）。 这是默认行为.|
| `origin-when-cross-origin` | 发送相同来源请求的完整URL（带参数的），但仅发送其他情况下的来源. |
| `same-origin` | 将发送针对相同站点来源的引荐来源网址，但跨域请求将不包含引荐来源网址信息. |
| `strict-origin` | 仅将文档的原始来源作为引荐来源发送到优先级较高的目标（HTTPS-> HTTPS），而不将其发送到安全性较低的目标（HTTPS-> HTTP）. |
| `strict-origin-when-cross-origin` | 在执行相同来源的请求时发送完整的URL，仅将文档的原点发送到先验的非常安全的目标（HTTPS-> HTTPS），不发送标头到次安全的目标（HTTPS-> HTTP ）. |
| `unsafe-URL` | 发送同源或跨域请求的完整URL（带参数的URL）. |

!!! warn "Don't try this at home"
    - 某些浏览器支持引荐来源的始终，默认和从不推荐的值.
    - 动态插入`<meta name =“ referrer”>`（带有`document.write`或`appendChild`）会使引荐来源网址的行为不可预测.
    - 当定义了多个冲突策略时，将应用无引用策略.

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

此属性还可以具有从WHATWG Wiki MetaExtensions页面上定义的扩展列表中获取的值。 尽管尚未正式接受任何名称，但一些常用名称是：

- `creator` 它定义了文档创建者的名称，例如组织或机构。 如果不止一个，则应使用多个`<meta>`元素。
- `googlebot` Googlebot（Google的索引搜寻器）仅跟随机器人的同义词。
- `publisher` 定义文档发布者的名称。
- `robots` 定义了协作爬网程序或“机器人”应与页面一起使用的行为。 它是以下值的逗号分隔列表：

### `<meta name="robots">`的`content`属性值

| 值 | 描述 | 使用者 |
| :-- | :-- | :-- |
| `index` | 允许机械手索引页面（默认）. | 所有 |
| `noindex` | 要求机械手不索引页面. | 所有 |
| `follow` | 允许漫游器跟踪页面上的链接（默认）. | 所有 |
| `nofollow` | 要求漫游器不遵循页面上的链接. | 所有 |
| `none` | 相当于noindex，nofollow | Google |
| `noodp` | 禁止将Open Directory Project描述（如果有）用作搜索引擎结果中的页面描述.| Google, Yahoo, Bing |
| `noarchive` | 要求搜索引擎不要缓存页面内容. | Google, Yahoo, Bing|
| `nosnippet` | 防止在搜索引擎结果中显示页面的任何描述. | Google, Bing|
| `noimageindex` | 要求此页面不显示为索引图像的引用页面.| Google|
| `nocache` | Synonym of noarchive. | Bing |

!!! warn "Don't try this at home"
    - 只有合作机器人遵守这些规则。 不要期望阻止电子邮件收集器。
    - 机器人仍然需要访问页面才能阅读这些规则。 为防止带宽消耗，请使用robots.txt文件.
    - 如果要删除页面，`noindex`将起作用，但仅在机器人再次访问该页面之后才起作用。 确保`robots.txt`文件没有阻止再次访问。
    - 一些值是互斥的，例如`index`和`noindex`或`follow`和`nofollow`。 在这些情况下，机器人的行为是不确定的，并且在它们之间可能有所不同。
    - 一些爬虫机器人，例如Google，Yahoo和Bing，都为HTTP标头`X-Robots-Tag`支持相同的值；这允许图像之类的非HTML文档使用这些规则。

- slurp是机器人的同义词，但仅适用于Slurp-Yahoo Search的搜寻器。
- 视口，它会提示有关视口初始尺寸的大小。 仅用于移动设备。

### `<meta name="viewport">`的`content`属性值

| 值 | 可能的子值 | 描述 |
| :-- | :-- | :-- |
| `width` | 一个正整数或文本`device-width` | 定义要在其上呈现网站的视口的像素宽度. |
| `height` | 一个正整数或文本`device-height` | 定义视口的高度。 未被任何浏览器使用. |
| `initial-scale` | 介于`0.0`和`10.0`之间的正数 | 定义设备宽度（纵向模式下的设备宽度或横向模式下的设备高度）与视口大小之间的比率. |
| `maximum-scale` | 介于`0.0`和`10.0`之间的正数 | 定义放大的最大数量。它必须大于或等于最小比例，否则行为未定义。 浏览器设置可以忽略此规则，而iOS10 +默认会忽略它. |
| `minimum-scale` | 介于`0.0`和`10.0`之间的正数 | 定义最小缩放级别。 它必须小于或等于最大比例，否则行为是不确定的。 浏览器设置可以忽略此规则，而iOS10 +默认会忽略它. |
| `user-scalable` | `yes`或`no` | 如果设置为no，则用户将无法放大网页。 默认值为是。 浏览器设置可以忽略此规则，默认情况下，iOS10 +会将其忽略.

| 规格 | 状态 | 评论 |
| :-- | :-- | :-- |
| CSS设备适配该规范中`<meta name="viewport">`的定义. | 工作草案 | 非规范地描述了视口META元素 |

另请参见：@viewport

!!! warn "事实上的主导地位"
    尽管没有标准化，但由于事实上的主导地位，大多数移动浏览器都尊重此声明。
    设备和浏览器的默认值可能会有所不同.

| 属性 | 描述 |
| :-- | :-- |
| `scheme` | 此属性定义描述元数据的方案。 方案是一种导致对内容值（例如格式）进行正确解释的上下文。|

!!! error "警告：过时废弃"
    请勿使用此值，因为它**已过时废弃**。 没有替代品，因为没有实际用途。

## 注意事项

根据属性集，元数据的类型可以是以下之一：

- 如果设置了`name`，则它是文档级元数据，适用于整个页面。
- 如果设置了`http-equiv`，则它是一个编译指示，即Web服务器通常提供的有关如何提供网页的信息。
- 如果设置了`charset`，则它是一个字符集声明-网页使用的字符编码。
- 如果设置了`itemprop`，则它是用户定义的元数据-对用户代理而言是透明的，因为元数据的语义是特定于用户的。

## 示例

```html
<!-- 标注网站作者信息：Dookbook是这个网页的作者 -->
<meta name="author" content="Dookbook">

<!-- 描述这个网页 -->
<meta name="description" content="A Dookbook webpage">

<!-- 关于这个网页的关键字，用逗号隔开 -->
<meta name="keywords" content="Dookbook,a,b">

<!-- 3秒后重新加载（刷新）这个网页 -->
<meta http-equiv="refresh" content="3">
<meta http-equiv="refresh" content="3;url=https://dookbook.info">
```

## 可达性问题

### 刷新内容

设置了刷新值的页面存在时间间隔太短的风险。借助屏幕阅读器等辅助技术进行导航的人们在自动重定向之前可能无法阅读并理解页面的内容。 页面内容的突然，未经通知的更新也可能使视力低下的人迷失方向。

- [MDN了解WCAG，准则2.1的说明](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Operable#Guideline_2.2_%E2%80%94_Enough_Time_Provide_users_enough_time_to_read_and_use_content)
- [MDN了解WCAG，准则3.1的说明](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Understandable#Guideline_3.2_%E2%80%94_Predictable_Make_Web_pages_appear_and_operate_in_predictable_ways)
- [了解成功标准2.2.1 | W3C了解WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-required-behaviors.html)
- [了解成功标准2.2.4 | W3C了解WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/time-limits-postponed.html)
- [了解成功标准3.2.5 | W3C了解WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-no-extreme-changes-context.html)
  
### 视口缩放

通过将`user-scalable`设置为no来禁用缩放功能，这会阻止视力不好的人阅读和理解页面内容。

- [MDN了解WCAG，准则1.4解释](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#Guideline_1.4_Make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [了解成功标准1.4.4 | W3C了解WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)
