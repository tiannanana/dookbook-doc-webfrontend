TOPICS: is attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML Global Attribute: `is`

The **`is`** [global attribute](/en/webfrontend/HTML_Global_Attributes) allows you to specify that a
standard HTML element should behave like a defined custom built-in element (see Using custom
elements for more details).

This attribute can only be used if the specified custom element name has been successfully defined
in the current document, and extends the element type it is being applied to.

## Examples

The following code is taken from our [word-count-web-component](https://github.com/mdn/web-components-examples/tree/master/word-count-web-component)
example ([see it live also](https://mdn.github.io/web-components-examples/word-count-web-component/)).

```javascript
// Create a class for the element
class WordCount extends HTMLParagraphElement {
  constructor() {
    // Always call super first in constructor
    super();

    // Constructor contents ommitted for brevity
    ...

  }
}

// Define the new element
customElements.define('word-count', WordCount, { extends: 'p' });
```

```html
<p is="word-count"></p>
```

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
