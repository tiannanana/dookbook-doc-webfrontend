TOPIC: Semantics

# Semantics

In programming, **Semantics** refers to the meaning of a piece of code — for example
"what effect does running that line of JavaScript have?", or "what purpose or role does
that HTML element have" (rather than "what does it look like?".)

## Semantics in HTML

In [[HTML]], for example, the [`<h1>`](/en/webfrontend/<h1>) element is a *semantic element*, which
gives the text it wraps around the **role** (or **meaning**) of "a top level heading on your page."

```html
<h1>This is a top level heading</h1>
```

By default, most browser's user agent stylesheet will style an [`<h1>`](/en/webfrontend/<h1>) with a
large font size to make it look like a heading (although you could style it to look like
anything you wanted).

On the other hand, you could make any element look like a top level heading. Consider the following:

```html
<span style="font-size: 32px; margin: 21px 0;">Is this a top level heading?</span>
```

This will render it to look like a top level heading, but it has no semantic value, so
it will not get any extra benefits as described above. It is therefore a good idea to
use the right [[HTML]] element for the right job.

[[HTML]] should be coded to represent the data that will be populated and not based on its
default presentation styling. Presentation (how it should look), is the sole responsibility of [[CSS]].

Some of the **benefits** from writing semantic markup are as follows:

- [Search engines](/en/glossary/Search_Engine) will consider its contents as important keywords to
  influence the page's search rankings (see [[SEO]])
- Screen readers can use it as a signpost to help visually impaired users navigate a page
- Finding blocks of meaningful code is significantly easier than searching though
  endless [`<div>`](/en/webfrontend/<div>)s with or without semantic or namespaced classes
- Suggests to the developer the type of data that will be populated
- Semantic naming mirrors proper custom element/component naming

When approaching which markup to use, ask yourself, "What element(s) best describe
represent the data that I'm going to populate?" For example, is it a list of data?; ordered,
unordered?; is it an article with sections and an aside of related information?; does it list out
definitions?; is it a figure or image that needs a caption?; should it have a header and
a footer in addition to the global site-wide header and footer?; etc.

## Semantic Elements

These are some of the roughly 100 semantic [elements](/en/glossary/HTML) available:

- [`<article>`](/en/webfrontend/<article>)
- [`<aside>`](/en/webfrontend/<aside>)
- [`<details>`](/en/webfrontend/<details>)
- [`<figcaption>`](/en/webfrontend/<figcaption>)
- [`<figure>`](/en/webfrontend/<figure>)
- [`<footer>`](/en/webfrontend/<footer>)
- [`<header>`](/en/webfrontend/<header>)
- [`<main>`](/en/webfrontend/<main>)
- [`<mark>`](/en/webfrontend/<mark>)
- [`<nav>`](/en/webfrontend/<nav>)
- [`<section>`](/en/webfrontend/<section>)
- [`<summary>`](/en/webfrontend/<summary>)
- [`<time>`](/en/webfrontend/<time>)

## Semantics in CSS

In CSS, consider styling a list with `li` elements representing different types of
fruits. Would you know what part of the DOM is being selected with `div > ul > li`, or `.fruits__item`?

## Semantics in JavaScript

In JavaScript, consider a function that takes a string parameter, and returns an
`<li>` element with that string as its `textContent`. Would you need to look at
the code to understand what the function did if it was called `build('Peach')`, or `createLiWithContent('Peach')`?

## Learn More

- [Using HTML sections and outlines on MDN](https://wiki.developer.mozilla.org/en-US/docs/Web/Guide/HTML/Using_HTML_sections_and_outlines#Problems_solved_by_HTML5)
- [Semantics (computer science) on Wikipedia](https://en.wikipedia.org/wiki/Semantics#Computer_science)
