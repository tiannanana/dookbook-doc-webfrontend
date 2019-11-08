TOPICS: <main>
        HTML main element
        HTML main tag
        <html> Accessibility Concerns
AUTHORS: Crystal-RainSlide; Crystal-RainSlide@github.com; github:Crystal-RainSlide
         alexanderonepills; alexanderonepills@gmail.com; github:AnePill
         Wang YiMing; wangyimig@icloud.com; github:yuyangzi
         潘韬; pantao@mozilla.net; mdn:pantao
         程成; holynewbie@mozilla.net; mdn:holynewbie

# HTML Main元素

## `<main>`

**HTML `<main>`元素**呈现了文档的[`<body>`](/zh-hans/webfrontend/<body>/)或应用的主体部分。
主体部分由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。

## `<main>`元数据

| | |
| :-- | :-- |
| **内容类别** | Flow content, palpable content. |
| **允许内容** | Flow content.|
| **标签省略** | 无; 开始与结束都是强制性.|
| **被允许的父级元素** | 任何支持流内容但可能不是继承元素的 元素`<article>`, `<aside>`, `<footer>`, `<header>`, 或`<nav>` |
| **DOM 接口** | `HTMLElement` |

## `<main>`属性

此元素仅包含全局属性。

## 使用说明

这部分内容在文档中应当是**独一无二**的，不包含在任何一系列文档中重复的内容，比如侧边栏，导航栏链接，版权信息，网站 Logo，搜索框（除非搜索框为文档的主要功能）。

`<main>`对文档的大纲没有贡献; 也就是说，与诸如[`<body>`](/en/webfrontend/<body>/)之类的元素，诸如`<h2>`之类的标题等不同，
`<main>`不会影响DOM的页面结构概念。这是严格的信息。

## 示例

```html
<!-- 其他内容 -->

<main>
  <h1>Apples</h1>
  <p>The apple is the pomaceous fruit of the apple tree.</p>
  
  <article>
    <h2>Red Delicious</h2>
    <p>These bright red apples are the most common found in many
    supermarkets.</p>
    <p>... </p>
    <p>... </p>
  </article>

  <article>
    <h2>Granny Smith</h2>
    <p>These juicy, green apples make a great filling for
    apple pies.</p>
    <p>... </p>
    <p>... </p>
  </article>

</main>

<!-- 其他内容 -->
```
