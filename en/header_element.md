TOPICS: <header>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Jamhur Mustafayev; github@jmstfv.com; github:jmstfv
         Jonathan Pool; JonathanPool@mozilla.net; mdn:JonathanPool
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Akseli Nurmio; akselinurmio@github.com; github:akselinurmio
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         John Whitlock; John-Whitlock@ieee.org; github:jwhitlock
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Peter; pwdst@mozilla.net; mdn:pwdst
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Christian Sonne; cers@mozilla.net; mdn:cers
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson

# `<header>`

The HTML `<header>` element represents introductory content, typically a group of introductory or
navigational aids. It may contain some heading elements but also a logo,
a search form, an author name, and other elements.

|||
| -- | --|
| ontent categories | Flow content, palpable content.|
| Permitted content | Flow content, but with no `<header>` or `<footer>` descendant.|
| Tag omission | None, both the starting and ending tag are mandatory.|
| Permitted parents | Any element that accepts flow content. Note that a `<header>` element must not be a descendant of an `<address>`, `<footer>` or another `<header>` element.|
| Permitted ARIA roles | `group`, `presentation`|
| DOM interface | `HTMLElement` |

## Usage Notes

The `<header>` element is not sectioning content and therefore does not introduce a new section in
the outline. That said, a `<header>` element is intended to usually contain the surrounding
section's heading (an `h1`–`h6` element), but this is **not** required.

### Historical Usage

Although the `<header>` element didn't make its way into specifications until HTML5, it actually
existed at the very beginning of HTML. As seen in the very first website, it was originally
used as the `<head>` element. At some point, it was decided to use a different name. This allowed
`<header>` to be free to fill a different role later on.

## Attributes

This element only includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

## Examples

### Page Header

```html
<header>
  <h1>Main Page Title</h1>
  <img src="mdn-logo-sm.png" alt="MDN logo">
</header>
```

### Article Header

```html
<article>
  <header>
    <h2>The Planet Earth</h2>
    <p>Posted on Wednesday, <time datetime="2017-10-04">4 October 2017</time> by Jane Smith</p>
  </header>
  <p>We live on a planet that's blue and green, with so many things still unseen.</p>
  <p><a href="https://janesmith.com/the-planet-earth/">Continue reading....</a></p>
</article>
```
