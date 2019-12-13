TOPICS: itemid attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `itemid`

The **`itemid`** [global attribute](/en/webfrontend/HTML_Global_Attributes) provides microdata in
the form of a unique, global identifier of an item. An `itemid` attribute can only be specified for an
element that has both [`itemscope`](/en/webfrontend/itemscope_attribute) and [`itemtype`](/en/webfrontend/itemtype_attribute)
attributes. Also, `itemid` can only be specified on
elements that possess an itemscope attribute whose corresponding [`itemtype`](/en/webfrontend/itemtype_attribute)
refers to or defines a vocabulary that supports global identifiers.

The exact meaning of an `itemtype`'s global identifier is provided by the definition of that identifier
within the specified vocabulary. The vocabulary defines whether several items with the same global
identifier can coexist and, if so, how items with the same identifier are handled.

!!! warn "Don't try this at home"
    **Note**: The Whatwg.org definition specifies that an `itemid` must be a URL. However, the following
    example correctly illustrates that a URN may also be used. This inconsistency may reflect the
    incomplete nature of the Microdata specification.

## Example

```html
<dl itemscope
    itemtype="http://vocab.example.net/book"
    itemid="urn:isbn:0-330-34032-8">
<dt>Title <dd itemprop="title">The Reality Dysfunction
<dt>Author <dd itemprop="author">Peter F. Hamilton
<dt>Publication date
<dd><time itemprop="pubdate" datetime="1996-01-26">26 January 1996</time> </dl>
```

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- Other, microdata related, global attributes:
  - [`itemprop`](/en/webfrontend/itemprop_attribute)
  - [`itemref`](/en/webfrontend/itemref_attribute)
  - [`itemscope`](/en/webfrontend/itemscope_attribute)
  - [`itemtype`](/en/webfrontend/itemtype_attribute)
