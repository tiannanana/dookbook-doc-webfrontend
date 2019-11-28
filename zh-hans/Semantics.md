TOPIC: Semantics

# 语义

在编程中，**语义**指的是一段代码的含义，例如“运行该行JavaScript有什么效果？”或“该HTML元素具有什么目的或作用”（而不是“什么”）。 看起来像吗？”。

## HTML中的语义

例如，在[[HTML]]中，[`<h1>`](/zh-hans/webfrontend/<h1>)元素是一个*语义元素*，它给它所包含的文字赋予“页面中的顶级标题”的**角色**（或**含义**）”。

```html
<h1>这是个顶级标题</h1>
```

默认情况下，大多数浏览器的样式表都将对具有较大字体大小的[`<h1>`](/zh-hans/webfrontend/<h1>)进行样式设置，
使其看起来像标题（尽管您可以将其样式设置为所需的样式）。

另一方面，您可以使任何元素看起来像是顶级标题。考虑如下：

```html
<span style="font-size: 32px; margin: 21px 0;">这个是顶级标题吗？</span>
```

这将使它看起来像顶级标题，但没有语义价值，因此不会获得如上所述的任何额外好处。因此，最好将正确的[[HTML]]元素用于正确的地方。

[[HTML]]应该用作展现数据，而不是基于其默认表示样式。样式（外观）是[[CSS]]的全部责任。

编写语义标记的一些**好处**如下：

- [搜索引擎](/zh-hans/glossary/Search_Engine）会将其内容视为影响页面搜索排名的重要关键字（请参见[[SEO]]）
- 屏幕阅读器可以将其用作路标，以帮助视障用户浏览页面
- 查找有意义的代码块比通过无尽的[`<div>`](/zh-hans/webfrontend/<div>)（带有或不带有语义或命名空间类）搜索要容易得多。
- 向开发人员建议将要填充的数据类型
- 语义命名反映了适当的自定义元素/组件命名

在接近要使用的标记时，问自己：“最能描述哪个元素代表将要填充的数据？” 例如，它是数据列表吗？ 有序，无序？
它是一篇包含各节并附带相关信息的文章吗？ 它列出了定义吗？ 它是需要字幕的图形或图像吗？
除了全局站点范围的页眉和页脚之外，还应该有页眉和页脚吗？ 等等。

## 语义元素

这是大约100种可用的语义[[元素]](/zh-hans/glossary/HTML)中其中的一些：

- [`<article>`](/zh-hans/webfrontend/<article>)
- [`<aside>`](/zh-hans/webfrontend/<aside>)
- [`<details>`](/zh-hans/webfrontend/<details>)
- [`<figcaption>`](/zh-hans/webfrontend/<figcaption>)
- [`<figure>`](/zh-hans/webfrontend/<figure>)
- [`<footer>`](/zh-hans/webfrontend/<footer>)
- [`<header>`](/zh-hans/webfrontend/<header>)
- [`<main>`](/zh-hans/webfrontend/<main>)
- [`<mark>`](/zh-hans/webfrontend/<mark>)
- [`<nav>`](/zh-hans/webfrontend/<nav>)
- [`<section>`](/zh-hans/webfrontend/<section>)
- [`<summary>`](/zh-hans/webfrontend/<summary>)
- [`<time>`](/zh-hans/webfrontend/<time>)

## Semantics in CSS

In [[CSS]], consider styling a list with `li` elements representing different types of
fruits. Would you know what part of the [[DOM]] is being selected with `div > ul > li`, or `.fruits__item`?

## Semantics in JavaScript

In [[JavaScript]], consider a function that takes a string parameter, and returns an
`<li>` element with that string as its `textContent`. Would you need to look at
the code to understand what the function did if it was called `build('Peach')`, or `createLiWithContent('Peach')`?

## 更多

- [如何使用HTML sections and outlines - MDN](https://wiki.developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML_sections_and_outlines#Problems_solved_by_HTML5)
- [Semantics (computer science) - 维基百科](https://en.wikipedia.org/wiki/Semantics#Computer_science)
