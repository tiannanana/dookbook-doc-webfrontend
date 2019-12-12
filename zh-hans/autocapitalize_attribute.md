TOPICS: autocapitalize attribute
AUTHORS: mdn; mdn@mozilla-community.org; github:mdn

# HTML 全局属性: `autocapitalize`

**autocapitalize** [全局属性](/zh-hans/webfrontend/HTML_Global_Attributes) 是一个枚举属性，它控制用户输入/编辑文本输入时文本输入是否自动大写，以及如何自动大写。属性必须取下列值之一：

- `off` or none: 没有应用自动大写（所有字母都默认为小写字母）。
- `on` or sentences: 每个句子的第一个字母默认为大写字母；所有其他字母都默认为小写字母。
- `words`: 每个单词的第一个字母默认为大写字母；所有其他字母都默认为小写字母。
- `characters`: 所有的字母都默认为大写。

在物理键盘上输入时， `autocapitalize` 属性不会影响行为。相反，它会影响其他输入机制的行为，比如移动设备的虚拟键盘和语音输入。这种机制的行为是，
它们经常通过自动地将第一个句子的字母大写来帮助用户。`autocapitalize` 属性使作者能够覆盖每个元素的行为。

`autocapitalize` 属性永远不会为带有 `type`  属性，其值为  `url`, `email` 或 `password`的 [`<input>`](/zh-hans/webfrontend/<input>)
元素启用自动大写。
