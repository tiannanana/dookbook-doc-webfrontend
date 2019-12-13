TOPICS: is attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `is`

**`is`**[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)允许您指定标准HTML元素的行为应类似于已定义的自定义内置元素（有关更多详细信息，请参见使用自定义元素）。

仅当在当前文档中成功定义了指定的自定义元素名称并扩展了要应用的元素类型时，才能使用此属性。

## 示例

以下代码来自我们的 [word-count-web-component](https://github.com/mdn/web-components-examples/tree/master/word-count-web-component)
示例（[see it live also](https://mdn.github.io/web-components-examples/word-count-web-component/)）。

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

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
