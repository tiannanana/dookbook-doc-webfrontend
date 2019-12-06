TOPICS: <bdi>

# `<bdi>`

**HTML `<bdi>` 元素** (双向隔离元素) 会隔离可能以不同方向进行格式化的外部文本。
当不知道是从什么方向嵌入文本，如来自于数据库的文本（有起数据库的文本方向）的时候，该元素是十分有用的。

## 属性

| 属性 | 描述 |
| :-- | :-- |
| `dir` | 如同其他HTML元素一样，它包含全局属性，但是有一些语义上的细微差别：`dir`属性不继承父元素。如果没有设置，默认值即为auto，以便浏览器根据元素内容决定元素内容的方向。 |

## 示例

```html
<p dir="ltr">This arabic word <bdi>ARABIC_PLACEHOLDER</bdi> is automatically displayed right-to-left.</p>
```
