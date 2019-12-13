TOPICS: lang attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `lang`

**`lang`** [全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) 参与了元素语言的定义。这个语言是不可编辑元素写入的语言，或者可编辑元素应该
写入的语言。标签包含单个条目，值的格式由 [用于定义语言的标签 (BCP47)](http://www.ietf.org/rfc/bcp/bcp47.txt) IETF 文档定义。如果标签的内容是空字
符串，语言就设为未知。如果标签内容是无效的，根据 BCP47，它就设为无效。

!!! warn "语言标签语法"
    完整的BCP47语法足以标记极其特定的语言方言，但大多数用法都要简单得多。
    语言标记由连字符分隔的语言子标签组成，其中每个子标签指示该语言的特定属性。 3个最常见的子标签是：
    **语言子标签**
    Required。一个2或3个字符的代码，用于定义基本语言，通常全部用小写编写。例如，English的语言代码是`en`，Badeshi的代码是`bdz`。
    **脚本子标签**
    该子标签定义了用于该语言的书写系统，并且总是4个字符长，首字母大写。例如，French-in-Braille是`fr-Brai`，`ja-Kana`是用Katakana字母书写的日文。如果语言是以非常典型的方式编写的，例如拉丁字母表中的英语，则无需使用此子标签。
    **地区子标签**
     该子标签定义了来自特定位置的基本语言的方言，并且是ALLCAPS中与国家代码匹配的2个字母，或者是与非国家区域匹配的3个数字。例如，es-ES是西班牙语中的西班牙语，es-013是中美洲的西
     班牙语。 “国际西班牙语”就是es。
     如果两者都存在，则脚本子标签位于区域子标签之前 ––ru-Cyrl-BY是俄语，用白俄罗斯语中的西里尔字母书写。
     要查找语言的正确子标签代码，请参阅[语言子标签查找](https://r12a.github.io/app-subtags/)。

即使设置了 **`lang`** 属性，也可能无效，因为 __xml:lang__ 属性更加优先。

对于CSS伪类[`:lang`](/zh-hans/webfrontend/:lang)，如果它们的名称不同，则两个无效的语言名称是不同的。比如`:lang(es)`匹配`lang =“es-ES”`
和`lang =“es-419”`，而`:lang(xyzzy)`与`lang =“xyzzy-Zorp！”`不匹配。

## 参见

- 所有HTML[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes).
