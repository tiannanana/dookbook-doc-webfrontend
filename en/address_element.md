TOPICS: <address>
AUTHORS: Masahiro Fujimoto; mfujimot@gmail.com; github:mfuji09
         Chris Mills; chrisdavidmills@mozilla.net; mdn:chrisdavidmills
         Karl Stolley; karlstolley@github.com; github:karlstolley
         Sphinx; SphinxKnight@github.com; github:SphinxKnight
         Eric Shepherd; eshepherd@mozilla.com; github:a2sheppy
         Teoli; teoli@mozilla.net; mdn:teoli
         Michael[tm] Smith; mike@w3.org; github:sideshowbarker
         Sebastian Zartner; SebastianZ@github.com; github:SebastianZ
         Jérémie Patonnier; Jeremie@mozilla.net; mdn:Jeremie
         Karen Scarfone; kscarfone@mozilla.net; mdn:kscarfone
         Peter; pwdst@mozilla.net; mdn:pwdst
         Keiichi; ethertank@mozilla.net; mdn:ethertank
         Trevor Hobson; trevorhobson@github.com; github:trevorhobson
         Tetsuharu OHZEKI; saneyuki_s@mozilla.net; mdn:saneyuki_s
         Christian Sonne; cers@mozilla.net; mdn:cers
         Jonathan Wilsson; jwilsson@github.com; github:jwilsson
         Janet Swisher; jmswisher@github.com; github:jmswisher
         Jeremy Keith; adactio@mozilla.net; mdn:adactio

# `<address>`

The **HTML `<address>` element** indicates that the enclosed HTML provides contact information for
a person or people, or for an organization.

The contact information provided by an `<address>` element's contents can take whatever form is
appropriate for the context, and may include any type of contact information that is needed,
such as physical address, URL, email address, phone number, social media handle, geographic coordinates,
and so forth. The `<address>` element should include the name of the person, people, or organization
to which the contact information refers.

`<address>` can be used in a variety of contexts, such as providing a business's contact information
in the page header, or indicating the author of an article by including an `<address>`
element within the [`<article>`](/en/webfrontend/<article>).

|  |  |
| :-- | :-- |
| **Content categories** | Flow content, palpable content. |
| **Permitted content** | Flow content, but with no nested `<address>` element, no heading content ([`<hgroup>`](/en/webfrontend/<hgroup>), [`<h1>`](/en/webfrontend/<h1>), [`<h2>`](/en/webfrontend/<h2>), [`<h3>`](/en/webfrontend/<h3>), [`<h4>`](/en/webfrontend/<h4>), [`<h5>`](/en/webfrontend/<h5>), [`<h6>`](/en/webfrontend/<h6>)), no sectioning content ([`<article>`](/en/webfrontend/<article>), [`<aside>`](/en/webfrontend/<aside>), [`<section>`](/en/webfrontend/<section>), [`<nav>`](/en/webfrontend/<nav>)), and no [`<header>`](/en/webfrontend/<header>) or [`<footer>`](/en/webfrontend/<footer>) element. |
| **Tag omission** | None, both the starting and ending tag are mandatory. |
| **Permitted parents** | Any element that accepts flow content, but always excluding `<address>` elements (according to the logical principle of symmetry, if `<address>` tag, as a parent, can not have nested `<address>` element, then the same `<address>` content can not have `<address>` tag as its parent). |
| **Permitted ARIA roles** | None |
| **DOM interface** | `HTMLElement` Prior to Gecko 2.0 (Firefox 4), Gecko implemented this element using the `HTMLSpanElement` interface |

## Attributes

This element only includes the [global attributes](https://wiki.developer.mozilla.org/en-US/docs/HTML/Global_attributes).

## Usage Notes

- To represent an arbitrary address, one that is not related to the contact information, use a
[`<p>`](/en/webfrontend/<p>) element rather than the `<address>` element.
- This element should not contain more information than the contact information, like a publication
date (which belongs in a [`<time>`](/en/webfrontend/<time>) element).
- Typically an `<address>` element can be placed inside the
[`<footer>`](/en/webfrontend/<footer>) element of the current section, if any.

## Example

This example demonstrates the use of `<address>` to demarcate the contact
information for an article's author.

```html
<address>
    You can contact author at <a href="http://www.somedomain.com/contact">
    www.somedomain.com</a>.<br>
    If you see any bugs, please <a href="mailto:webmaster@somedomain.com">
    contact webmaster</a>.<br>
    You may also want to visit us:<br>
    Mozilla Foundation<br>
    331 E Evelyn Ave<br>
    Mountain View, CA 94041<br>
    USA
</address>
```
