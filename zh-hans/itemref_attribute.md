TOPICS: itemref attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `itemref`

**`itemref`** [全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) 不具有 [`itemscope`](/zh-hans/webfrontend/itemscope_attribute)
属性的元素的后代，才可以与具有 `itemref` 的元素关联。`itemref` 提供了元素 `id`（并不是 `itemid`）的列表，并具有文档其它地方的额外属性。

`itemref` 属性只能在指定了 [`itemscope`](/zh-hans/webfrontend/itemscope_attribute) 的元素上指定。

!!! warn "Don't try this at home"
    `注：itemref` 属性并不是 microdata 数据模型的一部分。它仅仅是个语义结构，用于帮助作者向页面添加注解，其中被注解的数据不遵循便利的树结构。例如，它允许作者标记表格中的数据，以便每一列定义一个单独的条目，同时在表格中保留属性。

## 示例

```html
<div itemscope id="amanda" itemref="a b"></div>
<p id="a">Name: <span itemprop="name">Amanda</span> </p>
<div id="b" itemprop="band" itemscope itemref="c"></div>
<div id="c">
    <p>Band: <span itemprop="name">Jazz Band</span> </p>
    <p>Size: <span itemprop="size">12</span> players</p>
</div>
```

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
- 其它 `microdata` 相关的全局属性
  - [`itemid`](/zh-hans/webfrontend/itemid_attribute)
  - [`itemprop`](/zh-hans/webfrontend/itemprop_attribute)
  - [`itemscope`](/zh-hans/webfrontend/itemscope_attribute)
  - [`itemtype`](/zh-hans/webfrontend/itemtype_attribute)
