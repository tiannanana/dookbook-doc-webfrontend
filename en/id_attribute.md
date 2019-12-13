TOPICS: id attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `id`

The **`id`** [global attribute](/en/webfrontend/HTML_Global_Attributes) defines an identifier (ID)
which must be unique in the whole document. Its purpose is to identify the element when linking
(using a fragment identifier), scripting, or styling (with CSS).

!!! error ""
    This attribute's value is an opaque string: this means that web authors must not use it to convey
    human-readable information.

`id`'s value must not contain [[whitespace]] (spaces, tabs etc.). Browsers treat non-conforming IDs that
contain whitespace as if the whitespace is part of the ID. In contrast to the `class` attribute,
which allows space-separated values, elements can only have one single ID value.

!!! warn "Don't try this at home"
    **Note**: Using characters except [[ASCII]] letters, digits, `'_'`, `'-'` and `'.'` may cause compatibility
    problems, as they weren't allowed in HTML 4. Though this restriction has been lifted in [[HTML5]],
    an ID should start with a letter for compatibility.

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- [`Element.id`](/en/webfrontend/Element.id) that reflects this attribute.
