TOPICS: itemscope attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `itemscope`

**`itemscope`** is a boolean [global attribute](/en/webfrontend/HTML_Global_Attributes) that defines
the scope of associated metadata. Specifying the **`itemscope`** attribute for an element creates a
new item, which results in a number of name-value pairs that are associated with the element. A
related attribute, [`itemtype`](/en/webfrontend/itemtype_attribute), is used to specify the valid
URL of a vocabulary (such as schema.org) that describes the item and its
properties context. In each of the following examples, the vocabulary is from schema.org.

Every HTML element may have an `itemscope` attribute specified. An `itemscope` element that does not
have an associated [`itemtype`](/en/webfrontend/itemtype_attribute) must have an associated [`itemref`](/en/webfrontend/itemref_attribute).

!!! warn "Don't try this at home"
    **Note**: Find more about [`itemtype`](/en/webfrontend/itemtype_attribute) attributes at [http://schema.org/Thing](http://schema.org/Thing)

## Simple example

The following example specifies the `itemscope` attribute. The example specifies the [`itemtype`](/en/webfrontend/itemtype_attribute)
as `"http://schema.org/Movie"`, and specifies three related `itemprop` attributes.

```html
<div itemscope itemtype="http://schema.org/Movie">
  <h1 itemprop="name">Avatar</h1>
  <span>Director: <span itemprop="director">James Cameron</span> (born August 16, 1954)</span>
  <span itemprop="genre">Science fiction</span>
  <a href="https://youtu.be/0AY1XIkX7bY" itemprop="trailer">Trailer</a>
</div>
```

Structured data

The following table shows the structured data from the preceding example.

|  |  |  |
| :--- | :--- | :--- |
| Itemtype | Movie | <- |
| itemprop | (itemprop name) | (itemprop value) |
| itemprop | director | James Cameron |
| itemprop | genre | Science Fiction |
| itemprop | name | Avatar |
| itemprop | `https://youtu.be/0AY1XIkX7bY` | Trailer |

### `itemscope` id attributes

When you specify the `itemscope` attribute for an element, a new item is created. The item consists
of a group of name-value pairs. For elements with an `itemscope` attribute and an [`itemtype`](/en/webfrontend/itemtype_attribute)
attribute, you may also specify an id attribute. You can use the [`id`](/en/webfrontend/id_attribute)
attribute to set a global identifier for the new item. A global identifier allows the item to relate
to other items found on pages across the Web.

### Example

There are four `itemscope` attributes in the following example. Each `itemscope` attribute sets
the scope of its corresponding [`itemtype`](/en/webfrontend/itemtype_attribute) attribute.
The itemtypes, Recipe, AggregateRating, and NutritionInformation in the following example are part
of the schema.org structured data for a recipe, as specified by the first itemtype, `http://schema.org/Recipe`.

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

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- Other, microdata related, global attributes:
    - [`itemid`](/en/webfrontend/itemid_attribute)
    - [`itemprop`](/en/webfrontend/itemprop_attribute)
    - [`itemref`](/en/webfrontend/itemref_attribute)
    - [`itemtype`](/en/webfrontend/itemtype_attribute)
