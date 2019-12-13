TOPICS: itemscope attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `itemscope`

**`itemscope`** 是一个布尔值的 [全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) 。它定义了一个与元数据关联的数据项。就是说一个
元素的 **`itemscope`** 属性会创建一个项，包含了一组与元素相关的键值对。 相关的属性 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
通常表示表中一个有效的 URL （比如 schema.org） 来表述项目和上下文。下面每个例子中的概念表都来自 schema.org.

每个 HTML 元素都可以有指定的 `itemscope` 属性。一个具有 `itemscope` 属性的元素可以没有关联的 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)，
但必须有相关的 [`itemref`](/zh-hans/webfrontend/itemref_attribute)。

!!! warn "Don't try this at home"
    译者注: Schema.org 提供了一份共享的词汇表，站长可以使用它来标记网页，而这些标记则被主要的搜索引擎： Google， Microsoft， Yandex 和 Yahoo! 所支持。

!!! warn "Don't try this at home"
    提示: 获取更多关于 itemtype 属性的信息：[http://schema.org/Thing](http://schema.org/Thing)

## 简单示例

下面一个例子指定的 `itemscope` 属性，设置了 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute) 为
`"http://schema.org/Movie"`， 并且有3个关联的 [`itemprop`](/zh-hans/webfrontend/itemprop_attribute) 属性（[`name`](/zh-hans/webfrontend/name)、[`director`](/zh-hans/webfrontend/director)、[`genre`](/zh-hans/webfrontend/genre)）。

```html
<div itemscope itemtype ="http://schema.org/Movie">
  <h1 itemprop="name">Avatar</h1>
  <span>Director: <span itemprop="director">James Cameron</span> (born August 16, 1954)</span>
  <span itemprop="genre">Science fiction</span>
  <a href="https://youtu.be/0AY1XIkX7bY" itemprop="trailer">Trailer</a>
</div>
```

结构化数据

下表展示了上面例子当中的结构化数据。

|  |  |  |
| :--- | :--- | :--- |
| Itemtype | Movie | <- |
| itemprop | (itemprop name) | (itemprop value) |
| itemprop | director | James Cameron |
| itemprop | genre | Science Fiction |
| itemprop | name | Avatar |
| itemprop | `https://youtu.be/0AY1XIkX7bY` | Trailer |

## `itemscope` id 属性

当你表述一个元素的 `itemscope` 属性时，就创建了一个新的数据项。数据项包含了一组键值对。如果一个元素包含了 `itemscope` 和 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
属性，你同时也就阐述了一个 [`id`](/zh-hans/webfrontend/id_attribute.md) 属性。你可以用 [`id`](/zh-hans/webfrontend/id_attribute.md)
属性为数据项设置一个全局的身份识别。这样你就可以通过这个识别与页面中其他的数据进行交互。

## 示例

下面示例中有4个 `itemscope` 属性。每一个 `itemscope` 设置了相应的 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
属性。例子中[`itemtype`](/zh-hans/webfrontend/itemtype_attribute)，`Recipe`，`AggregateRating`，以及
`NutritionInformation` 通过指定了 `itemptype`，也就是`“http://schema.org/Recipe”`，也都是 schema.org 提供的一个食谱的结构化数据的一部分。

```html
<div itemscope itemtype="http://schema.org/Recipe">
<h2 itemprop="name">Grandma's Holiday Apple Pie</h2>
<img itemprop="image" src="https://c1.staticflickr.com/1/30/42759561_8631e2f905_n.jpg" width="50" height="50"/>
<p>By <span itemprop="author" itemscope itemtype="http://schema.org/Person">
<span itemprop="name">Carol Smith</p></span>
</span>
<p>Published: <time datetime="2009-11-05" itemprop="datePublished">
November 5, 2009</p></time>
<span itemprop="description">This is my grandmother's apple pie recipe. I like to add a dash of nutmeg.<br></span>
 <span itemprop="aggregateRating" itemscope itemtype="http://schema.org/AggregateRating">
 <span itemprop="ratingValue">4.0</span> stars based on <span itemprop="reviewCount">35</span> reviews<br></span>
Prep time: <time datetime="PT30M" itemprop="prepTime">30 min<br></time>
 Cook time: <time datetime="PT1H" itemprop="cookTime">1 hour<br></time>
 Total time: <time datetime="PT1H30M" itemprop="totalTime">1 hour 30 min<br></time>
 Yield: <span itemprop="recipeYield">1 9" pie (8 servings)<br></span>
 <span itemprop="nutrition" itemscope itemtype="http://schema.org/NutritionInformation">
 Serving size: <span itemprop="servingSize">1 medium slice<br></span>
 Calories per serving: <span itemprop="calories">250 cal<br></span>
 Fat per serving: <span itemprop="fatContent">12 g<br></span>
</span>
<p>Ingredients:<br>
  <span itemprop="recipeIngredient">Thinly-sliced apples: 6 cups<br></span>
  <span itemprop="recipeIngredient">White sugar: 3/4 cup<br></span>
 ... </p>

Directions: <br>
  <div itemprop="recipeInstructions">
    1. Cut and peel apples<br>
    2. Mix sugar and cinnamon. Use additional sugar for tart apples. <br>
    ...
  </div>
</div>
```

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
- 其它 `microdata` 相关的全局属性
    - [`itemid`](/zh-hans/webfrontend/itemid_attribute)
    - [`itemprop`](/zh-hans/webfrontend/itemprop_attribute)
    - [`itemref`](/zh-hans/webfrontend/itemref_attribute)
    - [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
