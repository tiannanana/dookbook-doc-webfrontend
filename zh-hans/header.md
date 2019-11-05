TOPICS: header web
AUTHORS: Crystal-RainSlide; Crystal-RainSlide@github.com; github:Crystal-RainSlide
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei
         huha; hutuxu@mozilla.net; mdn:hutuxu

# `<header>`

**HTML `<header>` 元素**用于展示介绍性内容，通常包含一组介绍性的或是辅助导航的实用元素。它可能包含一些标题元素，但也可能包含其他元素，比如 Logo、搜索框、作者名称，等等。

|||
| -- | --|
| 内容类型 | Flow content，palpable content。|
| 许可内容 | Flow content，但是不允许 `<header>` 或`<footer>` 成为子元素 |
| 标记省略 | 不允许，开始标签和结束标签都不能省略。|
| 允许的父元素 | 任何接受 flow content 的元素。注意 `<header>` 元素不能作为 `<address>`、`<footer>` 或另一个 `<header>` 元素的子元素。|
| 允许的 ARIA 角色 | `group` ，`presentation` |
| DOM 接口 | HTMLElement |

## 使用提示

`<header>` 元素不是分段内容，因此不会往 大纲 中引入新的段落。也就是说，`<header>` 元素通常用于包含周围部分的标题（`h1` 至 `h6` 元素），但这**不是**必需的。

## 属性

此元素仅拥有 全局属性。

## 示例

### 页面的 Header

```html
<header>
  <h1>主页标题</h1>
  <img src="mdn-logo-sm.png" alt="MDN logo">
</header>
```

### 文章的 Header

```html
<article>
  <header>
    <h2>The Planet Earth</h2>
    <p>Posted on Wednesday, 4 October 2017 by Jane Smith</p>
  </header>
  <p>We live on a planet that's blue and green, with so many things still unseen.</p>
  <p><a href="https://janesmith.com/the-planet-earth/">Continue reading....</a></p>
</article>
```
