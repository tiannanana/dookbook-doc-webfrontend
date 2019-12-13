TOPICS: <em>

# `<em>`

HTML 着重元素 (**`<em>`**) 标记出需要用户着重阅读的内容， `<em>` 元素是可以嵌套的，嵌套层次越深，则其包含的内容被认定为越需要着重阅读。

## 属性

此元素只包括[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

## 示例

`<em>` 元素通常被用于指示一个隐式或显式的对比。

```html
<p>
  In HTML 5, what was previously called <em>block-level</em> content is now called <em>flow</em> content.
</p>
```

## `<i>` vs. `<em>`

新的开发人员经常被它混淆，为什么有这么多的元素来表达对一些文本的强调。[`<i>`](/zh-hans/webfrontend/<i>) 和 `<em>` 也许是最常见的一种。
为什么使用 `<em></em>` vs `<i></i>`? 他们产生的结果是完全相同的，不是吗？

不完全是. 在默认情况下，视觉效果是一样的这两个标签都把内容呈现为斜体. 但语义是不同的。 `<em>` 标签表示着重强调其内容，
而 [`<i>`](/zh-hans/webfrontend/<i>) 标签表示从正常的散文中区分出的文本,
如电影或书籍的名字，一个外来词, 或者当文本指的是一个字的定义，而不是其自身代表的语义。

例如， `<em>` 可能是: "Just do it already!", 或: "We had to do something about it". 人或软件在阅读文本时会对斜体字的发音使用重读强调。

例如， [`<i>`](/zh-hans/webfrontend/<i>) 可能是: "The Queen Mary sailed last night".
在这里没有必要对这个词"Queen Mary"添加强调或重要性. 它只是表明，谈论问题的对象不是一个名叫玛丽女王, 而是一艘名字叫玛丽的船.
另一个例子 [`<i>`](/zh-hans/webfrontend/<i>) 可能是: "The word the is an article".
