TOPICS: contenteditable attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `contenteditable`

The **`contenteditable`** [global attribute](/en/webfrontend/HTML_Global_Attributes)
is an enumerated attribute indicating if the element should be editable by the user. If so, the
browser modifies its widget to allow editing.

The attribute must take one of the following values:

- `true` or the empty string, which indicates that the element must be editable;
- `false`, which indicates that the element must not be editable.
If this attribute is not set, its default value is inherited from its parent element.

This attribute is an enumerated one and not a Boolean one. This means that the explicit usage of one
of the values `true`, `false` or the empty string is mandatory and that a shorthand like
`<label contenteditable>Example Label</label>` is not allowed. The correct usage is
`<label contenteditable="true">Example Label</label>`.

You can set the color used to draw the text insertion caret with the CSS [`caret-color`](/en/webfrontend/caret-color)
property.

## See also

- [Making content editable](https://wiki.developer.mozilla.org/en-US/docs/Web/Guide/HTML/Editable_content)
- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes)
- [`HTMLElement.contentEditable`](/en/webfrontend/HTMLElement.contentEditable)
and [`HTMLElement.isContentEditable`](/en/webfrontend/HTMLElement.isContentEditable)
- The CSS [`caret-color`](/en/webfrontend/caret-color) property
- [`HTMLElement` `input` event](/en/webfrontend/HTMLElement_input_event)
