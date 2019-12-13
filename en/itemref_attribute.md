TOPICS: itemref attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `itemref`

Properties that are not descendants of an element with the [`itemscope`](/en/webfrontend/itemscope_attribute)
attribute can be associated with an item using the global attribute **`itemref`**.

itemref provides a list of element IDs (not itemids) elsewhere in the document, with additional properties

The itemref attribute can only be specified on elements that have an itemscope attribute specified.

!!! warn "Don't try this at home"
    **Note**: the itemref attribute is not part of the microdata data model. It is merely a syntactic
    construct to aid authors in adding annotations to pages where the data to be annotated does not follow
    a convenient tree structure. For example, it allows authors to mark up data in a table so that each
    column defines a separate item while keeping the properties in the cells.

## Example

```html
<div itemscope id="amanda" itemref="a b"></div>
<p id="a">Name: <span itemprop="name">Amanda</span> </p>
<div id="b" itemprop="band" itemscope itemref="c"></div>
<div id="c">
    <p>Band: <span itemprop="name">Jazz Band</span> </p>
    <p>Size: <span itemprop="size">12</span> players</p>
</div>
```

### Structured data

```json
{
  "@id": "amanda",
  "name": "Amanda",
  "band": {
    "@id": "b",
    "name": "Jazz Band",
    "size": 12
  }
}
```

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- Other, microdata related, global attributes:
  - [`itemid`](/en/webfrontend/itemid_attribute)
  - [`itemprop`](/en/webfrontend/itemprop_attribute)
  - [`itemscope`](/en/webfrontend/itemscope_attribute)
  - [`itemtype`](/en/webfrontend/itemtype_attribute)
