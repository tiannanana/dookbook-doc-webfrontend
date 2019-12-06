TOPICS: <span>
AUTHORS: King; King.@mozilla.net; mdn:King.

# `<span>`

**HTML `<span>` 元素**是短语内容的通用行内容器，并没有任何特殊语义。可以使用它来编组元素以达到某种样式意图（通过使用类或者Id属性），或者这些元素有着共同的属性，
比如 **lang**。应该在没有其他合适的语义元素时才使用它。`<span>` 与 [`<div>`](/zh-hans/webfrontend/<div>) 元素很相似，
但 [`<div>`](/zh-hans/webfrontend/<div>) 是一个块元素，而 `<span>` 则是行内元素.

|  |  |
| :-- | :-- |
| **内容分类** | 流内容, 表述内容. |
| **允许的内容** | 短语内容 |
| **标签省略** | 不允许，开始标签和结束标签都不能省略。 |
| **允许的父元素** | 任意可以包含 表述内容 或 流内容 的元素。 |
| **DOM 接口** | `HTMLSpanElement` (在 HTML5, 之前是 `HTMLElement`) |

## 属性

该元素仅包含 全局属性。

## 示例

例子1：

```html
<p><span>一些文字</span></p>
```

例子2：

```html
<li><span>
    <a href="portfolio.html" target="_blank">See my portfolio</a>
</span></li>
```

CSS

```css
li span {
  background: gold;
}
```
