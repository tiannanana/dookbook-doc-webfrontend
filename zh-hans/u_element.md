TOPICS: <u>
AUTHORS: Wizard; wizardforcel@mozilla.net; mdn:wizardforcel

# `<u>`

**HTML `<u>` 元素**使文本在其内容的基线下的一行呈现下划线。在HTML5中, 此元素表示具有未标注的文本跨度，显示渲染，非文本注释，例如将文本标记为中文文本中的专有名称(一个正确的中文标记),
或 将文本标记为拼写错误。

!!! warn "Don't try this at home"
    此元素以前在旧版本的HTML中称为“下划线”元素，但有时仍会以这种方式被滥用。要为文本加下划线，您应该应用包含CSS `text-decoration`属性设置为 `underline` 的样式。

|  |  |
| :-- | :-- |
| **内容类别** | 流式内容，短语内容，明显的内容。|
| **允许的内容** | 短语内容 |
| **标签省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 任何接受短语内容的元素。|
| **允许的 ARIA 角色** | 任意 |
| **DOM 接口** | `HTMLElement` Gecko 1.9.2 (Firefox 4) 之前（包含）, Firefox 为这个元素实现了 `HTMLSpanElement`  接口。|

## 属性

这个元素仅包含[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

## 使用说明

就像所有排版元素那样， `<u>` 在 HTML 4 中废弃，但是在 HTML 5 中恢复了一个新的语义，意思是：将文本标记为应用了某种形式的非文本注释。

!!! warn "Don't try this at home"
    提示： 在可能和超链接混淆的地方，避免使用 `<u>`。

## 用例

`<u>`元素的有效用例包括注释拼写错误，应用 [proper name mark](https://zh.wikipedia.org/wiki/proper%20name%20mark) 来表示中文文本中的专有名称以及其他形式的注释。

您不应该使用`<u>`简单地为文字加下划线，或者表示书籍的标题。

### 要考虑使用的其他要素

在大多数情况下，您应该使用`<u>`以外的元素，例如：

- [`<em>`](/zh-hans/webfrontend/<em>) 表示强调重点
- [`<b>`](/zh-hans/webfrontend/<b>) 提示注意文字
- [`<mark>`](/zh-hans/webfrontend/<mark>) 标记关键词或短语
- [`<strong>`](/zh-hans/webfrontend/<strong>) 表明文本具有重要意义
- [`<cite>`](/zh-hans/webfrontend/<cite>) 标记书籍或其他出版物的标题
- [`<i>`](/zh-hans/webfrontend/<i>) 表示西方文本中的技术术语，音译，思想或船名

要提供文本注释（与使用`<u>`创建的非文本注释相对），请使用 [`<ruby>`](/zh-hans/webfrontend/<ruby>) 元素。

要应用带下划线的外观而没有任何语义含义，请使用 `text-decoration` 属性的值 `underline`。

## 示例

### 表示拼写错误

此示例使用`<u>`元素和一些CSS来显示包含拼写错误的段落，其中错误以红色波浪下划线样式表示，这种情况通常用于此目的

HTML

```html
<p>This paragraph includes a <u class="spelling">wrnogly</u>
spelled word.</p>
```

在HTML中，我们看到 `<u>` 使用了一个类 `spelling`，用于表示“wrongly”一词的拼写错误。

```css
u.spelling {
  text-decoration: red wavy underline;
}
```

这个CSS表示当 `<u>` 元素使用类 `spelling` 进行样式化时，它的文本下面应该有一个红色的波浪下划线。这是拼写错误的常见样式。也可以使用另一种常见样式  `red dashed underline`。

### 避免使用 `<u>`

大多数情况下，您实际上不想使用 `<u>`。以下是一些示例，显示在几种情况下您应该做什么。

### 非语义下划线

要在不暗示任何语义含义的情况下为文本加下划线，请使用 [`<span>`](/zh-hans/webfrontend/<span>) 元素并将 `text-decoration` 属性设置为 "underline"，如下所示。

```html
<span class="underline">Today's Special</span>
<br>
Chicken Noodle Soup With Carrots
```

```css
.underline {
  text-decoration: underline;
}
```

### 表示书名

书籍标题应使用 [`<cite>`](/zh-hans/webfrontend/<cite>) 元素而不是 `<u>` 甚至 [`<i>`](/zh-hans/webfrontend/<i>) 来呈现。

```html
<p>The class read <cite>Moby Dick</cite> in the first term.</p>
```

请注意: [`<cite>`](/zh-hans/webfrontend/<cite>) 元素的默认样式会以斜体显示文本。如果您愿意，可以使用CSS覆盖它

```css
cite {
  font-style: normal;
  text-decoration: underline;
}
```
