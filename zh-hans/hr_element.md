TOPICS: <hr>

# `<hr>`

**HTML`<hr>`”元素** 代表了段落级元素之间的主题突破：例如，故事中场景的改变或部分中主题的转移。

从历史上看，这被表示为水平线或水平线。 尽管在视觉浏览器中仍可以将其显示为水平规则，但此元素现在是用语义术语而不是表示性术语定义的，因此，如果要绘制水平线，则应使用适当的CSS。

|  |  |
| :-- | :-- |
| **内容类别** | 流内容。 |
| **允许的内容** | 无，它是一个空元素。 |
| **标签遗漏** | 它必须具有开始标签，但不能具有结束标签。 |
| **允许的父元素** | 接受流内容的任何元素。|
| **允许的 ARIA 角色** | `presentation` |
| **DOM 接口** | `HTMLHRElement` |

## 属性

该元素的属性包括[全局属性](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes)。

| 属性 | 描述 |
| :-- | :-- |
| `align` | 设置页面上规则的对齐方式。 如果未指定任何值，则保留默认值。|
| `color` | 通过颜色名称或十六进制值设置规则的颜色。|
| `noshade` | 将规则设置为无阴影。|
| `size` | 设置规则的高度（以像素为单位）。|
| `width` | 通过像素或百分比值设置页面上规则的长度。|

## 示例

```html
<p>
  This is the first paragraph of text.
  This is the first paragraph of text.
  This is the first paragraph of text.
  This is the first paragraph of text.
</p>

<hr>

<p>
  This is the second paragraph of text.
  This is the second paragraph of text.
  This is the second paragraph of text.
  This is the second paragraph of text.
</p>
```
