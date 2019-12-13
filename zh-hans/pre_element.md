TOPICS: <pre>
AUTHORS: xgqfrms; xgqfrms@github.com; github:xgqfrms
         Jiang X.W; jiangseventeen@mozilla.net; mdn:jiangseventeen

# `<pre>`

**HTML `<pre>` 元素**表示预定义格式文本。在该元素中的文本通常按照原文件中的编排，以等宽字体的形式展现出来，文本中的空白符（比如空格和换行符）都会显示出来。(紧跟在 `<pre>` 开始标签后的换行符也会被省略)

!!! warn "Don't try this at home"
    注意： 你需要将该元素里的 '<' 字符转义为 '&lt;' 以保证代码里的关闭代码不被浏览器解释为标签。

|  |  |
| :-- | :-- |
| **内容类别** | 流内容, 可触知的内容.|
| **允许的内容** | 短语内容。 |
| **省略标签** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 任何可以接受流内容的元素 |
| **允许的 ARIA 角色** | 任何 |
| **DOM 接口** | `HTMLPreElement` |

## 属性

这个元素只具有[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

## 示例

```html
<p>Using CSS to change the font color is easy.</p>
<pre>
body {
  color: red;
}
</pre>
```
