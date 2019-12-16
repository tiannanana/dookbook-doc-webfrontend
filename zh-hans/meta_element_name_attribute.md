TOPICS: <meta> name attribute

# `<meta>`元素的`name`属性

该属性定义了一段文档级**元数据的名称**。如果还设置了属性`itemprop`，[`http-equiv`](/zh-hans/webfrontend/<meta>_http-equiv_attribute)或[`charset`](/zh-hans/webfrontend/<meta>_charset_attribute)之一，则不应设置此属性。

此元数据名称与`content`属性所包含的值相关。

## `<meta name="application-name">`

**`application-name`**，用于定义在网页中运行的**应用程序的名称**。

**注意：** 浏览器可以使用它来标识该应用程序。它与通常包含应用程序名称的[`<title>`](/zh-hans/webfrontend/<title>)元素不同，但也可能包含文档名称或状态之类的信息。

简单的网页不应定义应用程序名称`application-name`。

## `<meta name="author">`

**`author`**，用于定义文档的**作者信息**。

例如：

```html
<!-- 标注网站作者信息：Dookbook是这个网页的作者 -->
<meta name="author" content="Dookbook">
```

## `<meta name="description">`

**`description`**，用于包含页面内容的**简短准确摘要**。一些浏览器，例如Firefox和Opera，都将其用作添加了书签的页面的默认描述。

例如：

```html
<!-- 描述这个网页 -->
<meta name="description" content="A Dookbook webpage">
```

## `<meta name="generator">`

**`generator`**，用于包含生成或制作页面的**软件的标识符**。

## `<meta name="keywords">`

**`keywords`**，用于包含与**页面内容相关的单词**，用*逗号*隔开。

例如：

```html
<!-- 关于这个网页的关键字，用逗号隔开 -->
<meta name="keywords" content="Dookbook,a,b">
```

## `<meta name="referrer">`

**`referrer`**，用于控制附加到文档发送的请求的`Referer`HTTP头部。

### `<meta name="referrer">`的`content`属性值

!!! warn "注意"
    - 某些浏览器支持废弃的`referrer`值：`always`，`default`和`never`。
    - 动态插入`<meta name =“ referrer”>`（带有`document.write`或`appendChild`）会使引荐来源网址的行为不可预测。
    - 当定义了多个冲突策略时，将应用无引用策略`no-referrer`。

| 值 | 描述 |
| :-- | :-- |
| `no-referrer` | 不发送HTTP `Referer`头部. |
| `origin` | 发送文件来源. |
| `no-referrer-when-downgrade` | 将来源作为引荐来源发送到与当前页面一样安全的URL（https→https），但不将引荐来源发送给安全程度较低的URL（https→http）。 这是*默认*行为.|
| `origin-when-cross-origin` | 发送相同来源请求的完整URL（带参数的），但仅发送其他情况下的来源. |
| `same-origin` | 将发送针对相同站点来源的引荐来源网址，但跨域请求将不包含引荐来源网址信息. |
| `strict-origin` | 仅将文档的原始来源作为引荐来源发送到优先级较高的目标（HTTPS-> HTTPS），而不将其发送到安全性较低的目标（HTTPS-> HTTP）. |
| `strict-origin-when-cross-origin` | 在执行相同来源的请求时发送完整的URL，仅将文档的原点发送到先验的非常安全的目标（HTTPS-> HTTPS），不发送标头到次安全的目标（HTTPS-> HTTP ）. |
| `unsafe-URL` | 发送同源或跨域请求的完整URL（带参数的URL）. |

## `<meta name="robots">`

此属性还可以具有从WHATWG Wiki MetaExtensions页面上定义的扩展列表中获取的值。 尽管尚未正式接受任何名称，但一些常用名称是：

- `creator` 它定义了文档创建者的名称，例如组织或机构。 如果不止一个，则应使用多个[`<meta>`](/zh-hans/webfrontend/<meta>)元素。
- `googlebot` **Googlebot**（Google搜索的爬虫）。
- `slurp` **Slurp-Yahoo**搜索的爬虫。
- `publisher` 定义文档**发布者的名称**。
- `robots` 定义了**协作爬虫程序**（“机器人”）应与页面交互的行为。它是以下值的*逗号*分隔列表：

### `<meta name="robots">`的`content`属性值

| 值 | 描述 | 使用者 |
| :-- | :-- | :-- |
| `index` | 允许搜索引擎爬虫索引页面（默认）。| 所有 |
| `noindex` | 要求搜索引擎爬虫不索引页面。 | 所有 |
| `follow` | 允许搜索引擎爬虫跟踪页面上的链接（默认）。 | 所有 |
| `nofollow` | 要求搜索引擎爬虫不遵循页面上的链接。 | 所有 |
| `none` | 相当于`noindex, nofollow` | Google |
| `noodp` | 禁止将Open Directory Project描述（如果有）用作搜索引擎结果中的页面描述.| Google, Yahoo, Bing |
| `noarchive` | 要求搜索引擎不要缓存页面内容. | Google, Yahoo, Bing|
| `nosnippet` | 防止在搜索引擎结果中显示页面的任何描述. | Google, Bing|
| `noimageindex` | 要求此页面不显示为索引图像的引用页面.| Google|
| `nocache` | 等同于`noarchive`. | Bing |

!!! info "Note"
    - 只有合作爬虫遵守这些规则。 不要期望阻止电子邮件收集器。
    - 爬虫仍然需要访问页面才能阅读这些规则。 为防止带宽消耗，请使用`robots.txt`文件.
    - 如果要删除页面，`noindex`将起作用，但仅在爬虫再次访问该页面之后才起作用。 确保`robots.txt`文件没有阻止再次访问。
    - 一些值是互斥的，例如`index`和`noindex`或`follow`和`nofollow`。 在这些情况下，爬虫的行为是不确定的，并且在它们之间可能有所不同。
    - 一些爬虫机器人，例如Google，Yahoo和Bing，都为HTTP标头`X-Robots-Tag`支持相同的值；这允许图像之类的非HTML文档使用这些规则。

## `<meta name="viewport">`

这个属性会提示有关视口**初始尺寸的大小**。**仅用于移动设备**。

!!! warn "事实上的主导地位"
    尽管没有标准化，但由于事实上的主导地位，大多数移动浏览器都尊重此声明。
    设备和浏览器的默认值可能会有所不同。

### `<meta name="viewport">`的`content`属性值

| 值 | 可能的子值 | 描述 |
| :-- | :-- | :-- |
| `width` | 一个正整数或文本`device-width` | 定义要在其上呈现网站的视口的**像素宽度**. |
| `height` | 一个正整数或文本`device-height` | 定义视口的**高度**。 **未被任何浏览器使用**. |
| `initial-scale` | 介于`0.0`和`10.0`之间的正数 | 定义设备宽度（纵向模式下的设备宽度或横向模式下的设备高度）与视口大小之间的比率. |
| `maximum-scale` | 介于`0.0`和`10.0`之间的正数 | 定义放大的最大数量。它必须大于或等于最小比例，否则行为未定义。 浏览器设置可以忽略此规则，而**iOS10+** 默认会忽略它. |
| `minimum-scale` | 介于`0.0`和`10.0`之间的正数 | 定义最小缩放级别。 它必须小于或等于最大比例，否则行为是不确定的。 浏览器设置可以忽略此规则，而**iOS10+** 默认会忽略它. |
| `user-scalable` | `yes`或`no` | 如果设置为`no`，则用户将无法放大网页。 默认值为`yes`。 浏览器设置可以忽略此规则，默认情况下，**iOS10+** 会将其忽略.

### 视口缩放的访问性问题

通过将`user-scalable`设置为`no`来禁用缩放功能，这会阻止视力不好的人阅读和理解页面内容。

- [MDN了解WCAG，准则1.4解释](https://wiki.developer.mozilla.org/en-US/docs/Web/Accessibility/Understanding_WCAG/Perceivable#Guideline_1.4_Make_it_easier_for_users_to_see_and_hear_content_including_separating_foreground_from_background)
- [了解成功标准1.4.4 | W3C了解WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html)

## `<meta name="theme-color">`

`theme-color`，指示用户代理（浏览器）用来自定义页面或用户界面周边的**建议颜色**。`content`属性包含有效的CSS`color`。

## `<meta name="color-scheme">`

`color-scheme`，指定与文档兼容的一种或多种配色方案。浏览器将与用户的浏览器或设备设置一起使用此信息，以确定从背景和前景到窗体控件和滚动条，什么颜色用于所有内容。

`<meta name="color-scheme">`的主要用途是指示与*浅色* (*`light`*)和*深色* (*`dark`*)模式的兼容性以及优先顺序。

`color-scheme`的`content`属性的值可以是以下之一：

### `normal` 正常

该文档应仅使用*默认*的调色板进行渲染。

### `light` | `dark` 浅色或暗黑

文档支持的一种或多种配色方案。多次指定相同的配色方案与仅指定一次的效果相同。指示多种配色方案表示文档首选第一种方案，但如果用户喜欢第二种指定方案，则可以接受。

### `only light` 只限浅色

表示文档**仅支持浅色模式 (light mode)**，即浅色背景和深色前景色。根据规范，`only dark`是无效的，因为在与文档不真正兼容时强迫文档以深色模式呈现可能导致无法读取的内容；
如果未进行其他配置，则所有主要浏览器均默认为*浅色模式 (light mode)*。

例如，要表明文档更喜欢*暗黑模式* (*dark mode*)，但在功能上也确实以*浅色模式* (*light mode*)呈现：

```html
<meta name="color-scheme" content="dark light">
```

这在文档级别上的工作方式与CSS`color-scheme`属性允许单个元素指定其首选和可接受的配色方案的方式相同。 您的样式可以使用`prefers-color-scheme` CSS媒体功能来适应当前的配色方案。

## `<meta name="scheme">`

!!! error "已过时废弃"
    没有替代品，因为没有实际用途。
