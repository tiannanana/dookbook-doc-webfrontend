TOPICS: <bdo>

# `<bdo>`

**`<bdo>` 元素** (HTML双向覆盖元素)用于覆盖当前文本的朝向，它使得字符按给定的方向排列。

## 属性

这个标签包含 全局属性.

| 属性 | 描述 |
| :-- | :-- |
| `dir` | 这个标签包含文本的文本方向. 属性值可为:<br><br>`ltr`: 从左往右写，与现代汉语的书写习惯相同.<br>`rtl`: 从右往左写，与古代汉语书写习惯相同. |

## 示例

```html
<!-- 改变文本方向 -->
<p>This text will go left to right.</p>
<p><bdo dir="rtl">This text will go right
to left.</bdo></p>
```

## 备注

HTML 4的规范文档中没有描述该元素的事件，它们在XHTML中被添加。这应该是当时的疏忽。
