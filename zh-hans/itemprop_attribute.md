TOPICS: itemprop attribute

# HTML 全局属性: `itemprop`

[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) **`itemprop`**被用于向一个物体中添加属性。每一个HTML元素都可以指定一个
`itemprop`属性，一个`itemprop`属性由name-value对组成。每一个键值对称为一个属性，一个元素可以有一个或者多个属性。属性值可以是一个`string`或者一个URL，并且可以和
大部分元素进行组合，包括[`<audio>`](/zh-hans/webfrontend/<audio>)、[`<embed>`](/zh-hans/webfrontend/<embed>)、[`<iframe>`](/zh-hans/webfrontend/<iframe>)、[`<img>`](/zh-hans/webfrontend/<img>)、[`<link>`](/zh-hans/webfrontend/<link>)
[`<object>`](/zh-hans/webfrontend/<object>)、[`<source>`](/zh-hans/webfrontend/<source>)、[`<track>`](/zh-hans/webfrontend/<track>)和[`<video>`](/zh-hans/webfrontend/<video>)。

## 示例

下面的样例展示了一组带有`itemprop`属性的源代码，后面的表格展示了产生的结构化数据。

```html
<div itemscope itemtype ="http://schema.org/Movie">
  <h1 itemprop="name">Avatar</h1>
  <span>Director:
    <span itemprop="director">James Cameron</span>
    (born August 16, 1954)</span>
  <span itemprop="genre">Science fiction</span>
  <a href="../movies/avatar-theatrical-trailer.html"
    itemprop="trailer">Trailer</a>
</div>
```

## 属性

属性拥有的值可能是字符串又或者是URL。当一个字符串值是一个URL的时候，它被用 [`<a>`](/zh-hans/webfrontend/<a>)及它的属性值 `href`、[`<img>`](/zh-hans/webfrontend/<img>)及它的属性值`src`、或者其它被链接到或嵌入外部的资源的元素来表述。

### 值为字符串的三个属性

```html
<div itemscope>
 <p>My name is
   <span itemprop="name">Neil</span>.</p>
 <p>My band is called
   <span itemprop="band">Four Parts Water</span>.</p>
 <p>I am
   <span itemprop="nationality">British</span>.</p>
</div>
```

### 一个属性`image`，其值为URL

```html
<div itemscope>
 <img itemprop="image"
   src="google-logo.png" alt="Google">
</div>
```

当一个字符串值不能令人通俗易懂的时候（e.g.，一个长串的数字和字母），它能被用data元素的value属性表示，用所给元素内容的更易懂的版本（它不是结构化数据的一部分-请看下面的例子）。

### 具有其值为产品ID的属性的项目

ID不是人性化的，所以产品的名字是用的人所能看懂的文字而不是ID。

```html
<h1 itemscope>
 <data itemprop="product-id"
   value="9678AOU879">The Instigator 2000</data>
</h1>
```

对于数字数据，meter 元素及它的 value 属性值能够被用来表述。

### 仪表元素

```html
<div itemscope itemtype="http://schema.org/Product">
 <span itemprop="name">Panasonic White
   60L Refrigerator</span>
 <img src="panasonic-fridge-60l-white.jpg" alt="">
  <div itemprop="aggregateRating"
       itemscope
       itemtype="http://schema.org/AggregateRating">
   <meter itemprop="ratingValue"
     min=0 value=3.5 max=5>Rated 3.5/5</meter>
   (based on <span
     itemprop="reviewCount">11</span>
     customer reviews)
  </div>
</div>
```

与此相类似的，对于日期时间相关的数据，time 元素和他的 datetime 属性值能够被使用表示。

### 具有一个属性“生日”的项目，其值为日期

```html
<div itemscope>
 I was born on <time
   itemprop="birthday"
   datetime="2009-05-10">May 10th 2009</time>.
</div>
```

通过把元素上的 itemscope 属性中声明属性，属性也可以是一个组 name-values 对。每个值既可以是一个字符串又可以是一组 name-values 对（i.e. 一个项）。

### 代表一个人的外部项目，代表乐队的内部项目

```html
<div itemscope>
 <p>Name:
   <span itemprop="name">Amanda</span></p>
 <p>Band:
   <span itemprop="band" itemscope>
     <span itemprop="name">Jazz Band</span>
     (<span itemprop="size">12</span>
     players)</span></p>
</div>
```

上面的外层项有两个属性，“name” 和 “band”。“name” 的值是 “Amanda”, “band” 的值是一个在它右侧的项决定的，它有两个属性，“name” 和 “size”。乐队的
“name” 的值是 “Jazz Band”，“size” 的值是 “12”。这个例子的外层项是顶级微数据标签。不是其他项的项被称为顶级微数据项。

### 所有属性与其项目分开

这个样例和之前一个一摸一样，但是所有的属性都被从它们的项中分离了出来。

```html
<div itemscope id="amanda" itemref="a b"></div>
<p id="a">Name:
  <span itemprop="name">Amanda</span></p>
<div id="b"
  itemprop="band"
  itemscope itemref="c"></div>
<div id="c">
 <p>Band:
   <span itemprop="name">Jazz Band</span></p>
 <p>Size:
   <span itemprop="size">12</span> players</p>
</div>
```

这产生了和之前样例相同的结果。第一个项有两个属性，“name“，设置为“Amanda”和“band”，设置到另一个项去了。第二个项有两个更进一步的属性，“name”设置为“Jazz Band”并且“size”设置为“12”。

一个项可以有多个拥有相同名字但是值不同的属性。

### 两种口味的冰淇淋

```html
<div itemscope>
 <p>Flavors in my favorite ice cream:</p>
 <ul>
  <li itemprop="flavor">Lemon sorbet</li>
  <li itemprop="flavor">Apricot sorbet</li>
 </ul>
</div>
```

这产生了一个物体有两个属性,都拥有名字 "flavor" 但是却有不同的值 "Lemon sorbet" 和 "Apricot sorbet"。

为了当一些属性有相同值的时候避免重复，一个介绍一个属性的元素同样可以一次性介绍多个属性。

### 具有两个属性“收藏夹颜色”和“收藏夹水果”的项目都设置为值“橙色”

```html
<div itemscope>
 <span
  itemprop="favorite-color
    favorite-fruit">orange</span>
</div>
```

!!! warn "Don't try this at home"
    注意：微数据和被标记微数据的文档的内容之间是没有关系的。

### 相同的结构化数据以两种不同的方式标记

语义上下面的两个样例没有任何区别。

```html
<figure>
 <img src="castle.jpeg">
 <figcaption><span
   itemscope><span
   itemprop="name">The Castle</span></span>
     (1986)</figcaption>
</figure>
```

```html
<span itemscope><meta
  itemprop="name"
  content="The Castle"></span>
<figure>
 <img src="castle.jpeg">
 <figcaption>The Castle
  (1986)</figcaption>
</figure>
```

两者都是拥有标题的图，并且都同时， 和图完全无关地, 有一个 名字是 "name" 并且值是"The Castle"的键值对的物体项。唯一的区别是如果用户把图片标题拖拽出文档的话，这个项会包含在拖拽的数据中。图像相关的项不会被包括。

## 名字和值

一个属性是一个大小写敏感且展示键值对的包含唯一序列的无序集合。属性的值必须有至少一个序列。下面的这个样例中，每个数据格子都是一个序列。

|  | **itemprop name** | **itemprop value** |
| :--- | :--- | :--- |
| **itemprop** | country | Ireland |
| **itemprop** | Option | 2 |
| **itemprop** | `https://www.flickr.com/photos/nlireland/6992065114` | Ring of Kerry |
| **itemprop** | img | `https://www.flickr.com/photos/nlireland/6992065114/` |
| **itemprop** | website | flickr |
| **itemprop** | (token) | (token) |

**序列**既可以是字符串也可以是URL。如果是一个URL，那么这个项被称为**类型项**。否则它是一个字符串。字符串不能包括句号和冒号（如下）。

1. 如果项是一个类型项它必须满足:
   1. 是一个被定义的属性名
   2. 一个合法的指向语法定义的URL
   3. 一个合法的被用来当作所有权项属性名的URL
2. 如果一个项不是类型项，他必须：
   1. 一个不含 "." (U+002E 句号) 和 ":" (U+003A冒号) 并且被用作一个所有权项的属性名（没有公共规范定义的）

!!! warn "Don't try this at home"
    注意: 上面的规则不允许 ":" 在没有URL的值中 是因为否则它们没法和URL作区分。带有"." 的值被保留作为将来可能的拓展。 空格也不被允许是因为否则值就会被解析为多个序列。

## 值

名称-值对的属性值如以下列表中第一个匹配情况所给定：

1. 如果元素具有`itemscope`属性
   1. 该值是元素创建的**item**。
2. 如果元素是`meta`元素
   1. 该值是元素的`content`属性的值
3. 如果元素是`audio`、`embed`、`iframe`、`img`、`source`、`track`或`video`元素
   1. 该值是生成的URL字符串，它是通过在设置属性时解析元素的`src`属性相对于元素的节点文档（属于Microdata DOM API的一部分）的值而产生的
4. 如果元素是`a`，`area`或`link`元素
   1. 该值是生成的URL字符串，它是通过在设置属性时解析元素的href属性相对于元素的节点文档的值而得到的
5. 如果该元素是一个`object`对象
   1. 该值是生成的URL字符串，它是通过在设置属性时解析元素的data属性相对于元素的节点文档的值而得到的
6. 如果元素是`data`元素
   1. 该值是元素的`value`属性的值
7. 如果元素是一个`meter`元素
   1. 该值是元素的`value`属性的值
8. 如果元素是`time`元素
   1. 该值是元素的`datetime`值

除此以外

- 该值是元素的`textContent`。

如果属性的值为`URL`，则必须使用URL属性元素指定该属性。 URL属性元素是`a`、`area`、`audio`、`embed`、`iframe`、`img`、`link`、`object`、`source`、`track`和`video`元素。

### 名称顺序

名称相对于彼此是无序的，但是如果特定名称具有多个值，则它们确实具有相对顺序。

在下面的示例中，`a`属性的值依次为`1`和`2`，但是`a`属性是否位于`b`属性之前并不重要

```html
<div itemscope>
 <p itemprop="a">1</p>
 <p itemprop="a">2</p>
 <p itemprop="b">test</p>
</div>
```

以下等效

```html
<div itemscope>
 <p itemprop="b">test</p>
 <p itemprop="a">1</p>
 <p itemprop="a">2</p>
</div>
```

如下

```html
<div itemscope>
 <p itemprop="a">1</p>
 <p itemprop="b">test</p>
 <p itemprop="a">2</p>
</div>
```

而以下

```html
<div id="x">
 <p itemprop="a">1</p>
</div>
<div itemscope itemref="x">
 <p itemprop="b">test</p>
 <p itemprop="a">2</p>
</div>
```

### 其他例子

```html
<dl itemscope
  itemtype="http://vocab.example.net/book"
  itemid="urn:isbn:0-330-34032-8">
 <dt>Title
   <dd
    itemprop="title">The Reality Dysfunction
 <dt>Author
   <dd
     itemprop="author">Peter F. Hamilton
 <dt>Publication date
 <dd><time
   itemprop="pubdate"
   datetime="1996-01-26">26 January 1996</time>
</dl>
```

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
- 其它 `microdata` 相关的全局属性
  - [`itemid`](/zh-hans/webfrontend/itemid_attribute)
  - [`itemref`](/zh-hans/webfrontend/itemref_attribute)
  - [`itemscope`](/zh-hans/webfrontend/itemscope_attribute)
  - [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
