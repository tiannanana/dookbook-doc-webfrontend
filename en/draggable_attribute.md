TOPICS: draggable attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `draggable`

The **`draggable`** [global attribute](/en/webfrontend/HTML_Global_Attributes) is an enumerated
attribute that indicates whether the element can be dragged, either with native browser behavior or
the HTML Drag and Drop API.

`draggable` can have the following values:

- `true`: the element can be dragged.
- `false`: the element cannot be dragged.

!!! error ""
    This attribute is enumerated and not Boolean. A value of `true` or `false` is mandatory, and
    shorthand like `<img draggable>` is forbidden. The correct usage is `<img draggable="false">`.

If this attribute is not set, its default value is `auto`, which means drag behavior is the default
browser behavior: only text selections, images, and links can be dragged. For other elements, the
event [`ondragstart`](/en/webfrontend/ondragstart) must be set for drag and drop to work, as shown
in this comprehensive example.

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
