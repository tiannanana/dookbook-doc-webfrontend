TOPICS: <label>
AUTHORS: Greg Price; gnprice@github.com; github:gnprice
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Foluso; Foluso@mozilla.net; mdn:Foluso
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Bailey; ericwbailey@github.com; github:ericwbailey
         Roger Pence; roger.pence@gmail.com; github:rogerpence
         Bradley Flood; bradleyflood@github.com; github:bradleyflood
         Teoli; teoli@mozilla.net; mdn:teoli
         David Ross; bunnybooboo@github.com; github:bunnybooboo
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Javier Sánchez Mendoza; javier1nc@github.com; github:javier1nc
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Oleg Torbasow; torbasow@mozilla.net; mdn:torbasow
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Tom; tshinnic@mozilla.net; mdn:tshinnic
         Viktor Zozuliak; zuzusik@mozilla.net; mdn:zuzusik
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson

# `<label>`

The **HTML `<label>` element** represents a caption for an item in a user interface.

Associating a `<label>` with an [`<input>`](/en/webfrontend/<input>) element offers some major advantages:

- The label text is not only visually associated with its corresponding text input;
it is programmatically associated with it too. This means that, for example, a screenreader will
read out the label when the user is focused on the form input, making it easier for an assistive
technology user to understand what data should be entered.
- You can click the associated label to focus/activate the input, as well as the input itself.
This increased hit area provides an advantage to anyone trying to activate the input, including
those using a touch-screen device.

To associate the `<label>` with an [`<input>`](/en/webfrontend/<input>) element, you need to give the
[`<input>`](/en/webfrontend/<input>) an id attribute. The `<label>` then needs a for attribute whose
value is the same as the input's id.

Alternatively, you can nest the [`<input>`](/en/webfrontend/<input>) directly inside the `<label>`,
in which case the for and id attributes are not needed because the association is implicit:

```html
<label>Do you like peas?
  <input type="checkbox" name="peas">
</label>
```

Other Usage Notes:

- The form control that the label is labeling is called the labeled control of the label element.
One input can be associated with multiple labels.
- Labels are not themselves directly associated with forms. They are only indirectly associated
with forms through the controls with which they're associated.
- When a `<label>` is clicked or tapped and it is associated with a form control, the resulting
click event is also raised for the associated control.

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `for` | The id of a labelable form-related element in the same document as the `<label>` element. The first element in the document with an id matching the value of the for attribute is the labeled control for this label element, if it is a labelable element. If it is not labelable then the for attribute has no effect. If there are other elements which also match the id value, later in the document, they are not considered.<br>**Note:** A `<label>` element can have both a for attribute and a contained control element, as long as the for attribute points to the contained control element.
| `form` | The [`<form>`](/en/webfrontend/<form>) element with which the label is associated (its form owner). If specified, the value of the attribute is the id of a [`<form>`](/en/webfrontend/<form>)  element in the same document. This lets you place label elements anywhere within a document, not just as descendants of their form elements.

## Styling with CSS

There are no special styling considerations for `<label>` elements — structurally they are simple
inline elements, and so can be styled in much the same way as a [`<span>`](/en/webfrontend/<span>) or
[`<a>`](/en/webfrontend/<a>) element. You can apply styling to them in any way you want,
as long as you don't cause the text to become difficult to read.

## Examples

### Simple label example

```html
<label>Click me <input type="text"></label>
```

**Using the "for" attribute**:

```html
<label for="username">Click me</label>
<input type="text" id="username">
```

## Accessibility Concerns

### Interactive content

Don't place interactive elements such as anchors or buttons inside a `label`.
Doing so makes it difficult for people to activate the form input associated with the `label`.

Don't

```html
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions">
  I agree to the <a href="terms-and-conditions.html">Terms and Conditions</a>
</label>
```

Do

```html
<label for="tac">
  <input id="tac" type="checkbox" name="terms-and-conditions">
  I agree to the Terms and Conditions
</label>
<p>
  <a href="terms-and-conditions.html">Read our Terms and Conditions</a>
</p>
```

### Headings

Placing heading elements within a `<label>` interferes with many kinds of assistive technology,
because headings are commonly used as a navigation aid. If the label's text needs to be
adjusted visually, use CSS classes applied to the `<label>` element instead.

If a form, or a section of a form needs a title, use the [`<legend>`](/en/webfrontend/<legend>)
element placed within a [`<fieldset>`](/en/webfrontend/<fieldset>).

Don't

```html
<label for="your-name">
  <h3>Your name</h3>
  <input id="your-name" name="your-name" type="text">
</label>
```

Do

```html
<label class="large-label" for="your-name">
  Your name
  <input id="your-name" name="your-name" type="text">
</label>
```

### Buttons

An [`<input>`](/en/webfrontend/<input>) element with a `type="button"` declaration and a valid `value`
attribute does not need a label associated with it. Doing so may actually interfere with how assistive
technology parses the button input. The same applies for the [`<button>`](/en/webfrontend/<button>) element.

## Technical Summary

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, interactive content, form-associated element, palpable content.|
| **Permitted content** | Phrasing content, but no descendant label elements. No labelable elements other than the labeled control are allowed.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLLabelElement` |
