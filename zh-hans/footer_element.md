TOPICS: <footer>
AUTHORS: liutian; sweetliu@mozilla.net; mdn:sweetliu

# `<footer>`

**HTML `<footer>` 元素**表示最近一个章节内容或者根节点（sectioning root ）元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。

|  |  |
| :-- | :-- |
| **内容分类** | 流内容, 可触内容。|
| **允许的内容** | 流内容，但是不能包含`<footer>`或者[`<header>`](/zh-hans/webfrontend/<header>)。|
| **标签省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 任何接收流内容的元素。注意`<footer>`元素必须不能是 [`<address>`](/zh-hans/webfrontend/<address>), [`<header>`](/zh-hans/webfrontend/<header>) 或者另一个`<footer>` 元素的后代元素。|
| **DOM 接口** | `HTMLElement` |

## 属性

该元素仅包含全局属性。

## 使用说明

- `<footer>`元素内的作者信息应包含在[`<address>`](/zh-hans/webfrontend/<address>) 元素中。
- `<footer>`元素不是章节内容，因此在outline中不能包含新的章节。

## 示例

```html
<footer>
  Some copyright info or perhaps some author info for an &lt;article&gt;?
</footer>
```
