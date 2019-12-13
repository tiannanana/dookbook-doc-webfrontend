TOPICS: <textarea>

# `<textarea>`

The HTML `<textarea>` element represents a multi-line plain-text editing control, useful when you
want to allow users to enter a sizeable amount of free-form text, for example a comment on a
review or feedback form.

The above examples demonstrate a number of features of `<textarea>`. The first example shows the
most simple usage, with only an id attribute to allow the `<textarea>` to be associated with a [`<label>`](/en/webfrontend/<label>)
element for accessibility purposes, and a name attribute to set the name of the associated data point
submitted to the server when the form is submitted.

The second example show some more complex features:

- The `rows` and cols attributes allow you to specify an exact size for the `<textarea>` to take.
Setting these is a good idea for consistency, as browser defaults can differ.
- `maxlength` specifies a maximum number of characters that the `<textarea>` is allowed to contain.
You can also set a minimum length that is considered valid using the `minlength` attribute,
and specify that the `<textarea>` will not submit (and is invalid) if it is empty, using the
`required` attribute. This provides the `<textarea>` with simple validation, which is more basic than
the other form elements (for example, you can't provide specific regexs to validate the value against
using the `pattern` attribute, like you can with the [`<input>`](/en/webfrontend/<input>) element).
- `wrap` specifies the wrapping behavior of the text when it reaches the edge of the `<textarea>`.
- If you want default content for your `<textarea>`, you enter it between the opening and closing
tags. `<textarea>` does not support the `value` attribute.

The `<textarea>` element also accepts several attributes common to form [`<input>`](/en/webfrontend/<input>)s,
such as `autocomplete`, `autofocus`, `disabled`, `placeholder`, `readonly`, and `required`.

## Attributes

This element includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `autocapitalize` | This is a non-standard attribute supported by WebKit on iOS (therefore nearly all browsers running on iOS, including Safari, Firefox, and Chrome), which controls whether and how the text value should be automatically capitalized as it is entered/edited by the user. The non-deprecated values are available in iOS 5 and later. Possible values are:<br>`none`: Completely disables automatic capitalization.<br>`sentences`: Automatically capitalize the first letter of sentences.<br>`words`: Automatically capitalize the first letter of words.<br>`characters`: Automatically capitalize all characters.<br>`on`:  Deprecated since iOS 5.<br>`off`:  Deprecated since iOS 5.
| `autocomplete` | This attribute indicates whether the value of the control can be automatically completed by the browser. Possible values are:<br>`off`: The user must explicitly enter a value into this field for every use, or the document provides its own auto-completion method; the browser does not automatically complete the entry.<br>`on`: The browser can automatically complete the value based on values that the user has entered during previous uses.<br><br>If the autocomplete attribute is not specified on a `<textarea>` element, then the browser uses the autocomplete attribute value of the `<textarea>` element's form owner. The form owner is either the [`<form>`](/en/webfrontend/<form>) element that this `<textarea>` element is a descendant of or the form element whose id is specified by the form attribute of the input element. For more information, see the autocomplete attribute in [`<form>`](/en/webfrontend/<form>).
| `autofocus` | This Boolean attribute lets you specify that a form control should have input focus when the page loads. Only one form-associated element in a document can have this attribute specified.
| `cols` | The visible width of the text control, in average character widths. If it is specified, it must be a positive integer. If it is not specified, the default value is `20`.
| `disabled` | This Boolean attribute indicates that the user cannot interact with the control. If this attribute is not specified, the control inherits its setting from the containing element, for example [`<fieldset>`](/en/webfrontend/<fieldset>); if there is no containing element when the `disabled` attribute is set, the control is enabled.
| `form` | The form element that the `<textarea>` element is associated with (its "form owner"). The value of the attribute must be the id of a form element in the same document. If this attribute is not specified, the `<textarea>` element must be a descendant of a form element. This attribute enables you to place `<textarea>` elements anywhere within a document, not just as descendants of form elements.
| `maxlength` | The maximum number of characters (UTF-16 code units) that the user can enter. If this value isn't specified, the user can enter an unlimited number of characters.
| `minlength` | The minimum number of characters (UTF-16 code units) required that the user should enter.
| `name` | The name of the control.
| `placeholder` | A hint to the user of what can be entered in the control. Carriage returns or line-feeds within the placeholder text must be treated as line breaks when rendering the hint.<br>**Note:** Placeholders should only be used to show an example of the type of data that should be entered into a form; they are not a substitute for a proper [`<label>`](/en/webfrontend/<label>) element tied to the input. See Labels and placeholders in [`<input>`](/en/webfrontend/<input>): The Input (Form Input) element for a full explanation.
| `readonly` | This Boolean attribute indicates that the user cannot modify the value of the control. Unlike the `disabled` attribute, the `readonly` attribute does not prevent the user from clicking or selecting in the control. The value of a read-only control is still submitted with the form.
| `required` | This attribute specifies that the user must fill in a value before submitting a form.
| `rows` | The number of visible text lines for the control.
| `spellcheck` | Specifies whether the `<textarea>` is subject to spell checking by the underlying browser/OS. the value can be:<br>**`true`:** Indicates that the element needs to have its spelling and grammar checked.<br>**`default`:** Indicates that the element is to act according to a default behavior, possibly based on the parent element's own `spellcheck` value.<br>**`false`:** Indicates that the element should not be spell checked.
| `wrap` | Indicates how the control wraps text. Possible values are:<br>**`hard`:** The browser automatically inserts line breaks (CR+LF) so that each line has no more than the width of the control; the `cols` attribute must also be specified for this to take effect.<br>**`soft`:** The browser ensures that all line breaks in the value consist of a CR+LF pair, but does not insert any additional line breaks.<br>**`off`:** Like `soft` but changes appearance to white-space: pre so line segments exceeding `cols` are not wrapped and the `<textarea>` becomes horizontally scrollable.<br>If this attribute is not specified, `soft` is its default value.

## Styling With CSS

`<textarea>` is a replaced element — it has intrinsic dimensions, like a raster image.
By default, its `display` value is block. Compared to other form elements it is relatively
easy to style, with its box model, fonts, color scheme, etc. being easily manipulable using regular CSS.

Styling HTML forms provides some useful tips on styling `<textarea>`s.

### Baseline Inconsistency

The HTML specification doesn't define where the baseline of a `<textarea>` is, so different browsers
set it to different positions. For Gecko, the `<textarea>` baseline is set on the baseline of the
first line of the textarea's first line, on another browser it may be set on the bottom of the
`<textarea>` box. Don't use `vertical-align: baseline` on it; the behavior is unpredictable.

### Controlling Whether a Textarea is Resizable

In most browsers, `<textarea>`s are resizable — you'll notice the drag handle in the right hand
corner, which can be used to alter the size of the element on the page. This is controlled by the
`resize` CSS property — resizing is enabled by default, but you can explicitly disable it using a
`resize` value of `none`:

```css
textarea {
  resize: none;
}
```

### Styling Valid and Invalid Values

Valid and invalid values of a `<textarea>` element (e.g. those within, and outside the bounds
set by `minlength`, `maxlength`, or `required`) can be highlighted using the `:valid` and `:invalid`
pseudo-classes. For example, to give your textarea a different border depending on whether
it is valid or invalid:

```css
textarea:invalid {
  border: 2px dashed red;
}

textarea:valid {
   border: 2px solid lime;
}
```

## Example

### Basic example

The following example show a very simple textarea, with a set numbers of rows and columns and
some default content.

```html
<textarea name="textarea"
   rows="10" cols="50">Write something here</textarea>
```

### Min and Max Length

This example has a minimum and maximum number of characters — of 10 and 20 respectively. Try it and see.

```html
<textarea name="textarea"
   rows="5" cols="30"
   minlength="10" maxlength="20">Write something here</textarea>
```

Note that `minlength` doesn't stop the user from removing characters so that the number entered goes
past the minimum, but it does make the value entered into the `<textarea>` invalid. Also note
that even if you have a `minlength` value set (3, for example), an empty `<textarea>` is still
considered valid unless you also have the `required` attribute set.

### Placeholder

This example has a placeholder set. Notice how it disappears when you start typing into the box.

```html
<textarea name="textarea"
   rows="5" cols="30"
   placeholder="Comment text."></textarea>
```

!!! warn "Don't try this at home"
    Note: Placeholders should only be used to show an example of the type of data that should be
    entered into a form; they are not a substitute for a proper [`<label>`](/en/webfrontend/<label>)
    element tied to the input. See Labels and placeholders in [`<input>`](/en/webfrontend/<input>):
    The Input (Form Input) element for a full explanation.

### Disabled and Readonly

This example shows two `<textarea>`s — one of which is `disabled`, and one of which is `readonly`.
Have a play with both and you'll see the difference in behavior — the `disabled` element is not
selectable in any way (and its value is not submitted), whereas the `readonly` element is selectable
and its contents copyable (and its value is submitted); you just can't edit the contents.

!!! warn "Don't try this at home"
    Note: In browsers other than firefox, such as chrome, the disabled textarea content may be
    selectable and copyable.

```html
<textarea name="textarea"
   rows="5" cols="30"
   disabled>I am a disabled textarea</textarea>
<textarea name="textarea"
   rows="5" cols="30"
   readonly>I am a readonly textarea</textarea>
```

## Technical Summary

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, Interactive content, listed, labelable, resettable, and submittable form-associated element. |
| **Permitted content** | Text |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content. |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLTextAreaElement` |

## See Also

Other form-related elements:

- [`<form>`](/en/webfrontend/<form>)
- [`<button>`](/en/webfrontend/<button>)
- [`<datalist>`](/en/webfrontend/<datalist>)
- [`<legend>`](/en/webfrontend/<legend>)
- [`<label>`](/en/webfrontend/<label>)
- [`<select>`](/en/webfrontend/<select>)
- [`<optgroup>`](/en/webfrontend/<optgroup>)
- [`<option>`](/en/webfrontend/<option>)
- [`<input>`](/en/webfrontend/<input>)
- [`<keygen>`](/en/webfrontend/<keygen>)
- [`<fieldset>`](/en/webfrontend/<fieldset>)
- [`<output>`](/en/webfrontend/<output>)
- [`<progress>`](/en/webfrontend/<progress>)
- [`<meter>`](/en/webfrontend/<meter>)
