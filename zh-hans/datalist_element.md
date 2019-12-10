TOPICS: <datalist>
AUTHORS: Sphinx; SphinxKnight@github.com; github:SphinxKnight
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei

# `<datalist>`

HTML `<datalist>` 元素包含了一组[`<option>`](/zh-hans/webfrontend/<option>)元素，这些元素表示其它表单控件可选值.

|  |  |
| :-- | :-- |
| **内容范畴** | 流内容，段落内容。|
| **允许内容** | 要么 段落内容 要么 0个或多个 [`<option>`](/zh-hans/webfrontend/<option>)元素. |
| **遗漏标签** | 不允许，开始标签和结束标签都不能省略。|
| **允许父级元素** | 任何接受段落内容的元素. |
| **Permitted ARIA roles** | None |
| **DOM接口** | `HTMLDataListElement` |

## 属性

该元素除了公用的全局属性之外，没有其他属性。

## 示例

```html
<label>Choose a browser from this list:
<input list="browsers" name="myBrowser" /></label>
<datalist id="browsers">
  <option value="Chrome">
  <option value="Firefox">
  <option value="Internet Explorer">
  <option value="Opera">
  <option value="Safari">
</datalist>
```
