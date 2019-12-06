TOPICS: <i>
AUTHORS: Mike Chen; ranwu@mozilla.net; mdn:ranwu
         潘韬; pantao@mozilla.net; mdn:pantao

# `<i>`

**HTML元素 `<i>`** 用于表现因某些原因需要区分普通文本的一系列文本。例如技术术语、外文短语或是小说中人物的思想活动等，它的内容通常以斜体显示。

## 属性

该元素只包含 全局属性。

## 示例

```html
<p>The Latin phrase <i class="latin">Veni, vidi, vici</i> is often
mentioned in music, art, and literature</p>
```

## 注释

在较早版本的 HTML 技术参数声明中，`<i>` 标签只是一个用于将文本显示为斜体的表示性元素，很像 [`<b>`](/zh-hans/webfrontend/<b>) 标签被用来将文本显示为粗体。情况不再是这样了，
因为这些标签现在定义了更多的语义而不只是排版外观。`<i>` 标签应表现一系列带有不同语义的文本，它的典型样式显示为斜体。这意味着浏览器通常任会将内容显示为斜体，但是，根据定义，不再是必须的。

该元素只在没有更适合的语义元素表示时使用。例如：

- 使用 [`<em>`](/zh-hans/webfrontend/<em>) 表示强调或重读。
- 使用 [`<strong>`](/zh-hans/webfrontend/<strong>) 表示重要性。
- 使用 [`<mark>`](/zh-hans/webfrontend/<mark>) 表示相关性。
- 使用 [`<cite>`](/zh-hans/webfrontend/<cite>) 标记著作名，如一本书、剧本或是一首歌。
- 使用 [`<dfn>`](/zh-hans/webfrontend/<dfn>) 标记术语的定义实例。

使用 **class** 属性用来识别为何使用该元素是一个很好的办法，这样的话，如果该表示以后需要改变，就可以有选择性地改变样式表。
