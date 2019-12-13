TOPICS: tabindex attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `tabindex`

The **`tabindex`** [global attribute](/en/webfrontend/HTML_Global_Attributes) indicates that its
element can be focused, and where it participates in sequential keyboard navigation (usually with the
!!!Tab!!! key, hence the name).

It accepts an integer as a value, with different results depending on the integer's value:

- A negative value (usually `tabindex="-1"`) means that the element is not reachable via sequential
keyboard navigation, but could be focused with Javascript or visually. It's mostly useful to create
accessible widgets with JavaScript. You can observe the Tabindex Accessibility example below to
clear confusion.

!!! warn "Don't try this at home"
    A negative value is useful when you have off-screen content that appears on a specific event. The
    user won't be able to focus any element with a negative `tabindex` using the keyboard, but a script
    can do so by calling the `focus()` method.

- `tabindex="0"` means that the element should be focusable in sequential keyboard navigation, but
its order is defined by the document's source order.

- A positive value means the element should be focusable in sequential keyboard navigation, with its
order defined by the value of the number. That is, `tabindex="4"` is focused before `tabindex="5"`,
but after `tabindex="3"`. If multiple elements share the same positive `tabindex` value, their order
relative to each other follows their position in the document source. The maximum value for `tabindex`
is 32767. If not specified, it takes the default value 0.

!!! error ""
    Avoid using `tabindex` values greater than 0. Doing so makes it difficult for people who rely on
    assistive technology to navigate and operate page content. Instead, write the document with the
    elements in a logical sequence.

If you set the `tabindex` attribute on a [`<div>`](/en/webfrontend/<div>), then its child content
cannot be scrolled with the arrow keys unless you set `tabindex` on the content, too.
[Check out this fiddle to understand the scrolling effects of `tabindex`](https://jsfiddle.net/jainakshay/0b2q4Lgv/).

## Tabindex Accessibility

```html
<input type="file"
       id="f-upload"
       tabindex="-1"
       aria-role="button"
       aria-label="Click here to upload a file and view its content" />
<button role="presentation none"><label for="f-upload">Click here to view a file's text content</label></button>
<br />
<textarea id="f-contents" role="textbox" rows="8"></textarea>
```

```css
#f-upload {
    position: fixed;
    visibility: hidden;
}
#f-contents {
    box-sizing: border-box;
    width: 100%;
}
```

```javascript
var fReader = new FileReader(); // used to asynchronously convert blobs into text

var fUploadNode = document.getElementById("f-upload");
fUploadNode.onchange=function(){ fReader.readAsText( fUploadNode.files[0] ); };

var fContentsNode = document.getElementById("f-contents");
fReader.onload=function(){ fContentsNode.value = fReader.result; };
```

([equivalent JSFiddle can be found here if MDN is down](https://jsfiddle.net/7gk4pqwf/3/))

In the above example, you might use a label whose `for` attribute points to a file upload dialog.
You can use `tabindex` to mark the label as focusable so that visual readers can see the selected button,
but use WAI-ARIA to ignore the label and only present the visually-hidden upload button so that the
assistive software can more simply understand that it is a file upload and thus be less prone to
errors or mistakes that might impede the end user.

### Accessibility concerns

Avoid using the `tabindex` attribute in conjunction with non-interactive content to make something
intended to be interactive focusable by keyboard input. An example of this would be using a
[`<div>`](/en/webfrontend/<div>) element to describe a button, instead of the
[`<button>`](/en/webfrontend/<button>) element.

Interactive components authored using non-interactive elements are not be listed in the accessibility
tree. This prevents assistive technology from being able to navigate to and manipulate those components.
The content should be semantically described using interactive elements ([`<a>`](/en/webfrontend/<a>),
[`<button>`](/en/webfrontend/<button>), [`<details>`](/en/webfrontend/<details>),
[`<input>`](/en/webfrontend/<input>), [`<select>`](/en/webfrontend/<select>),
[`<textarea>`](/en/webfrontend/<textarea>), etc.) instead. These elements have built-in roles and
states that communicate status to the accessibility that would otherwise have to be managed by [[ARIA]].

- [Using the tabindex attribute | The Paciello Group](https://developer.paciellogroup.com/blog/2014/08/using-the-tabindex-attribute/)

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- [`HTMLElement.tabIndex`](/en/webfrontend/HTMLElement.tabIndex) that reflects this attribute
- Accessibility problems with tabindex: see [Don’t Use Tabindex Greater than 0](http://adrianroselli.com/2014/11/dont-use-tabindex-greater-than-0.html)
by Adrian Roselli
