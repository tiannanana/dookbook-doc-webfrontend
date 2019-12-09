TOPICS: <select>
        <option>
        <optgroup>
AUTHORS: Jonathan Pool; JonathanPool@mozilla.net; mdn:JonathanPool
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Kasper; kaspergotcha@mozilla.net; mdn:kaspergotcha
         Taylor Hunt; tigt@github.com; github:tigt
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Rory O’Kane; rory@roryokane.com; github:roryokane
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Teoli; teoli@mozilla.net; mdn:teoli
         Spencer Williams; enderandpeter@mozilla.net; mdn:enderandpeter
         Praveen Puglia; praveenpuglia@mozilla.net; mdn:praveenpuglia
         David Ross; bunnybooboo@github.com; github:bunnybooboo
         John Whitlock; John-Whitlock@ieee.org; github:jwhitlock
         Michiel Renty; mrenty@mozilla.net; mdn:mrenty
         Chris Rebert; cvrebert@mozilla.net; mdn:cvrebert
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Stefan W; Foo@mozilla.net; mdn:Foo
         Tyler Childs; tylerchilds@github.com; github:tylerchilds
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         luke crouch; lcrouch@mozilla.com; github:groovecoder
         Les Orchard; me@lmorchard.com; github:lmorchard
         Patrick Wied; pa7@mozilla.net; mdn:pa7
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Gaurang Patel; g-patel@github.com; github:g-patel
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Akash Agrawal; akagr@outlook.com; github:akagr
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Christian Sonne; cers@mozilla.net; mdn:cers

# `<select>`

The **HTML `<select>` element** represents a control that provides a menu of options:

The above example shows typical `<select>` usage. It is given an `id` attribute to enable it to be
associated with a [`<label>`](/en/webfrontend/<label>) for accessibility purposes, as well as a `name`
attribute to represent the name of the associated data point submitted to the server. Each menu
option is defined by an `<option>` element nested inside the `<select>`.

Each `<option>` element should have a `value` attribute containing the data value to submit to the
server when that option is selected; if no `value` attribute is included, the value defaults to
the text contained inside the element. You can include a `selected` attribute on an `<option>`
element to make it selected by default when the page first loads.

The `<select>` element has some unique attributes you can use to control it, such as `multiple` to
specify whether multiple options can be selected, and `size` to specify how many options should be
shown at once. It also accepts most of the general form input attributes such
as `required`, `disabled`, `autofocus`, etc.

You can further nest `<option>` elements inside `<optgroup>` elements to create
separate groups of options inside the dropdown.

For further examples, see The native form widgets: Drop-down content.

## Technical Summary

|  |  |
| :-- | :-- |
| **Content categories** | flow content, phrasing content, interactive content, listed, labelable, resettable, and submittable form-associated element |
| **Permitted content** | Zero or more `<option>` or `<optgroup>` elements. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | any element that accepts phrasing content |
| **Permitted ARIA roles** | `menu` |
| **DOM interface** | `HTMLSelectElement` |

## Attributes

This element includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

| Attribute | Description |
| :-- | :-- |
| `autocomplete` | A `DOMString` providing a hint for a user agent's autocomplete feature. See The HTML autocomplete attribute for a complete list of values and details on how to use autocomplete.
| `autofocus` | This Boolean attribute lets you specify that a form control should have input focus when the page loads. Only one form element in a document can have the `autofocus` attribute.
| `disabled` | This Boolean attribute indicates that the user cannot interact with the control. If this attribute is not specified, the control inherits its setting from the containing element, for example fieldset; if there is no containing element with the `disabled` attribute set, then the control is enabled.
| `form` | This attribute lets you specify the [`<form>`](/en/webfrontend/<form>) element to which the `<select>` element is associated (that is, its "form owner"). If this attribute is specified, its value must be the same as the `id` of a [`<form>`](/en/webfrontend/<form>) element in the same document. This enables you to place `<select>` elements anywhere within a document, not just as descendants of their [`<form>`](/en/webfrontend/<form>) elements.
| `multiple` | This Boolean attribute indicates that multiple options can be selected in the list. If it is not specified, then only one option can be selected at a time. When `multiple` is specified, most browsers will show a scrolling list box instead of a single line dropdown.
| `name` | This attribute is used to specify the name of the control.
| `required` | A Boolean attribute indicating that an option with a non-empty string value must be selected.
| `size` | If the control is presented as a scrolling list box (e.g. when `multiple` is specified), this attribute represents the number of rows in the list that should be visible at one time. Browsers are not required to present a select element as a scrolled list box. The default value is 0.<br>**Note:** According to the HTML5 specification, the default value for size should be 1; however, in practice, this has been found to break some web sites, and no other browser currently does that, so Mozilla has opted to continue to return 0 for the time being with Firefox.

## Styling With CSS

The `<select>` element is notoriously difficult to style productively with
CSS. You can affect
certain aspects like any element — for example, manipulating the box model,
the displayed font, etc., and you can use the
`appearance` property to remove the default system `appearance`.

However, these properties don't produce a consistent result across browsers, and it is hard to do
things like line different types of form element up with one another in a column. The `<select>`
element's internal structure is complex, and hard to control. If you want to get full control,
you should consider using a library with good facilities for styling form widgets (such as jQuery UI),
or try rolling your own dropdown menu using non-semantic elements, JavaScript,
and WAI-ARIA to provide semantics.

For more useful information on styling `<select>`, see:

- [Styling HTML forms](https://wiki.developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Styling_HTML_forms)
- [Advanced styling for HTML forms](https://wiki.developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Advanced_styling_for_HTML_forms)

## `<option>`

The HTML `<option`> element is used to define an item contained in a `<select>`, an `<optgroup>`,
or a [`<datalist>`](/en/webfrontend/<datalist>) element. As such, `<option>` can represent menu items
in popups and other lists of items in an HTML document.

|  |  |
| :-- | :-- |
| **Content categories** | None.
| **Permitted content** | Text, possibly with escaped characters (like `&eacute;`).
| **Tag omission** | The start tag is mandatory. The end tag is optional if this element is immediately followed by another `<option>` element or an `<optgroup>`, or if the parent element has no more content. |
| **Permitted parents** | A `<select>`, an `<optgroup>` or a [`<datalist>`](/en/webfrontend/<datalist>) element. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLOptionElement` |

| Attribute | Description |
| :-- | :-- |
| `disabled` | If this Boolean attribute is set, this option is not checkable. Often browsers grey out such control and it won't receive any browsing event, like mouse clicks or focus-related ones. If this attribute is not set, the element can still be disabled if one of its ancestors is a disabled `<optgroup>` element.
| `label` | This attribute is text for the `label` indicating the meaning of the option. If the label attribute isn't defined, its value is that of the element text content.
| `selected` | If present, this Boolean attribute indicates that the option is initially selected. If the `<option>` element is the descendant of a `<select>` element whose `multiple` attribute is not set, only one single `<option>` of this `<select>` element may have the `selected` attribute.
| `value` | The content of this attribute represents the value to be submitted with the form, should this option be selected. If this attribute is omitted, the value is taken from the text content of the option element.

## `<optgroup>`

The **HTML `<optgroup>` element** creates a grouping of options within a `<select>` element.

|  |  |
| :-- | :-- |
| **Content categories** | None. |
| **Permitted content** | Zero or more `<option>` elements. |
| **Tag omission** | The start tag is mandatory. The end tag is optional if this element is immediately followed by another `<optgroup>` element, or if the parent element has no more content. |
| **Permitted parents** | A `<select>` element. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLOptGroupElement` |

!!! warn "Don't try this at home"
    Note: Optgroup elements may not be nested.

| Attribute | Description |
| :-- | :-- |
| `disabled` | If this Boolean attribute is set, none of the items in this option group is selectable. Often browsers grey out such control and it won't receive any browsing events, like mouse clicks or focus-related ones.
| `label` | The name of the group of options, which the browser can use when labeling the options in the user interface. This attribute is mandatory if this element is used.

## Examples

### Basic select

```html
<!-- The second value will be selected initially -->
<select name="choice">
  <option value="first">First Value</option>
  <option value="second" selected>Second Value</option>
  <option value="third">Third Value</option>
</select>
```

### Advanced select with multiple features

The follow example is more complex, showing off more features you can use on a `<select>` element:

```html
<label>Please choose one or more pets:
  <select name="pets" multiple size="4">
    <optgroup label="4-legged pets">
      <option value="dog">Dog</option>
      <option value="cat">Cat</option>
      <option value="hamster" disabled>Hamster</option>
    </optgroup>
    <optgroup label="Flying pets">
      <option value="parrot">Parrot</option>
      <option value="macaw">Macaw</option>
      <option value="albatross">Albatross</option>
    </optgroup>
  </select>
</label>
```

We haven't shown this as a live example on the page because it wouldn't display correctly (MDN
currently strips out the `multiple` attribute when rendering the final page); instead you can
view our multiple-select example on GitHub to see how it renders.

You'll see that:

- Multiple options are selectable because we've included the `multiple` attribute.
- The `size` attribute causes only 4 lines to display at a time; you can scroll to view all the options.
- We've included `<optgroup`> elements to divide the options up into different groups. This is a
purely visual grouping, its visualization generally consists of the group name being bolded,
and the options being indented.
- The "Hamster" option includes a `disabled` attribute and therefore can't be selected at all.

### Selecting multiple options

On a desktop computer, there are a number of ways to select multiple options in a `<select>`
element with a `multiple` attribute:

Mouse users can hold the `<kbd>Ctrl</kbd>`, `<kbd>Command</kbd>`, or `<kbd>Shift</kbd>` keys
(depending on what makes sense for your operating system) and then click
multiple options to select/deselect them.

!!! error ""
    Warning: The mechanism for selecting multiple non-contiguous items via the keyboard described below
    currently only seems to work in Firefox. Also note that on macOS, the `<kbd>Ctrl</kbd> + <kbd>Up</kbd>`
    and `<kbd>Ctrl</kbd> + <kbd>Down</kbd>` shortcuts conflict with the OS default shortcuts for Mission
    Control and Application windows, so you'll have to turn these off before it will work.

Keyboard users can select multiple contiguous items by:

- Focusing on the `<select>` element (e.g. using `<kbd>Tab</kbd>`).
- Selecting an item at the top or bottom of the range they want to select using
the `<kbd>Up</kbd>` and `<kbd>Down</kbd>` cursor keys to go up and down the options.
- Holding down the `<kbd>Shift</kbd>` key and then using the `<kbd>Up</kbd>`
and `<kbd>Down</kbd>` cursor keys to increase or decrease the range of items selected.

Keyboard users can select multiple non-contiguous items by:

- Focusing on the `<select>` element (e.g. using `<kbd>Tab</kbd>`).
- Holding down the Ctrl key then using the `<kbd>Up</kbd>` and `<kbd>Down</kbd>` cursor keys to
change the "focused" select option, i.e. the one that will be selected if you choose to do so. The
"focused" select option is highlighted with a dotted outline, in the same way as a keyboard-focused link.
- Pressing `<kbd>Space</kbd>` to select/deselect "focused" select options.
