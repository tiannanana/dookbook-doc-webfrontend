TOPICS: <u>

# `<u>`

The **HTML Unarticulated Annotation Element (`<u>`)** represents a span of inline text which should
be rendered in a way that indicates that it has a non-textual annotation. This is rendered by
default as a simple solid underline, but may be altered using CSS.

!!! warn "Don't try this at home"
    This element used to be called the "Underline" element in older versions of HTML, and is still
    sometimes misused in this way. To underline text, you should instead apply a style that
    includes the CSS `text-decoration` property set to underline.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content. |
| **Permitted content** | Phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts phrasing content. |
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` |

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

## Usage Notes

Along with other pure styling elements, the original HTML Underline (`<u>`) element was deprecated
in HTML 4; however, `<u>` was restored in HTML 5 with a new, semantic, meaning: to mark text as
having some form of non-textual annotation applied.

!!! warn "Don't try this at home"
    Be careful to avoid using the `<u>` element with its default styling (of underlined text) in
    such a way as to be confused with a hyperlink, which is also underlined by default.

### Use Cases

Valid use cases for the `<u>` element include annotating spelling errors, applying a
proper name mark to denote proper names in Chinese text, and other forms of annotation.

You should not use `<u>` to simply underline text for presentation purposes, or to denote titles of books.

### Other Elements to Consider Using

In most cases, you should use an element other than `<u>`, such as:

- [`<em>`](/en/webfrontend/<em>) to denote stress emphasis
- [`<b>`](/en/webfrontend/<b>)  to draw attention to text
- [`<mark>`](/en/webfrontend/<mark>) to mark key words or phrases
- [`<strong>`](/en/webfrontend/<strong>)  to indicate that text has strong importance
- [`<cite>`](/en/webfrontend/<cite>) to mark the titles of books or other publications
- [`<i>`](/en/webfrontend/<i>) to denote technical terms, transliterations, thoughts,
or names of vessels in Western texts

To provide textual annotations (as opposed to the non-textual annotations created with `<u>`),
use the [`<ruby>`](/en/webfrontend/<ruby>) element.

To apply an underlined appearance without any semantic meaning, use the `text-decoration`
property's value `underline`.

## Examples

### Indicating a Spelling Error

This example uses the `<u>` element and some CSS to display a paragraph which includes a misspelled
error, with the error indicated in the red wavy underline style which is
fairly commonly used for this purpose.

```html
<p>This paragraph includes a <u class="spelling">wrnogly</u>
spelled word.</p>
```

In the HTML, we see the use of `<u>` with a class, `spelling`, which is used to
indicate the misspelling of the word "wrongly".

```css
u.spelling {
  text-decoration: red wavy underline;
}
```

This CSS indicates that when the `<u>` element is styled with the class `spelling`, it should have
a red wavy underline underneath its text. This is a common styling for spelling errors. Another common
style can be presented using `red dashed underline`.

### Avoiding `<u>`

Most of the time, you actually don't want to use `<u>`. Here are some examples that show what you
should do instead in several cases.

### Non-semantic Underlines

To underline text without implying any semantic meaning, use a [`<span>`](/en/webfrontend/<span>)
element with the `text-decoration` property set to `"underline"`, as shown below.

```html
<span class="underline">Today's Special</span>
<br>
Chicken Noodle Soup With Carrots
```

```css
.underline {
  text-decoration: underline;
}
```

### Presenting a Book Title

Book titles should be presented using the [`<cite>`](/en/webfrontend/<cite>) element instead of
`<u>` or even [`<i>`](/en/webfrontend/<i>)

```html
<p>The class read <cite>Moby Dick</cite> in the first term.</p>
```

Note that the default styling for the [`<cite>`](/en/webfrontend/<cite>) element renders the text
in italics. You can, if you wish, override that using CSS:

```css
cite {
  font-style: normal;
  text-decoration: underline;
}
```
