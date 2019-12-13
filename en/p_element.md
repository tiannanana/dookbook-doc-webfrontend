TOPICS: <p>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Taylor Hunt; tigt@github.com; github:tigt
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Bailey; ericwbailey@github.com; github:ericwbailey
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Christina; shoelaces@mozilla.net; mdn:shoelaces
         David Ross; bunnybooboo@github.com; github:bunnybooboo
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Pablo Alejandro Fiumara; pablo.fiumara@gmail.com; github:pablofiumara
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Thierry Régagnon; tregagnon@github.com; github:tregagnon
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Florian Scholz; fscholz@mozilla.net; mdn:fscholz

# `<p>`

The **HTML `<p>` element** represents a paragraph. Paragraphs are usually represented in visual
media as blocks of text separated from adjacent blocks by blank lines and/or first-line indentation,
but HTML paragraphs can be any structural grouping of related content, such as images or form fields.

Paragraphs are block-level elements, and notably will automatically close if another
block-level element is parsed before the closing `</p>` tag. See “**Tag omission**” below.

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, palpable content. |
| **Permitted content** | Phrasing content. |
| **Tag omission** | The start tag is required. The end tag may be omitted if the `<p>` element is immediately followed by an [`<address>`](/en/webfrontend/<address>), [`<article>`](/en/webfrontend/<article>), [`<aside>`](/en/webfrontend/<aside>), [`<blockquote>`](/en/webfrontend/<blockquote>), [`<div>`](/en/webfrontend/<div>), [`<dl>`](/en/webfrontend/<dl>), [`<fieldset>`](/en/webfrontend/<fieldset>), [`<footer>`](/en/webfrontend/<footer>), [`<form>`](/en/webfrontend/<form>), [`<h1>`](/en/webfrontend/<h1>), [`<h2>`](/en/webfrontend/<h2>), [`<h3>`](/en/webfrontend/<h3>), [`<h4>`](/en/webfrontend/<h4>), [`<h5>`](/en/webfrontend/<h5>), [`<h6>`](/en/webfrontend/<h6>), [`<header>`](/en/webfrontend/<header>), [`<hr>`](/en/webfrontend/<hr>), [`<menu>`](/en/webfrontend/<menu>), [`<nav>`](/en/webfrontend/<nav>), [`<ol>`](/en/webfrontend/<ol>), [`<pre>`](/en/webfrontend/<pre>), [`<section>`](/en/webfrontend/<section>), [`<table>`](/en/webfrontend/<table>), [`<ul>`](/en/webfrontend/<ul>) or another `<p>` element, or if there is no more content in the parent element and the parent element is not an [`<a>`](/en/webfrontend/<a>) element. |
| **Permitted parents** | Any element that accepts flow content. |
| **Permitted ARIA roles** | Any |
| **DOM interface** | `HTMLParagraphElement` |

## Attributes

This element only includes the [global attributes](/en/webfrontend/HTML_Global_Attributes).

!!! warn "Don't try this at home"
    Note: The `align` attribute on `<p>` TOPICS is obsolete and shouldn't be used.

## Example

```html
<p>This is the first paragraph of text.
  This is the first paragraph of text.
  This is the first paragraph of text.
  This is the first paragraph of text.</p>
<p>This is the second paragraph.
  This is the second paragraph.
  This is the second paragraph.
  This is the second paragraph.</p>
```

## Styling paragraphs

By default, browsers separate paragraphs with a single blank line. Alternate separation methods,
such as first-line indentation, can be achieved with CSS:

```html
<p>Separating paragraphs with blank lines is easiest
for readers to scan, but they can also be separated
by indenting their first lines. This is often used
to take up less space, such as to save paper in print.</p>

<p>Writing that is intended to be edited, such as school
papers and rough drafts, uses both blank lines and
indentation for separation. In finished works, combining
both is considered redundant and amateurish.</p>

<p>In very old writing, paragraphs were separated with a
special character: ¶, the <i>pilcrow</i>. Nowadays, this
is considered claustrophobic and hard to read.</p>

<p>How hard to read? See for yourself:
  <button data-toggle-text="Oh no! Switch back!">Use pilcrow for paragraphs</button>
</p>
```

```css
p {
  margin: 0;
  text-indent: 3ch;
}

p.pilcrow {
  text-indent: 0;
  display: inline;
}

p.pilcrow + p.pilcrow::before {
  content: " ¶ ";
}
```

```javascript
document.querySelector('button').addEventListener('click', function (event) {
  document.querySelectorAll('p').forEach(function (paragraph) {
    paragraph.classList.toggle('pilcrow');
  });
  var newButtonText = event.target.dataset.toggleText;
  var oldText = event.target.innerText;
  event.target.innerText = newButtonText;
  event.target.dataset.toggleText = oldText;
});
```

## Accessibility Concerns

Breaking up content into paragraphs helps make a page more accessible. Screen-readers and other
assistive technology provide shortcuts to let their users skip to the next or previous paragraph,
letting them skim content like how white space lets visual users skip around.

Using empty `<p>` elements to add space between paragraphs is problematic for people who navigate
with screen-reading technology. Screen readers may announce the paragraph's presence, but not any
content contained within it — because there is none. This can confuse and frustrate
the person using the screen reader.

If extra space is desired, use CSS properties like `margin` to create the effect:

```css
p {
  margin-bottom: 2em;/* increase white space after a paragraph */
}
```
