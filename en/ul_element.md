TOPICS: <ul>
        <li>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         ExE-Boss; ExE-Boss@mozilla.net; mdn:ExE-Boss
         Tzu-Hsuan (TH) Huang; thhuang@github.com; github:thhuang
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Ian Gall; ianpgall@mozilla.net; mdn:ianpgall
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Stanciu Andreea-Diana; AndreeaStanciu@mozilla.net; mdn:AndreeaStanciu
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Jongryul Yang; urty5656@gmail.com; github:alattalatta
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Christian Sonne; cers@mozilla.net; mdn:cers
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<ul>`

The **HTML `<ul>` element** represents an unordered list of items, typically rendered as a bulleted list.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, and if the `<ul>` element's children include at least one `<li>` element, Palpable content.
| **Permitted content** | zero or more `<li>` elements, which in turn often contain nested [`<ol>`](/en/webfrontend/<ol>) or `<ul>` elements.
| **Tag omission** | None, both the starting and ending tag are mandatory.
| **Permitted parents** | Any element that accepts flow content.
| **Permitted ARIA roles** | `directory`, `group`, `listbox`, `menu`, `menubar`, `radiogroup`, `tablist`, `toolbar`, `tree`, `presentation` |
| **DOM interface** | `HTMLUListElement` |

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `compact` | This Boolean attribute hints that the list should be rendered in a compact style. The interpretation of this attribute depends on the user agent and it doesn't work in all browsers.<br>**Usage note:** Do not use this attribute, as it has been deprecated: the `<ul>` element should be styled using CSS. To give a similar effect as the `compact` attribute, the CSS property `line-height` can be used with a value of 80%.
| `type` | Used to set the bullet style for the list. The values defined under HTML3.2 and the transitional version of HTML 4.0/4.01 are:<br>1. `circle`,<br>2. `disc`,<br>3. and `square`

A fourth bullet type has been defined in the WebTV interface, but not all browsers support it: `triangle`.

If not present and if no CSS `list-style-type` property does apply to the element,
the user agent decide to use a kind of bullets depending on the nesting level of the list.

!!! warn "Don't try this at home"
    Usage note: Do not use this attribute, as it has been deprecated; use the CSS
    `list-style-type` property instead.

## Usage Notes

- The `<ul>` element is for grouping a collection of items that do not have a numerical ordering,
and their order in the list is meaningless. Typically, unordered-list items are displayed with a
bullet, which can be of several forms, like a dot, a circle or a squared. The bullet style is
not defined in the HTML description of the page, but in its associated CSS,
using the list-style-type property.
- There is no limitation to the depth and alternation of nested lists defined with the [`<ol>`](/en/webfrontend/<ol>)
and `<ul>` elements.
- The [`<ol>`](/en/webfrontend/<ol>) and `<ul>` elements both represent a list of items.
They differ in that, with the [`<ol>`](/en/webfrontend/<ol>) element, the order is meaningful.
As a rule of thumb to determine which one to use,
try changing the order of the list items; if the meaning is changed,
the [`<ol>`](/en/webfrontend/<ol>) element should be used, otherwise you can use `<ul>`.

## `<li>`

The **HTML `<li>` element** is used to represent an item in a list. It must be contained in a
parent element: an ordered list ([`<ol>`](/en/webfrontend/<ol>)), an unordered list (`<ul>`), or a menu
([`<menu>`](/en/webfrontend/<menu>)). In menus and unordered lists,
list items are usually displayed using bullet points.
In ordered lists, they are usually displayed with an ascending counter on the left,
such as a number or letter.

|  |  |
| :-- | :-- |
| **Content categories** | None. |
| **Permitted content** | Flow content. |
| **Tag omission** | The end tag can be omitted if the list item is immediately followed by another `<li>` element, or if there is no more content in its parent element. |
| **Permitted parents** | An `<ul>`, [`<ol>`](/en/webfrontend/<ol>), or [`<menu>`](/en/webfrontend/<menu>) element. Though not a conforming usage, the obsolete [`<dir>`](/en/webfrontend/<dir>) can also be a parent. |
| **Permitted ARIA roles** | `menuitem` `menuitemcheckbox`, `menuitemradio`, `option`, `presentation`, `radio`, `separator`, `tab`, `treeitem` |
| **DOM interface** | `HTMLLIElement` |

| Attribute | Description |
| :-- | :-- |
| `value` | This integer attribute indicates the current ordinal value of the list item as defined by the [`<ol>`](/en/webfrontend/<ol>) element. The only allowed value for this attribute is a number, even if the list is displayed with Roman numerals or letters. List items that follow this one continue numbering from the value set. The value attribute has no meaning for unordered lists (`<ul>`) or for menus ([`<menu>`](/en/webfrontend/<menu>)).<br>**Note:** This attribute was deprecated in HTML4, but reintroduced in HTML5.<br>**Note:** Prior to Gecko 9.0, negative values were incorrectly converted to 0. Starting in Gecko 9.0 all integer values are correctly parsed.
| `type` | This character attribute indicates the numbering type:<br>`a`: lowercase letters<br>`A`: uppercase letters<br>`i`: lowercase Roman numerals<br>`I`: uppercase Roman numerals<br>`1`: numbers
  
This type overrides the one used by its parent [`<ol>`](/en/webfrontend/<ol>) element, if any.

!!! warn "Don't try this at home"
    Usage note: This attribute has been deprecated: use the CSS `list-style-type` property instead.

## Examples

### Simple example

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

### Nesting list

```html
<ul>
  <li>first item</li>
  <li>second item
  <!-- Look, the closing </li> tag is not placed here! -->
    <ul>
      <li>second item first subitem</li>
      <li>second item second subitem
      <!-- Same for the second nested unordered list! -->
        <ul>
          <li>second item second subitem first sub-subitem</li>
          <li>second item second subitem second sub-subitem</li>
          <li>second item second subitem third sub-subitem</li>
        </ul>
      </li> <!-- Closing </li> tag for the li that
                  contains the third unordered list -->
      <li>second item third subitem</li>
    </ul>
  <!-- Here is the closing </li> tag -->
  </li>
  <li>third item</li>
</ul>
```

### Nested `<ul>` and `<ol>`

```html
<ul>
  <li>first item</li>
  <li>second item
  <!-- Look, the closing </li> tag is not placed here! -->
    <ol>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ol>
  <!-- Here is the closing </li> tag -->
  </li>
  <li>third item</li>
</ul>
```
