TOPICS: <ol>
        <li>

# `<ol>`

The HTML `<ol>` element represents an ordered list of items, typically rendered as a numbered list.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, and if the `<ol>` element's children include at least one `<li>` element, palpable content.
| **Permitted content** | Zero or more `<li>` elements, which in turn often contain nested `<ol>` or [`<ul>`](/en/webfrontend/<ul>) elements.
| **Tag omission** | None, both the starting and ending tag are mandatory.
| **Permitted parents** | Any element that accepts flow content.
| **Permitted ARIA roles** | `directory`, `group`, `listbox`, `menu`, `menubar`, `radiogroup`, `tablist`, `toolbar`, `tree`, `presentation` |
| **DOM interface** | `HTMLOListElement` |

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `compact` | This Boolean attribute hints that the list should be rendered in a compact style. The interpretation of this attribute depends on the user agent and it doesn't work in all browsers.<br>**Note:** Do not use this attribute, as it has been deprecated: the `<ol>` element should be styled using CSS. To give an effect similar to the `compact` attribute, the CSS property `line-height` can be used with a value of `80%`.
| `reversed` | This Boolean attribute specifies that the items of the list are specified in reversed order.
| `start` | This integer attribute specifies the start value for numbering the individual list items. Although the ordering type of list elements might be Roman numerals, such as XXXI, or letters, the value of start is always represented as a number. To start numbering elements from the letter "C", use `<ol start="3">`.<br>**Note:** This attribute was deprecated in HTML4, but reintroduced in HTML5.
| `type` | Indicates the numbering type:<br>`'a'` indicates lowercase letters,<br>`'A'` indicates uppercase letters,<br>`'i'` indicates lowercase Roman numerals,<br>`'I'` indicates uppercase Roman numerals,<br>and `'1'` indicates numbers (default).

The type set is used for the entire list unless a different `type` attribute is used within
an enclosed `<li>` element.

!!! warn "Don't try this at home"
    Note: This attribute was deprecated in HTML4, but reintroduced in HTML5.

Unless the value of the list number matters (e.g. in legal or technical documents where items are to
be referenced by their number/letter), the CSS `list-style-type` property should be used instead.

## Usage Notes

- Typically, ordered-list items are displayed with a preceding numbering, which can be of any form,
like numerals, letters or Romans numerals or even simple bullets. This numbered style is not defined
in the HTML description of the page, but in its associated CSS, using the list-style-type property.
- There is no limitation to the depth and alternation of nested lists defined with the `<ol>` and
[`<ul>`](/en/webfrontend/<ul>) elements.
- The `<ol>` and [`<ul>`](/en/webfrontend/<ul>) both represent a list of items.
They differ in the way that,
with the `<ol>` element, the order is meaningful. As a rule of thumb to determine which one to use,
try changing the order of the list items; if the meaning is changed, the `<ol>` element should be used,
else the [`<ul>`](/en/webfrontend/<ul>) is adequate.

## `<li>`

The **HTML `<li>` element** is used to represent an item in a list. It must be contained in a parent
element: an ordered list (`<ol>`), an unordered list ([`<ul>`](/en/webfrontend/<ul>)), or a menu ([`<menu>`](/en/webfrontend/<menu>)).
In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists,
they are usually displayed with an ascending counter on the left, such as a number or letter.

|  |  |
| :-- | :-- |
| **Content categories** | None. |
| **Permitted content** | Flow content. |
| **Tag omission** | The end tag can be omitted if the list item is immediately followed by another `<li>` element, or if there is no more content in its parent element. |
| **Permitted parents** | An [`<ul>`](/en/webfrontend/<ul>), `<ol>`, or [`<menu>`](/en/webfrontend/<menu>) element. Though not a conforming usage, the obsolete [`<dir>`](/en/webfrontend/<dir>) can also be a parent. |
| **Permitted ARIA roles** | `menuitem` `menuitemcheckbox`, `menuitemradio`, `option`, `presentation`, `radio`, `separator`, `tab`, `treeitem` |
| **DOM interface** | `HTMLLIElement` |

| Attribute | Description |
| :-- | :-- |
| `value` | This integer attribute indicates the current ordinal value of the list item as defined by the `<ol>` element. The only allowed value for this attribute is a number, even if the list is displayed with Roman numerals or letters. List items that follow this one continue numbering from the value set. The value attribute has no meaning for unordered lists ([`<ul>`](/en/webfrontend/<ul>)) or for menus ([`<menu>`](/en/webfrontend/<menu>)).<br>**Note:** This attribute was deprecated in HTML4, but reintroduced in HTML5.<br>**Note:** Prior to Gecko 9.0, negative values were incorrectly converted to 0. Starting in Gecko 9.0 all integer values are correctly parsed.
| `type` | This character attribute indicates the numbering type:<br>`a`: lowercase letters<br>`A`: uppercase letters<br>`i`: lowercase Roman numerals<br>`I`: uppercase Roman numerals<br>`1`: numbers
  
This type overrides the one used by its parent `<ol>` element, if any.

!!! warn "Don't try this at home"
    Usage note: This attribute has been deprecated: use the CSS `list-style-type` property instead.

## Examples

For more detailed examples, see the `<ol>` and [`<ul>`](/en/webfrontend/<ul>) pages.

### Ordered list

```html
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

### Ordered list with a custom value

```html
<ol type="I">
  <li value="3">third item</li>
  <li>fourth item</li>
  <li>fifth item</li>
</ol>
```

### Unordered list

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```
