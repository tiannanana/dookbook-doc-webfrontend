TOPICS: itemid attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `itemid`

**`itemid`** [全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) 是元素的唯一的全局标识符。`itemid` 属性只能为同时拥有
[`itemscope`](/zh-hans/webfrontend/itemscope_attribute) 和 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
的元素指定。同时，`itemid` 只能为拥有 [`itemscope`](/zh-hans/webfrontend/itemscope_attribute) 的元素指定，它的相应 [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
引用或定义了支持全局标识符的词汇。

[`itemtype`](/zh-hans/webfrontend/itemtype_attribute) 的全局标识符的准确含义，由该标识符以指定的词汇提供。词汇定义了全局标识符相同的多个元素是否
可以共存，并且如果是这样，这些元素如何处理。

!!! warn "Don't try this at home"
    注：Whatwg.org 的定义规定了 `itemid` 必须是 URL。但是，下面的示例正确展示了 URN 也可以使用。这个不一致性可能反映了 Microdata 规范的不完善性。

## 示例

```html
<dl itemscope
    itemtype="http://vocab.example.net/book"
    itemid="urn:isbn:0-330-34032-8">
<dt>Title <dd itemprop="title">The Reality Dysfunction
<dt>Author <dd itemprop="author">Peter F. Hamilton
<dt>Publication date
<dd><time itemprop="pubdate" datetime="1996-01-26">26 January 1996</time> </dl>
```

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
- 其它 `microdata` 相关的全局属性
  - [`itemprop`](/zh-hans/webfrontend/itemprop_attribute)
  - [`itemref`](/zh-hans/webfrontend/itemref_attribute)
  - [`itemscope`](/zh-hans/webfrontend/itemscope_attribute)
  - [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
