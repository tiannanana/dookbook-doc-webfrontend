TOPICS: <cite>

# `<cite>`

**HTML Citation元素（`<cite>`** 用于描述对引用的创意作品的引用，并且必须包括该作品的标题。 根据与引用元数据有关的适合上下文的约定，引用可以采用缩写形式。

|  |  |
| :-- | :-- |
| **内容分类** | 流程内容，措辞内容，可触知内容. |
| **允许的内容** | 短语内容.|
| **标签遗漏** | 无，开始标签和结束标签都是必需的.|
| **允许的父元素** | 任何接受短语内容的元素.|
| **允许的 ARIA 角色** | 任何 |
| **DOM 接口** | `HTMLElement`直到Gecko 1.9.2（包括Firefox 4），Firefox都为此元素实现了`HTMLSpanElement`接口 |

## Attributes

该元素仅包含[全局属性](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes)。

## Usage Notes

在`<cite>`元素的上下文中，可能被引用的创造性作品可以是例如以下一项：

- 一本书
- 研究论文
- 一篇文章
- 一首诗
- 乐谱
- 一首歌
- 剧本或电影剧本
- 一个电影
- 电视节目
- 一个游戏
- 雕塑
- 一幅画
- 戏剧制作
- 一出戏
- 一部歌剧
- 音乐剧
- 展览
- 法律案件报告
- 计算机程序
- 网站
- 网页
- 博客文章或评论
- 论坛帖子或评论
- 一条推文
- 脸书贴
- 书面或口头陈述
- 等等。

值得注意的是，W3C规范指出，对包含在`<cite>`元素中的创意作品的引用可能包含作品作者的姓名。 但是，针对`<cite>`的WHATWG规范却相反：在任何情况下都绝不能包含一个人的名字。

要包含对引用的材料来源的引用，该引用内容包含在[`<blockquote>`](/zh-hans/webfrontend/<blockquote>)或[`<q>`](/zh-hans/webfrontend/<q>)元素中，请在元素上使用cite属性。

通常，浏览器默认情况下会以斜体样式设置`<cite>`元素的内容。 为了避免这种情况，请将CSS`font-style`属性应用于`<cite>`元素。

## 示例

```html
<p>More information can be found in <cite>ISO-0000]</cite>.</p>
```
