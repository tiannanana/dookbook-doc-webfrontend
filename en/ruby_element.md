TOPICS: <ruby>
        <rp>
        <rt>
        <rb>
        <rtc>
AUTHORS: ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Anton Ingfors; antoningfors@github.com; github:antoningfors
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Andrew Pfeiffer; Andrew_Pfeiffer@mozilla.net; mdn:Andrew_Pfeiffer
         Makoto Kato; mkato@mozilla.net; mdn:mkato
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Ali; alispivak@mozilla.net; mdn:alispivak
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Onur Avsar; avsaro@mozilla.net; mdn:avsaro
         Towkir Ahmed; towkir17@mozilla.net; mdn:towkir17
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         ExE Boss; ExE-Boss@github.com; github:ExE-Boss
         Aleksey Shvayka; shvaikalesh@mozilla.net; mdn:shvaikalesh
         Inkbug; Inkbug@github.com; github:Inkbug

# `<ruby>`

The **HTML `<ruby>` element** represents a ruby annotation. Ruby annotations are for showing
pronunciation of East Asian characters.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content.|
| **Permitted content** | Phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` |

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes)

## `<rp>`

The **HTML Ruby Fallback Parenthesis (`<rp>)` element** is used to provide fall-back parentheses for
browsers that do not support display of ruby annotations using the `<ruby>` element. One `<rp>`
element should enclose each of the opening and closing parentheses that wrap the `<rt>` element
that contains the annotation's text.

|  |  |
| :-- | :-- |
| **Content categories** | None. |
| **Permitted content** | Text |
| **Tag omission** | The end tag can be omitted if the element is immediately followed by an `<rt>` or another `<rp>` element, or if there is no more content in the parent element. |
| **Permitted parents** | A `<ruby>` element. `<rp>` must be positioned immediately before or after an `<rt>` element. |
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` |

Usage Notes

Ruby annotations are for showing pronunciation of East Asian characters, like using Japanese
furigana or Taiwanese bopomofo characters. The `<rp>` element is used in the case of lack of `<ruby>`
element support; the `<rp>` content provides what should be displayed in order to indicate the
presence of a ruby annotation, usually parentheses.

## `<rt>`

The **HTML Ruby Text (`<rt>`) element** specifies the ruby text component of a ruby annotation,
which is used to provide pronunciation, translation, or transliteration information for East Asian
typography. The `<rt>` element must always be contained within a `<ruby>` element.

|  |  |
| :-- | :-- |
| **Content categories** | None. |
| **Permitted content** | Phrasing content.|
| **Tag omission** | The end tag may be omitted if the `<rt>` element is immediately followed by an `<rt>` or `<rp>` element, or if there is no more content in the parent element|
| **Permitted parents** | A `<ruby>` element.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` |

## `<rb>`

The **HTML Ruby Base (`<rb>`) element** is used to delimit the base text component of a  `<ruby>`
annotation, i.e. the text that is being annotated. One `<rb>` element should wrap each separate
atomic segment of the base text.

|  |  |
| :-- | :-- |
| **Content categories** | None. |
| **Permitted content** | As a child of a `<ruby>` element.|
| **Tag omission** | The end tag can be omitted if the element is immediately followed by an `<rt>`, `<rtc>`, or `<rp>` element or another `<rb>` element, or if there is no more content in the parent element. |
| **Permitted parents** | A `<ruby>` element. |
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` |

Usage Notes

- Ruby annotations are for showing pronunciation of East Asian characters, like using Japanese
furigana or Taiwanese bopomofo characters. The `<rb>` element is used to separate out each segment
of the ruby base text.
- Even thought `<rb>` is not an empty element, it is common to just include the opening tag of each
element in the source code, so that the ruby markup is less complex and easier to read. The browser
can then fill in the full element in the rendered version.
- You need to include one `<rt>` element for each base segment/`<rb>` element that you want to annotate.

## `<rtc>`

The HTML Ruby Text Container (`<rtc>`) element embraces semantic annotations of characters
presented in a ruby of `<rb>` elements used inside of `<ruby>` element. `<rb>` elements can have
both pronunciation (`<rt>`) and semantic (`<rtc>`) annotations.

|  |  |
| :-- | :-- |
| **Content categories** | None.
| **Permitted content** | Phrasing content or `<rt>` elements.
| **Tag omission** | The closing tag can be omitted if it is immediately followed by a `<rb>`, `<rtc>`
or `<rt>` element opening tag or by its parent closing tag. |
| **Permitted parents** | A `<ruby>` element. |
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` |

## Example

### `<rp>`、`<rt>` Example

```html
<ruby>
  漢 <rp>(</rp><rt>Kan</rt><rp>)</rp>
  字 <rp>(</rp><rt>ji</rt><rp>)</rp>
</ruby>
```

### `<rb>` Example

```html
<ruby>
  <rb>漢<rb>字
  <rp>(</rp><rt>kan<rt>ji<rp>)</rp>
</ruby>
```

### `<rbc>` Example

```html
<div class="info">
  <ruby>
    <rbc>
      <rb>旧</rb><rt>jiù</rt>
      <rb>金</rb><rt>jīn</rt>
      <rb>山</rb><rt>shān</rt>
    </rbc>
    <rtc>San Francisco</rtc>
  </ruby>
</div>
```
