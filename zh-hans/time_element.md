TOPICS: <time>
AUTHORS: Xun Morl; xunmorl@mozilla.net; mdn:xunmorl
         紫云飞; ziyunfei@mozilla.net; mdn:ziyunfei

# `<time>`

 HTML time 标签(`<time>`) 用来表示24小时制时间或者[公历日期](http://en.wikipedia.org/wiki/Gregorian_calendar)，若表示日期则也可包含时间和时区。

此元素意在以机器可读的格式表示日期和时间。 有安排日程表功能的应用可以利用这一点。

!!! warn "Don't try this at home"
    用法提示： 如果给定的日期不是正常日期或者在公历中最早的日期之前，请不要使用此元素。

!!! warn "Don't try this at home"
    状态提示： 该元素仍在设计和讨论中([http://blog.whatwg.org/weekly-time-data](http://blog.whatwg.org/weekly-time-data))

|  |  |
| :-- | :-- |
| **内容分类** | 流量内容，措辞内容 |
| **可包含内容** | 短语内容， 但不能包含子 `time` 元素。 |
| **标签可省略** | 起止标签均不能省略。 |
| **允许的父元素** | 任何接受措辞内容的元素。 |
| **标准文档** | HTML5, section 4.6.10 |

## 属性

像所有其他元素一样，此元素拥有可以使用 通用属性。

| 属性 | 描述 |
| :-- | :-- |
| `datetime` | 该属性表示此元素的时间和日期，并且属性值必须是一个[有效的日期格式，并可包含时间](http://www.w3.org/TR/html5/common-microsyntaxes.html#valid-date-string-with-optional-time)。如果此值不能被解析为日期，元素不会有一个关联的时间戳. |

## 示例

```html
<p>The concert starts at <time>20:00</time>.</p>
```

### `pubdate` 示例

```html
<article>
  <p>This article was created on <time pubdate>2011-01-28</time>.</p>
</article>
```

### `datetime` 示例

```html
<p>The concert took place on <time datetime="2001-05-15 19:00">May 15</time>.</p>
```
