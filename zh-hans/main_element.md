TOPICS: <main>
TRANSLATION: landmark = 界标
             Skip Navigation = 跳跃导航
             Reader Mode = 阅读器模式
SYNONYM: 阅读模式 = Reader Mode

# HTML 主体元素: `<main>`

HTML `<main>`元素呈现了文档的[`<body>`](/zh-hans/webfrontend/<body>/)或应用的**主体部分**。
主体部分由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。

## `<main>`元数据

| | |
| :-- | :-- |
| **内容类别** | `流内容`, palpable content. |
| **允许内容** | `流内容` |
| **标签省略** | 无; 开始与结束都是强制性.|
| **被允许的父级元素** | 任何支持流内容但可能不是继承元素的元素`<article>`, `<aside>`, `<footer>`, `<header>`, 或`<nav>` |
| **DOM 接口** | `HTMLElement` |

## `<main>`属性

此元素仅包含全局属性。

## 使用说明

这部分内容在文档中应当是**唯一**的，不包含在任何一系列文档中重复的内容，比如侧边栏，导航栏链接，版权信息，网站 Logo，搜索框（除非搜索框为文档的主要功能）。

`<main>`对文档的大纲没有贡献; 也就是说，与诸如[`<body>`](/zh-hans/webfrontend/<body>/)之类的元素，
诸如[`<h2>`](/zh-hans/webfrontend/<h2>/)之类的标题等不同，`<main>`不会影响DOM的页面结构概念。这是严格的信息。

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

## 可访问性

### 界标

`<main>`元素的行为类似于`role="main"`具有**界标**的意义。辅助技术可以使用**界标**来快速*识别*和*导航*到文档的大部分。除非声明有旧版浏览器支持问题，
否则最好使用`<main>`元素而不是声明`role ="main"`。

### 跳跃导航

**跳跃导航**，也称为“*skipnav*”，是一种允许辅助技术用户**快速绕过**大部分重复内容（主导航，信息标语等）的技术。这使用户可以更快地访问页面的主要内容。

在`<main>`元素中添加`id`属性可以使其成为跳跃导航链接的目标。

```html
<body>
  <a href="#main-content">跳跃到主要内容</a>

  <!-- 导航栏和网页页眉内容 -->

  <main id="main-content">
    <!-- 主要网页内容 -->
  </main>
</body>
```

### 阅读器模式

当将内容转换为专门的阅读器视图时，浏览器**阅读器模式**功能会寻找`<main>`元素以及标题和内容分段元素的存在。
