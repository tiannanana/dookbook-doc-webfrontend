TOPICS: <output>
AUTHORS: King; King.@mozilla.net; mdn:King.

# `<output>`

**HTML `<output>` 标签**表示计算或用户操作的结果。

|  |  |
| :-- | :-- |
| **内容分类** | 流式元素，短语元素，列出的，可标记的，可重置的，与表单相关的元素，可触摸的内容. |
| **允许元素** | 短语元素 |
| **省略标签** | 不允许，开始标签和结束标签都不能省略。|
| **允许父元素** | 接受任何短语元素 |
| **允许ARIA角色** | 任何 |
| **DOM 接口** | `HTMLOutputElement` |

## 属性

这个标签具有[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

| 属性 | 描述 |
| :-- | :-- |
| `for` | 其它影响计算结果的标签的ID，可以多个。 |
| `form` | 与当前标签有关联的form（从属的表单）。该属性的值必须是当前文档内的表单元素的ID。如果未指明该属性，output标签必须是一个form的后代标签。该属性的用处在于可以让output标签脱离form标签，存在于一个网页文档的任意位置。 |
| `name` | name属性。 |

## 示例

```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
    <input type="range" name="b" value="50" /> +
    <input type="number" name="a" value="10" /> =
    <output name="result"></output>
</form>
```
