TOPICS: <em>
AUTHORS: Jongryul Yang; urty5656@gmail.com; github:alattalatta
         Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Yuhei Yasuda; yuhei.yasuda1003@gmail.com; github:yuheiy
         Anton Ingfors; antoningfors@github.com; github:antoningfors
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher

# `<em>`

The **HTML `<em>` element** marks text that has stress emphasis. The `<em>` element can be nested,
with each level of nesting indicating a greater degree of emphasis.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, phrasing content, palpable content.|
| **Permitted content** | Phrasing content.|
| **Tag omission** | None, both the starting and ending tag are mandatory.|
| **Permitted parents** | Any element that accepts phrasing content.|
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLElement` Up to Gecko 1.9.2 (Firefox 4) inclusive, Firefox implements the `HTMLSpanElement` interface for this element.|

## Attributes

This element only includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

## Usage Notes

The `<em>` element is for words that have a stressed emphasis compared to surrounding text,
which is often limited to a word or words of a sentence and affects the meaning of the sentence itself.

Typically this element is displayed in italic type. However, it should not be used simply to apply
italic styling; use the CSS `font-style` property for that purpose. Use the [`<cite>`](/en/webfrontend/<cite>)
element to mark the title of a work (book, play, song, etc.). Use the [`<i>`](/en/webfrontend/<i>)
element to mark text that is in an alternate tone or mood, which covers many common situations for
italics such as scientific names or words in other languages. Use the [`<strong>`](/en/webfrontend/<strong>)
element to mark text that has greater importance than surrounding text.

### `<i>` vs. `<em>`

New developers are often confused at seeing multiple elements that produce similar results.
`<em>` and [`<i>`](/en/webfrontend/<i>) are a common example, since they both italicize text.
What's the difference? Which should you use?

By default, the visual result is the same. However, the semantic meaning is different.
The `<em>` element represents stress emphasis of its contents, while the [`<i>`](/en/webfrontend/<i>)
element represents text that is set off from the normal prose, such a foreign word, fictional
character thoughts, or when the text refers to the definition of a word instead of representing its
semantic meaning. (The title of a work, such as the name of a book or movie, should use [`<cite>`](/en/webfrontend/<cite>).)

This means the right one to use depends on the situation. Neither is for purely decorational purposes,
that's what CSS styling is for.

An example for `<em>` could be: "Just do it already!", or: "We had to do something about it".
A person or software reading the text would pronounce the words in italics with an emphasis,
using verbal stress.

An example for [`<i>`](/en/webfrontend/<i>) could be: "The Queen Mary sailed last night".
Here, there is no added emphasis or importance on the word "Queen Mary". It is merely indicated
that the object in question is not a queen named Mary, but a ship named Queen Mary. Another example
for [`<i>`](/en/webfrontend/<i>) could be: "The word the is an article".

## Example

The `<em>` element is often used to indicate an implicit or explicit contrast.

```html
<p>
  In HTML 5, what was previously called
  <em>block-level</em> content is now called
  <em>flow</em> content.
</p>
```
