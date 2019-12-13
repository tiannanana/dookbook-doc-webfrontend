TOPICS: <base>
AUTHORS: Taylor Hunt; tigt@github.com; github:tigt
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Lucas Lombardo; LucasLombardo@github.com; github:LucasLombardo
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Teoli; teoli@mozilla.net; mdn:teoli
         DYM; noformnocontent@mozilla.net; mdn:noformnocontent
         Mary; marymar@mozilla.net; mdn:marymar
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Renoir Boulanger; renoirb@mozilla.net; mdn:renoirb
         sotos; sroskylo@github.com; github:sroskylo
         Joe Medley; jmedley@chromium.org;github:jpmedley
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Rodney Rehm; rodneyrehm@github.com; github:rodneyrehm
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Nickolay Ponomarev; asqueella@gmail.com; github:nickolay
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Masahiko Imanaka; marsf@github.com; github:marsf
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<base>`

The HTML `<base>` element specifies the base URL to use for all relative URLs contained within a
document. There can be only one `<base>` element in a document.

The base URL of a document can be queried from a script using document.baseURI.

|  |  |
| :-- | :-- |
| **Content categories** | Metadata content. |
| **Permitted content** | None, it is an empty element. |
| **Tag omission** | There must be no closing tag. |
| **Permitted parents** | Any [`<head>`](/en/webfrontend/<head>) that doesn't contain any other `<base>` element |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLBaseElement` |

## Attributes

This element's attributes include the [global attributes](/en/webfrontend/HTML_Global_Attributes).

| Attribute | Description |
| :-- | :-- |
| `href` | The base URL to be used throughout the document for relative URL addresses. If this attribute is specified, this element must come before any other elements with attributes whose values are URLs. Absolute and relative URLs are allowed.
| `target` | A name or keyword indicating the default location to display the result when hyperlinks or forms cause navigation, for elements that do not have an explicit target reference. It is a name of, or keyword for, a browsing context (for example: tab, window, or inline frame). The following keywords have special meanings:<br>`_self`: Load the result into the same browsing context as the current one. This value is the default if the attribute is not specified.<br>`_blank`: Load the result into a new unnamed browsing context.<br>`_parent`: Load the result into the parent browsing context of the current one. If there is no parent, this option behaves the same way as _self.<br>`_top`: Load the result into the top-level browsing context (that is, the browsing context that is an ancestor of the current one, and has no parent). If there is no parent, this option behaves the same way as _self. If this attribute is specified, this element must come before any other elements with attributes whose values are URLs. |

## Usage Notes

### Base priority

If multiple `<base>` elements are specified, only the first href and first target value are used;
all others are ignored.

### Anchor elements

Anchor TOPICS within a page, e.g. `<a href="#anchor">anchor</a>`, are resolved by using the base URL
as the reference and trigger an HTTP request to the base URL.

For example, given this base URL:

`<base href="http://www.example.com/">`

... and this anchor:

`<a href="#anchor">Anker</a>`

... the link points to:

`http://www.example.com/#anchor`

### Open Graph

Open Graph meta-TOPICS do not acknowledge the base URL and should always have full URLs. For example:

```html
<meta property='og:image' content='http://example.com/thumbnail.jpg'>
```

## Examples

```html
<base href="http://www.example.com/">
<base target="_blank" href="http://www.example.com/">
```
