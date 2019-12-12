TOPICS: data- attribute

# HTML Global Attribute: `data-*`

The **`data-*`** [global attributes](/en/webfrontend/HTML_Global_Attributes)
form a class of attributes called custom data attributes, that allow proprietary information to be
exchanged between the HTML and its DOM representation by scripts.

All such custom data are available via the `HTMLElement` interface of the element the attribute is
set on. The `HTMLElement.dataset` property gives access to them.

The * may be replaced by any name following
[the production rule of xml names](http://www.w3.org/TR/REC-xml/#NT-Name) with the following restrictions:

- the name must not start with xml, whatever case is used for these letters;
- the name must not contain any semicolon (U+003A);
- the name must not contain capital letters.

Note that the `HTMLElement.dataset` property is a `DOMStringMap`, and the name of the custom data
attribute data-test-value will be accessible via `HTMLElement.dataset.testValue` ( or
`HTMLElement.dataset["testValue"]` ) as any dash (`U+002D`) is replaced by the capitalization of the
next letter, converting the name to camelcase.

## Usage

By adding `data-*` attributes, even ordinary HTML elements can become rather complex and powerful
program-objects.  For example, a space-ship "sprite" in a game could be a simple [`<img>`](/en/webfrontend/<img>)
element with a class attribute and several `data-*` attributes:

```html
<img class="spaceship cruiserX3" src="shipX3.png"
  data-ship-id="324" data-weapons="laserI laserII" data-shields="72%"
  data-x="414354" data-y="85160" data-z="31940"
  onclick="spaceships[this.dataset.shipId].blasted()"/>
```

For a more in-depth tutorial about using HTML data attributes, see [Using data attributes](https://wiki.developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes).

## See also

- All HTML [global attributes](/en/webfrontend/HTML_Global_Attributes).
- The [`HTMLElement.dataset`](/en/webfrontend/HTMLElement.dataset)
property that allows to access and modify these values.
