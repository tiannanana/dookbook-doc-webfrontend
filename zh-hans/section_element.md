TOPICS: <section>
AUTHORS: 许振涛; Annlix@mozilla.net; mdn:Annlix
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei
         ZoomZhao; zoom.zhao@gmail.com; github:ZoomZhao

# `<section>`

**HTML `<section>` 元素**表示一个包含在HTML文档中的独立部分，它没有更具体的语义元素来表示，一般来说会有包含一个标题。

例如，导航菜单应该包含在[`<nav>`](/zh-hans/webfrontend/<nav>)元素中，但搜索结果列表和地图显示及其控件没有特定元素，可以放在`<section>`里。

!!! warn "Don't try this at home"
    注意：如果元素的内容作为一个独立的有意义的集合，[`<article>`](/zh-hans/webfrontend/<article>)元素可能是更好的选择。

|  |  |
| :-- | :-- |
| **内容分类** | 流内容，切片内容，可触知的内容。 |
| **允许的内容** | 流内容。 |
| **标签省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 接受流内容的任何元素。 请注意，`<section>`元素不得为[`<address>`](/zh-hans/webfrontend/<address>)元素的后代。 |
| **允许的 ARIA 角色** | `alert`, `alertdialog`, `application`, `banner`, `complementary`, `contentinfo`, `dialog`, `document`, `feed`, `log`, `main`, `marquee`, `navigation`, `search`, `status`, `tabpanel` |
| **DOM 接口** | `HTMLElement` |

## 属性

此元素只包含全局属性

## 使用说明

- 一般通过是否包含一个标题 ([`<h1>`](/zh-hans/webfrontend/<h1>)-[`<h6>`](/zh-hans/webfrontend/<h6>) element)
作为子节点 来 辨识每一个`<section>`。
- 如果元素内容可以分为几个部分的话，应该使用 [`<article>`](/zh-hans/webfrontend/<article>) 而不是 `<section>`。
- 不要把 `<section>` 元素作为一个普通的容器来使用，这是本应该是[`<div>`](/zh-hans/webfrontend/<div>)的用法
（特别是当片段（the sectioning ）仅仅是为了美化样式的时候）。
一般来说，一个 `<section>` 应该出现在文档大纲中。

范例1：

之前

```html
<div>
  <h1>Heading</h1>
  <p>Bunch of awesome content</p>
</div>
```

之后

```html
<section>
  <h1>Heading</h1>
  <p>Bunch of awesome content</p>
</section>
```

范例2：

之前

```html
<div>
  <h2>Heading</h2>
  <img src="bird.jpg" alt="bird">
</div>
```

之后

```html
<section>
  <h2>Heading</h2>
  <img src="bird.jpg" alt="bird">
</section>
```
