TOPICS: <cite>

# `<cite>`

The **HTML Citation element (`<cite>`)** is used to describe a reference to a cited creative work,
and must include the title of that work. The reference may be in an abbreviated form according to
context-appropriate conventions related to citation metadata.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content. |
| **Permitted content** | Phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` Up to Gecko 1.9.2 (Firefox 4) inclusive, Firefox implements the `HTMLSpanElement` interface for this element.

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

## Usage Notes

In the context of the `<cite>` element, a creative work that might be cited could be, for example,
one of the following:

- A book
- A research paper
- An essay
- A poem
- A musical score
- A song
- A play or film script
- A film
- A television show
- A game
- A sculpture
- A painting
- A theatrical production
- A play
- An opera
- A musical
- An exhibition
- A legal case report
- A computer program
- A web site
- A web page
- A blog post or comment
- A forum post or comment
- A tweet
- A Facebook post
- A written or oral statement
- And so forth.

It's worth noting that the W3C specification says that a reference to a creative work, as included
within a `<cite>` element, may include the name of the work’s author. However,
the WHATWG specification for `<cite>` says the opposite: that a person’s name must never be included,
under any circumstances.

To include a reference to the source of quoted material which is contained within a
[`<blockquote>`](/en/webfrontend/<blockquote>) or [`<q>`](/en/webfrontend/<q>) element,
use the `cite` attribute on the element.

Typically, browsers style the contents of a `<cite>` element in italics by default. To avoid this,
apply the CSS `font-style` property to the `<cite>` element.

## Example

```html
<p>More information can be found in <cite>ISO-0000]</cite>.</p>
```
