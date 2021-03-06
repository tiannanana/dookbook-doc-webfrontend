TOPICS: <a>

# HTML 锚元素：`<a>`

**HTML `<a>` 元素**（或称**锚元素**）可以创建通向其他网页、文件、同一页面内的位置、电子邮件地址或任何其他 URL 的**超链接**。

## 技术摘要

|  |  |
| :-- | :-- |
| **内容分类** | 流内容、文字内容、交互内容、可触摸内容。
| **允许的内容** | 可见的内容，包含流内容（不包括交互式内容）或文字内容。|
| **标签省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 接受短语内容的任何元素或接受流内容的任何元素，但始终不接受 `<a>` 元素（根据对称的逻辑原理，如果 `<a>` 标记作为父元素，不能具有交互内容，则相同的 `<a>` 内容不能具有 `<a>` 标记作为其父元素）。|
| **Permitted ARIA roles** | `button`, `checkbox`, `menuitem`, `menuitemcheckbox`, `menuitemradio`, `option`, `radio`, `switch`, `tab`, `treeitem` |
| **DOM 接口** | `HTMLAnchorElement` |

## 属性

该元素的属性包含[HTML全局属性](/zh-hans/webfrontend/HTML_Global_attributes)。

| 属性 | 描述 |
| :-- | :-- |
| **`href`** | 包含**超链接**指向的URL或URL片段(fragment)。URL不限于基于HTTP的文档，也可以使用浏览器支持的任何协议。例如，[`file:`](https://en.wikipedia.org/wiki/File_URI_scheme)、`ftp:`和`mailto:`。|
| *`target`* | 该属性指定在**何处显示**链接的资源。取值为标签页(tab)、窗口(window)、或[`<iframe>`](/en/webfrontend/<iframe>)等浏览上下文的名称或关键词。以下关键字具有特殊的意义:<br><br>**`_self`** (*默认*): **当前页面加载**，即当前的响应到同一浏览上下文<br><br>**`_blank`**: **新窗口或标签页打开**，即到一个新的未命名的浏览器上下文<br><br>**`_parent`**: 加载响应到当前浏览上下文的父浏览上下文。如果没有父浏览上下文，此选项的行为方式与`_self`相同<br><br>**`_top`**: 加载响应进入顶层浏览上下文（即，浏览上下文，它是当前的一个的祖先，并且没有parent）。如果没有parent框架或者浏览上下文，此选项的行为方式相同`_self`<br><br>**注意：**使用`target`时，考虑添加`rel="noopener"`以防止针对`window.opener`API的恶意行为。 |
| *`rel`* | 该属性指定了目标对象到链接对象的**关系**。该值是*空格分隔*的列表类型值。 |
| *`download`* | 此属性指示浏览器**下载**URL而不是导航到它，因此将提示用户将其保存为本地文件。如果属性有一个值，那么此值将在下载保存过程中作为预填充的文件名（如果用户需要，仍然可以更改文件名）。此属性对允许的值没有限制，但是`/`和`\`会被转换为下划线。大多数文件系统限制了文件名中的标点符号，因此浏览器将相应地调整建议的文件名。<br>**Note:**<br>此属性仅适用于同源 URL。<br>尽管 HTTP URL 需要位于同一源中，但是可以使用`blob:`URL和`data:` URL ，以方便用户下载使用JavaScript生成的内容（例如使用在线绘图Web应用程序创建的照片）。<br>如果HTTP头部中的 `Content-Disposition`赋予了一个不同于此属性的文件名，HTTP头属性优先于此属性。<br>如果 HTTP头属性`Content-Disposition` 被设置为inline（即`Content-Disposition='inline'`），那么 Firefox 优先考虑HTTP 头 `Content-Disposition`download 属性。 |
| `hreflang` | 该属性用于指定链接文档的人类语言。其仅提供建议，并没有内置的功能。hreflang 允许的值取决于HTML5 [BCP47](http://www.ietf.org/rfc/bcp/bcp47.txt) |
| `ping` | 包含一个以空格分隔的url列表，当跟随超链接时，将由浏览器(在后台)发送带有正文 PING 的 POST 请求。通常用于跟踪 |
| `referrerpolicy` | 表明在获取URL时发送哪个提交者（referrer）:<br><br>`"no-referrer"` 表示 `Referer:` 头将不会被发送。<br>`"no-referrer-when-downgrade"` 表示当从使用HTTPS的页面导航到不使用 TLS(HTTPS)的来源 时不会发送 `Referer:` 头。如果没有指定策略，这将是用户代理的默认行为。<br>`"origin"` 表示 referrer将会是页面的来源，大致为这样的组合：主机和端口（不包含具体的路径和参数的信息）。<br>`"origin-when-cross-origin"` 表示导航到其它源将会限制为这种组合：主机 + 端口，而导航到相同的源将会只包含 referrer的路径。<br>`'strict-origin-when-cross-origin'`<br>`"unsafe-url"` 表示 referrer将会包含源和路径（domain + path）（但是不包含密码或用户名的片段）。这种情况是不安全的，因为它可能会将安全的URLs数据泄露给不安全的源。 |
| `type` | 该属性指定在一个[[MIME]]类型链接目标的形式的**媒体类型**。其仅提供建议，并没有内置的功能。|

## 示例

### 链接到外部地址

```html
<a href="http://dookbook.info/">外部链接</a>
```

### 在新的浏览环境打开链接

!!! warn "安全和隐私问题"
    使用`target="_blank"`链接到另一个页面将在与页面相同的进程上运行新页面。
    如果新页面执行昂贵的JavaScript，那么页面的性能可能会受到影响。要避免这种情况，请使用`rel=noopener`。

```html
<!-- 在新的标签页或浏览器窗口打开链接 -->
<a href="https://dookbook.info/" target="_blank" rel="noreferrer noopener">External Link</a>
```

### 链接到本页的某个部分

```html
<!-- 链接到本页的某个部分 id="attr-href" -->
<a href="#attr-href">链接的显示文本</a>
```

### 创建一个可点击的图片

```html
<a href="https://dookbook.info">
  <img src="https://dookbook.info/static/img/logo-tail.svg" alt="Dookbook logo" />
</a>
```

### Email链接

点击该按钮或链接，可将用户的电子邮件程序打开，开始发送新邮件。这里有一个简单的例子：

```html
<a href="mailto:dookbook@zhiliaokeji.com">发送邮件给Dookbook</a>
```

有关`mailto:`URL方案的更多细节，比如如何包含主题，正文，或其他预定内容，参考[RFC 6068](https://tools.ietf.org/html/rfc6068)。

### 电话链接

提供电话链接有助于用户查看连接到手机的网络文档和笔记本电脑。

```html
<a href="tel:+8612312345678">+86 123 1234 5678</a>
```

关于`tel:`更详细的语法请参考[RFC 3966](https://tools.ietf.org/html/rfc3966)。

### 下载链接

```html
<a href="<下载地址>" download="<默认文件名>" title="<文本提示>">下载链接文本</a>
```

### 使用 download 属性将 `<canvas>` 保存为 PNG 格式

如果你想允许用户下载一个HTML画布，你可以创建一个下载属性和画布数据作为文件URL链接图像：

```javascript
var link = document.createElement('a');
link.innerHTML = 'download image';

link.addEventListener('click', function(ev) {
    link.href = canvas.toDataURL();
    link.download = "my_painting.png";
}, false);

document.body.appendChild(link);
```

## 无障碍建议

锚点标签常常通过将`href`属性设置为`"#"` 或 `"javascript:void(0)"` 来创造一个能阻止页面刷新的伪按钮的方式被滥用。 这些属性值会在拖动或
复制链接时导致意外行为，在新窗口或新标签打开链接，加入书签以及JavaScript仍在下载时会出现错误或被禁用。这也会向辅助技术（如屏幕阅读器）传达不正确的语义。在这些情况下，推荐使用
[`<button>`](/zh-hans/webfrontend/<button>) 来代替。通常情况下，您应该只将锚点用于正常的URL导航。
