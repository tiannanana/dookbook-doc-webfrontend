TOPICS: <img>

# HTML 图像元素：`<img>`

**HTML `<img>` 元素** 代表文档中的一个**图像**。

!!! warn "使用说明"
    浏览器并不总是显示该元素中的图像。对于非图形浏览器（包括那些有视力障碍的人所使用的）来说就是这种情况，如果用户选择不显示图像，或者如果浏览器无法显示图像，因为它是无效的或 不支持的类型。
    在这些情况下，浏览器会用该元素的 `alt` 属性定义的文本来替换图像。

## 元数据

|  |  |
| :-- | :-- |
| **内容类别** | 流式内容，段落内容，嵌入式内容，可触摸内容。如果元素有 `usemap` 属性，它也是交互内容的一部分。|
| **允许的内容** | 没有，它是一个 空元素. |
| **标签省略** | 必须有一个开始标签，不允许有结束标签. |
| **允许的父元素** | 接受嵌入式内容的任意元素. |
| **DOM 接口** | `HTMLImageElement` |

## 属性

这个元素包括 [HTML全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

| 属性 | 描述 |
| :-- | :-- |
| `alt` | 这个属性定义了描述图像的替换文本。用户将看到这个显示，如果图像的URL是错误的，该图像不在 支持的格式 列表中，或者如果图像还没有被下载。<br>使用说明： 省略这个属性表明该图像是内容的关键部分，但没有等效的文本可用。把这个属性设置为空字符串，表明该图像不是内容的关键部分，非可视化浏览器在渲染的时候可能会忽略它。 |
| `crossorigin` | 这个枚举属性表明是否必须使用 CORS 完成相关图像的抓取。启用CORS的图像 在 [`<canvas>`](/zh-hans/webfrontend/<canvas>) 元素中可以重复使用而不会被污染。允许的值有：<br><br>`anonymous`<br>执行一个跨域的请求（比如，有 `Origin:` HTTP header）。但是没有发送证书（比如，没有 cookie，没有 X.509 证书，没有 HTTP 基本的授权认证）。如果服务器没有给源站证书（没有设置 Access-Control-Allow-Origin: HTTP头），图像会被污染而且它的使用会被限制。<br><br>`use-credentials`<br>一个有证书的跨域请求（比如，有 `Origin:` HTTP header）被发送 （比如，a cookie, a certificate, and HTTP Basic authenticationis performed）。如果服务器没有给源站发送证书（通过 Access-Control-Allow-Credentials: HTTP header），图像将会被污染，且它的使用会受限制。当用户并未显式使用本属性时，默认不使用 CORS 发起请求(例如，不会向服务器发送 HTTP 头部信息)，用以防止其在[`<canvas>`](/zh-hans/webfrontend/<canvas>)中的使用。如果无效，默认当做 **anonymous** 关键字生效。更多信息，请查看 CORS 属性设置 。 |
| `height` | 图像的高度，在 HTML5 中的单位是 CSS 像素，在 HTML 4 中可以是像素也可以是百分比。 |
| `ismap` | 这个布尔属性表示图像是否是服务器端map的一部分。如果是， 那么点击的精准坐标将会被发送到服务器。<br>**Note:**<br>使用说明：只有在 `<img>` 元素是一个拥有有效 `href` 属性的 [`<a>`](/zh-hans/webfrontend/<a>) 元素的后代元素的情况下，这个属性才会被允许使用。 |
| `longdesc` | URL 描述要显示图像的URL描述，是对 **`alt`** 文本的补充。 |
| `sizes` | 表示资源大小的以逗号隔开的一个或多个字符串。每一个资源大小包括：<br>1. 一个媒体条件。最后一项一定是被忽略的。<br>2. 一个资源尺寸的值。<br><br>资源尺寸的值被用来指定图像的预期尺寸。当`srcset`使用 `'w'` 描述符时，用户代理使用当前图像大小来选择`srcset`中合适的一个图像URL。 被选中的尺寸影响图像的显示大小（如果没有CSS样式被应用的话）。如果没有设置`srcset`属性，或者没值，那么sizes属性也将不起作用。 |
| `src` | 图像的 URL，这个属性对 `<img>` 元素来说是必需的。在支持 `srcset` 的浏览器中，`src` 被当做拥有一个像素密度的描述符 `1x` 的候选图像处理，除非一个图像拥有这个像素密度描述符已经被在 `srcset` 或者 `srcset` 包含 `'w'` 描述符中定义了. |
| `srcset` | 以逗号分隔的一个或多个字符串列表表明一系列用户代理使用的可能的图像。每一个字符串由以下组成：<br>1. 一个图像的 URL。<br>2. 可选的，空格后跟以下的其一：<br><br>一个宽度描述符，这是一个正整数，后面紧跟 'w' 符号。该整数宽度除以sizes属性给出的资源（source）大小来计算得到有效的像素密度，即换算成和x描述符等价的值。<br><br>一个像素密度描述符，这是一个正浮点数，后面紧跟 'x' 符号。<br>如果没有指定源描述符，那它会被指定为默认的 `1x`。<br><br>在相同的 `srcset` 属性中混合使用宽度描述符和像素密度描述符时，会导致该值无效。重复的描述符（比如，两个源 在相同的`srcset`两个源都是 `'2x'`）也是无效的。<br><br>浏览器选择在给出的时间点显示大部分 adequate 图片。 |
| `width` | 图像的宽度，在 HTML5 中单位是 CSS 像素， 在 HTML 4 中可以是像素也可以是百分比。 |
| `usemap` | 与元素相关联的的 image map 的部分 URL（以 '`#`' 开始的部分）。<br>Note:<br>使用说明： 如果 `<img>` 元素是 [`<a>`](/zh-hans/webfrontend/<a>) 或 [`<button>`](/zh-hans/webfrontend/<button>) 元素的后代元素则不能使用这个属性。 |

## 支持的图像格式

HTML 标准并没有给出必须支持的图像格式的列表，因此每个用户代理支持一组不同的格式。 Gecko 支持：

- [JPEG](http://en.wikipedia.org/wiki/JPEG)
- [GIF](http://en.wikipedia.org/wiki/Graphics_Interchange_Format)，包括动态的GIFs
- [PNG](http://en.wikipedia.org/wiki/Portable_Network_Graphics)
- [APNG](https://wiki.developer.mozilla.org/en-US/docs/Animated_PNG_graphics)
- [SVG](https://wiki.developer.mozilla.org/en-US/docs/SVG)
- [BMP](http://en.wikipedia.org/wiki/BMP_file_format)
- [BMP ICO](http://en.wikipedia.org/wiki/ICO_%28file_format%29)
- [PNG ICO](http://en.wikipedia.org/wiki/ICO_%28file_format%29)

## 与 CSS 的交互

关于 CSS，`<img>` 是一个 替换元素。它没有基线，这意味着当在一个行内格式的上下文中使用 `vertical-align: baseline` 时，图像的底部将会与容器的基线对齐。

根据它的类型，图像可能会有一个本征维数（intrinsic dimension），但这不是一个必要条件：SVG图像就没有，而光栅图像有。

## 示例

### 基础写法

```html
<!-- 全局链接地址 -->
<img src="https://dookbook.info/static/img/logo-tail.svg" alt="Dookbook logo">

<!-- 本地绝对路径 -->
<img src="/static/img/logo-tail.svg" alt="Dookbook logo">

<!-- 本地相对路径 -->
<img src="static/img/logo-tail.svg" alt="Dookbook logo">
```

### 图像链接

```html
<a href="https://dookbook.info">
  <img src="https://dookbook.info/static/img/logo-tail.svg" alt="Visit the Dookbook site">
</a>
```

### 使用 `srcset` 和 `sizes` 属性

在支持 `srcset` 的用户代理中，当使用 '`w`' 描述符时，`src` 属性会被忽略。当匹配了媒体条件 (`min-width: 600px`) 时，图像将宽 `200px`，否则宽 `50vw`（视图宽度的50%）。

```html
<img src="clock-demo-thumb-200.png"
     alt="Clock"
     srcset="clock-demo-thumb-200.png 200w,
             clock-demo-thumb-400.png 400w"
     sizes="(min-width: 600px) 200px, 50vw">
```
