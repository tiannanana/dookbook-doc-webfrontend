TOPICS: <audio>

# `<audio>`

HTML `<audio>` 元素用于在文档中表示音频内容。 `<audio>` 元素可以包含多个音频资源， 这些音频资源可以使用 `src` 属性或者
[`<source>`](/zh-hans/webfrontend/<source>) 元素来进行描述； 浏览器将会选择最合适的一个来使用。对于不支持`<audio>`元素的浏览器，`<audio>`元素也可以作为浏览器不识别的内容加入到文档中。

你也可以使用Gecko特有的更加强大的audio API特性在JavaScript 代码中直接生成和控制音频流。详情参见 [Introducing the audio API extension](https://wiki.developer.mozilla.org/en-US/docs/Introducing_the_Audio_API_Extension)

|  |  |
| :-- | :-- |
| **内容分类** | 流内容，短语内容，嵌入内容。 如果具有控件属性：交互式内容和可触摸的内容. |
| **允许内容** | 如果元素包含 src 属性：零个或多个 [`<track>`](/zh-hans/webfrontend/<track>) 元素，其后紧跟不包含 `<audio>` 或者 [`<video>`](/zh-hans/webfrontend/<video>)媒体元素的透明内容。或者：零个或多个 [`<source>`](/zh-hans/webfrontend/<source>) 元素，其后紧跟零个或多个 [`<track>`](/zh-hans/webfrontend/<track>) 元素，其后紧跟不包含 `<audio>` 或者 [`<video>`](/zh-hans/webfrontend/<video>)媒体元素的透明内容。 |
| **标记省略** | 不允许，开始标签和结束标签都不能省略。|
| **允许的父级元素** | 任何接受嵌入内容的元素。|
| **允许的 ARIA 角色** | `application` |
| **DOM 接口** | `HTMLAudioElement` |

## 属性

该元素包含[全局属性](/zh-hans/webfrontend/HTML_Global_Attributes)。

| 属性 | 描述 |
| :-- | :-- |
| `autoplay` | 布尔属性；如果指定（默认值为"false"！）；指定后，音频会马上自动开始播放，不会停下来等着数据载入结束。 |
| `buffered` | 你可以通过该属性获取已缓冲的资源的时间段信息。该属性包含一个 `TimeRanges` 对象。 |
| `controls` | 如果设置了该属性，浏览器将提供一个包含声音，播放进度，播放暂停的控制面板，让用户可以控制音频的播放。 |
| `loop` | 布尔属性；如果指定，将循环播放音频。 |
| `mozCurrentSampleOffset` | 在音频播放时，表示相对于音频开始处的偏移量的一个数值。 |
| `muted` | 表示是否静音的布尔值。默认值为false，表示有声音。 |
| `played` | 一个TimeRanges 对象，表示所有已播放的音频片段。 |
| `preload` | 枚举属性，让开发者自行思考来示意浏览器使用何种加载方式以达到最好的用户体验。可以是以下属性之一：<br><br>`none`: 示意用户可能不会播放该音频，或者服务器希望节省带宽；换句话说，该音频不会被缓存；<br>`metadata`: 示意即使用户可能不会播放该音频，但获取元数据 (例如音频长度) 还是有必要的。<br>`auto`: 示意用户可能会播放音频；换句话说，如果有必要，整个音频都将被加载，即使用户不期望使用。<br>空字符串 : 等效于`auto`属性。<br><br>假如不设置，默认值就是浏览器定义的了（不同浏览器会选择自己的默认值）， 即使规范建议设置为 metadata. |

## 使用备注

- `autoplay` 属性优先于 `preload` 假如用户想自动播放视频，那么很明显浏览器需要下载视频。同时设置`autoplay` 和 `preload`属性在规范里是允许的。
- 规范没有强制浏览器去遵循该属性的值；这仅仅只是个提示。

| 属性 | 描述 |
| :-- | :-- |
| `src` | 嵌入的音频的URL。 该URL应遵从 HTTP access controls. 这是一个可选属性；你可以在audio元素中使用 [`<source>`](/zh-hans/webfrontend/<source>) 元素来替代该属性指定嵌入的音频。|
| `volume` | 音频播放的音量。值从0.0 (无声) 到 1.0 (最大声). 时间偏移量目前是指定为float类型的值，表示偏移的秒数。|

**备注**： HTML 5 规范中，时间偏移量值的定义还没有完成，有可能会变更。

## 事件

`audio`元素支持的事件

## 示例

### 基本用法

```html
<!-- Simple audio playback -->
<audio src="http://developer.mozilla.org/@api/deki/files/2926/=AudioTest_(1).ogg" autoplay>
  Your browser does not support the <code>audio</code> element.
</audio>

<!-- Audio playback with captions -->
<audio src="foo.ogg">
  <track kind="captions" src="foo.en.vtt" srclang="en" label="English">
  <track kind="captions" src="foo.sv.vtt" srclang="sv" label="Svenska">
</audio>
```

### 使用`source`元素的`audio`元素

```html
<audio controls="controls">
  Your browser does not support the <code>audio</code> element.
  <source src="foo.wav" type="audio/wav">
</audio>
```
