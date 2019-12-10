TOPICS: CSS Class Selector

# CSS 类选择器

在一个HTML文档中，[[CSS]] **类选择器**会根据元素的*类属性*(`class`)中的内容匹配元素。类属性被定义为一个以空格分隔的列表项，在这组类名中，必须有一项与类选择器中的类名完全匹配，此条样式声明才会生效。

## 语法

```css
.类名 { 样式声明 }
```

注意它与下面的[属性选择器](/zh-hans/webfrontend/CSS_Attribute_Selector)语句等价:

```css
[class~=class_name] { 样式声明 }
```

## 示例

```css
.red {
  color: #f33;
}

.yellow-bg {
  background: #ffa;
}

.fancy {
  font-weight: bold;
  text-shadow: 4px 4px 3px #77f;
}
```

```html
<p class="red">这个段落是红色文本。</p>
<p class="red yellow-bg">这个段落是红色文本，和黄色背景。</p>
<p class="red fancy">这个段落是红色文本，和"fancy"的样式。</p>
<p>这个是常规段落，无特殊样式。</p>
```
