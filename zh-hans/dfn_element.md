TOPICS: <dfn>

# `<dfn>`

HTML Definition元素（`<dfn>`）用于指示在定义短语或句子的上下文中定义的术语。 [`<p>`](/zh-hans/webfrontend/<p>)元素，[`<dt>`](/zh-hans/webfrontend/<dt>)，[`<dd>`](/zh-hans/webfrontend/<dd>)对或`<dfn>`的最接近祖先的[`<section>`](/zh-hans/webfrontend/<section>)元素被视为该术语的定义。

|  |  |
| :-- | :-- |
| **内容分类** | 流程内容，措辞内容，可触知内容. |
| **允许的内容** | 短语内容，但没有`<dfn>`元素必须是后代. |
| **标签遗漏** | 无，开始标签和结束标签都是必需的. |
| **允许的父元素** | 任何接受短语内容的元素. |
| **允许的 ARIA 角色** | 任何 |
| **DOM 接口** | `HTMLElement` |

## 属性

该元素的属性包括[全局属性](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes)。

在HTML5中，`title` 属性具有特殊含义，如下所述。

## 使用说明

使用`<dfn>`元素有一些并不十分明显的方面。 我们在这里检查那些。

### 指定要定义的术语

这些术语的定义遵循以下规则：

- 如果`<dfn>`元素具有标题属性，则将标题属性的值视为正在定义的术语。 元素中仍必须包含文本，但是该文本可以是缩写（也许使用[`<abbr>`](/zh-hans/webfrontend/<abbr>)）或该术语的另一种形式。
- 如果`<dfn>`包含单个子元素并且不具有任何文本内容，并且子元素是具有标题属性的[`<abbr>`](/zh-hans/webfrontend/<abbr>)元素，
则[`<abbr>`](/zh-hans/webfrontend/<abbr>)的确切值 元素的标题是所定义的术语。
- 否则，将定义`<dfn>`元素的文本内容。 这在下面的第一个示例中显示。

!!! warn "Don't try this at home"
    如果`<dfn>`元素具有`title`属性，则它必须包含正在定义的术语，并且不得包含其他文本。

### 链接到`<dfn>`元素

如果在`<dfn>`元素上包含一个`id`属性，则可以使用[`<a>`](/zh-hans/webfrontend/<a>)元素链接到该属性。 此类链接应该是术语的使用，目的是使读者可以通过单击术语的链接来快速导航到该术语的定义（如果他们尚不知道的话）。

这在下面的链接到定义的示例中显示。

- `<dfn>`元素标记正在定义的术语； 该术语的定义应由周围的[`<p>`](/zh-hans/webfrontend/<p>)、[`<section>`](/zh-hans/webfrontend/<section>)或定义列表组（通常是[`<dt>`](/zh-hans/webfrontend/<dt>)、[`<dd>`](/zh-hans/webfrontend/<dd>)对）给出。

- 所定义术语的确切值由以下规则确定：
  1. 如果`<dfn>`元素具有标题属性，则该术语就是该属性的值。
  2. 否则，如果它仅包含具有标题属性的[`<abbr>`](/zh-hans/webfrontend/<abbr>)元素，则该术语就是该属性的值。 这在下面的“一起使用缩写和定义”中得到了证明。
  3. 否则，`<dfn>`元素的文本内容就是所定义的术语.

## 示例

让我们看一下各种使用场景的一些示例.

### 术语的基本识别

本示例仅使用简单的<dfn>元素来标识术语在定义中的位置。

```html
<p>The <strong>HTML Definition element</strong>
(<strong><dfn>&lt;dfn&gt;</dfn></strong>) is used to indicate the
term being defined within the context of a definition phrase or
sentence.</p>
```

由于`<dfn>`元素没有标题，因此`<dfn>`元素本身的文本内容用作要定义的术语。

### 链接到定义

要添加到定义的链接，请使用[`<a>`](/zh-hans/webfrontend/<a>)元素以通常的方式创建链接。

```html
<p>The <strong>HTML Definition element</strong>
(<strong><dfn id="definition-dfn">&lt;dfn&gt;</dfn></strong>) is
used to indicate the term being defined within the context of a
definition phrase or sentence.</p>

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Graece
donan, Latine voluptatem vocant. Confecta res esset. Duo Reges:
constructio interrete. Scrupulum, inquam, abeunti; </p>

<p>Negare non possum. Dat enim intervalla et relaxat. Quonam modo?
Equidem e Cn. Quid de Pythagora? In schola desinis. </p>

<p>Ubi ut eam caperet aut quando? Cur iustitia laudatur? Aperiendum
est igitur, quid sit voluptas; Quid enim? Non est igitur voluptas
bonum. Urgent tamen et nihil remittunt. Quid enim possumus hoc
agere divinius? </p>

<p>Because of all of that, we decided to use the
<code><a href="#definition-dfn">&lt;dfn&gt;</a></code> element for
this project.</p>
```

在这里，我们看到了定义-现在具有`id`属性`"definition-dfn"`，可用作链接的目标。 稍后，使用[`<a>`](/zh-hans/webfrontend/<a>)创建一个链接，并且将href属性设置为`"＃definition-dfn"`以将链接设置回定义。

### 缩写和定义一起使用

在某些情况下，您可能希望在定义术语时使用缩写。 这可以通过同时使用`<dfn>`和[`<abbr>`](/zh-hans/webfrontend/<abbr>)元素来完成，如下所示：

```html
<p>The <dfn><abbr title="Hubble Space Telescope">HST</abbr></dfn>
is among the most productive scientific instruments ever constructed.
It has been in orbit for over 20 years, scanning the sky and
returning data and photographs of unprecedented quality and
detail.</p>

<p>Indeed, the <abbr title="Hubble Space Telescope">HST</abbr> has
arguably done more to advance science than any device ever built.</p>
```

注意嵌套在`<dfn>`内部的[`<abbr>`](/zh-hans/webfrontend/<abbr>)元素。 前者确定该术语为缩写（"HST"），并在其`title`属性中指定完整术语
（"Hubble Space Telescope"）。 后者表示缩写术语代表正在定义的术语。
