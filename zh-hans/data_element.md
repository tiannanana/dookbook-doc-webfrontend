TOPICS: <data>

# `<data>`

**HTML `<data>` 元素** 将一个指定内容和机器可读的翻译联系在一起。但如果内容是与 time 或者 date 相关的，一定要使用 [`<time>`](/zh-hans/webfrontend/<time>)。

## 属性

该元素含有[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

| 属性 | 描述 |
| :-- | :-- |
| `value` | 该属性指定元素内容对应的机器可读的翻译。 |

## 示例

下面的示例展示了一些产品名称并且每个名称都与其UPC码相关联。

```html
<p>新产品</p>
<ul>
 <li><data value="3967381398">迷你番茄酱</data></li>
 <li><data value="3967381399">巨无霸番茄酱</data></li>
 <li><data value="3967381400">超级巨无霸番茄酱</data></li>
</ul>
```
