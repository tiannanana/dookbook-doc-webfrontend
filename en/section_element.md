TOPICS: <section>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Jamhur Mustafayev; github@jmstfv.com; github:jmstfv
         Eric Bailey; ericwbailey@github.com; github:ericwbailey
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         wilson-farfetch; wilson-farfetch@github.com; github:wilson-farfetch
         Teoli; teoli@mozilla.net; mdn:teoli
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Scott Isaacman; Popodopolos@mozilla.net; mdn:Popodopolos
         Saurabh / Jsx; jsx@mozilla.net; mdn:jsx
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         MusikAnimal; MusikAnimal@github.com; github:MusikAnimal
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<section>`

The **HTML `<section>` element** represents a standalone section — which doesn't have a more specific
semantic element to represent it — contained within an HTML document. Typically, but not always,
sections have a heading.

As an example, a navigation menu should be wrapped in a [`<nav>`](/en/webfrontend/<nav>) element,
but a list of search results and a map display and its controls don't have specific elements,
and could be put inside a `<section>`.

Note: If the contents of the element would make sense syndicated as a standalone piece, the
[`<article>`](/en/webfrontend/<article>) element may be a better choice.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, Sectioning content, palpable content. |
| **Permitted content** | Flow content. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content. Note that a `<section>` element must not be a descendant of an [`<address>`](/en/webfrontend/<address>) element. |
| **Permitted ARIA roles** | alert, alertdialog, application, banner, complementary, contentinfo, dialog, document, feed, log, main, marquee, navigation, search, status, tabpanel |
| **DOM interface** | `HTMLElement`

## Attributes

This element only includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

## Usage Notes

- Each `<section>` should be identified, typically by including a heading
([`<h1>`](/en/webfrontend/<h1>)-[`<h6>`](/en/webfrontend/<h6>) element)
as a child of the `<section>` element.
- If it makes sense to separately syndicate the content of a `<section>` element,
use an `<article>` element instead.
- Do not use the `<section>` element as a generic container; this is what
[`<div>`]((/en/webfrontend/<div>)) is for,
especially when the sectioning is only for styling purposes. A rule of thumb is that a section should
logically appear in the outline of a document.

## Example

Before

```html
<div>
  <h1>Heading</h1>
  <p>Bunch of awesome content</p>
</div>
```

After

```html
<section>
  <h1>Heading</h1>
  <p>Bunch of awesome content</p>
</section>
```
