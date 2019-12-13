TOPICS: <ol>
        <li>
AUTHORS: Dong WEI; FredWe@mozilla.net; mdn:FredWe
         Wizard; wizardforcel@mozilla.net; mdn:wizardforcel
         李杰华; JoshuaLee@mozilla.net; mdn:JoshuaLee

# `<ol>`

**HTML `<ol>` 元素** 表示多个有序列表项，通常渲染为有带编号的列表。

|  |  |
| :-- | :-- |
| **内容分类** | 流内容, and if the `<ol>` element's children include at least one `<li>` element, palpable content. |
| **允许的内容** | 一个或多个`<li>`元素。这些`<li>`元素可以再包含嵌套的`<ol>`或[`<ul>`](/zh-hans/webfrontend/<ul>)元素。|
| **标签省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父元素** | 任何接受流内容的元素 流内容. |
| **允许的 ARIA 角色** | `directory`, `group`, `listbox`, `menu`, `menubar`, `radiogroup`, `tablist`, `toolbar`, `tree`, `presentation` |
| **DOM 接口** | `HTMLOListElement` |

## 属性

这个元素包含[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).

| 属性 | 描述 |
| :-- | :-- |
| `reversed` | 这个布尔属性规定了列表的条目采用倒序，即最不重要的条目放在列表第一个位置。 |
| `start` | 这是整数属性，规定了列表得条目序号的开始的值。尽管列表条目的序号可能是罗马字母顺序，如 XXXI， 或者字母，这个开始的顺序总是使用数字表示。比如想要元素序号从字母 “C” 开始，使用 `<ol start="3">`。<br>**Note:**<br>这个属性在 HTML4中弃用，但是在 HTML5 中被重新引入。 |
| `type` | 编号类型:<br>'a' 表示小写字母编号；<br>'A' 表示大写字母编号；<br>'i' 表示小写罗马数字编号；<br>'I' 表示大写罗马数字编号；<br>'1' 表示数字编号（默认值）。<br><br>除非在封闭的`<li>`元素中使用不同的type属性，否则类型集将用于整个列表。<br>**Note:**<br>这个属性在 HTML4中弃用，但是在 HTML5 中被重新引入。除非列表中序号很重要（比如，在法律或者技术文件中条目通常被需要所引用），否则请使用 CSS `list-style-type` 属性替代。 |

## 使用说明

- 通常，有序列表条目和它前面的编号一起显示，它的编号可以是任何形式，如数字、字母或者罗马数字，甚至可以是小子弹。而这种样式（小子弹）并没有在 HTML 页面内定义，而是在其关联的 CSS 中，使用了
`list-style-type` 属性。
- HTML 并没有对 `<ol>` 和 [`<ul>`](/zh-hans/webfrontend/<ul>) 元素的深度和反复使用次数（overlap）作出限制。
- `<ol>`和 [`<ul>`](/zh-hans/webfrontend/<ul>) 都是列表项。它们的不同点在于 `<ol>` 元素里条目的顺序是有意义的。 对于该选择哪一个去使用下面有个建议：尝试去更改列表项的顺序，如果其含义改变了，
那么应该使用 `<ol>` 元素，否则使用 [`<ul>`](/zh-hans/webfrontend/<ul>) 更合适。

## `<li>`

**HTML `<li>` 元素** （或称 HTML 列表条目元素） 用于表示列表里的条目。它必须包含在一个父元素里：一个有序列表(`<ol>`)，一个无序列表([`<ul>`](/zh-hans/webfrontend/<ul>))，
或者一个菜单 ([`<menu>`](/zh-hans/webfrontend/<menu>))。在菜单或者无序列表里，列表条目通常用点排列显示；在有序列表里，列表条目通常在左边显示按升序排列的计数，例如数字或者字母。

|  |  |
| :-- | :-- |
| **内容类别** | 无 |
| **允许的内容** | 流式内容 |
| **标签省略** | 如果列表元素的后面紧随另一个 `<li>` 元素，或者它的父元素中没有更多内容，结束标签可以省略。|
| **允许的父元素** | `<ul>`、`<ol>`、 或者 [`<menu>`](/zh-hans/webfrontend/<menu>) 元素。过时的 [`<dir>`](/zh-hans/webfrontend/<dir>) 也可以作为父元素，但是并不提倡。|
| **DOM 接口** | HTMLLIElement |
| **元素类型** | 块级 |

`value`

这个整数型属性表明了本 `<li>` 元素在有序列表 （由 `<ol>` 元素定义）中的序号。本属性值只能用数字，即使列表使用罗马数字或字母来展示。随后的列表条目会从设置的值开始计数。
value 属性对于无序列表 ([`<ul>`](/zh-hans/webfrontend/<ul>)) 或者菜单 ([`<menu>`](/zh-hans/webfrontend/<menu>)) 无效。

## 示例

### 简单示例

```html
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

### 使用 `start` 属性

```html
<ol start="7">
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

### 嵌套列表

```html
<ol>
  <li>first item</li>
  <li>second item      <!-- Look, the closing </li> tag is not placed here! -->
    <ol>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ol>
  </li>                <!-- Here is the closing </li> tag -->
  <li>third item</li>
</ol>
```

### 嵌套 `<ol>` 和 `<ul>`

```html
<ol>
  <li>first item</li>
  <li>second item      <!-- Look, the closing </li> tag is not placed here! -->
    <ul>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ul>
  </li>                <!-- Here is the closing </li> tag -->
  <li>third item</li>
</ol>
```
