TOPICS: <s>
AUTHORS: Wizard; wizardforcel@mozilla.net; mdn:wizardforcel

# `<s>`

**HTML `<s>` 元素** 使用删除线来渲染文本。使用 `<s>` 元素来表示不再相关，或者不再准确的事情。但是当表示文档编辑时，不提倡使用 `<s>`；
为此提倡使用 [`<del>`](/zh-hans/webfrontend/<del>) 和 [`<ins>`](/zh-hans/webfrontend/<ins>) 元素。

|  |  |
| :-- | :-- |
| **内容分类** | 短语内容 or 流式内容 |
| **允许的内容** | 短语内容 |
| **标签省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 任何接受短语内容的元素 |
| **允许的 ARIA 角色** | 任意 |
| **DOM 接口** | `HTMLElement` |

## 属性

这个元素仅仅包含[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)

## 示例

```html
<s>Today's Special: Salmon</s> SOLD OUT<br>
<span style="text-decoration: line-through;">Today's Special:
  Salmon</span> SOLD OUT
```
