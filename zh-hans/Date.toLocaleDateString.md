TOPICS: Date.toLocaleDateString

# `Date.toLocaleDateString()`

**`toLocaleDateString()`** 方法返回该日期对象日期部分的字符串，该字符串格式因不同语言而不同。新增的参数 `locales` 和 `options` 使程序能够指定使用哪种
语言格式化规则，允许定制该方法的表现（behavior）。在旧版本浏览器中， `locales` 和 `options` 参数被忽略，使用的语言环境和返回的字符串格式是各自独立实现的。

## 语法

```javascript
dateObj.toLocaleDateString([locales [, options]])
```

| 参数 | 说明 |
| :-- | :-- |
| `locales` | 具有BCP 47语言标记的字符串，或此类字符串的数组。 要使用浏览器的默认语言环境，请忽略此参数或传递`undefined`。 支持Unicode扩展名（例如"`en-US-u-ca-buddhist`"）。 有关`locales`参数的一般形式和解释，请参见Intl页面。 允许使用以下Unicode扩展名:<br><br>**`nu`**<br>编号系统。 可能的值包括: "`arab`", "`arabext`", "`bali`", "`beng`", "`deva`", "`fullwide`", "`gujr`", "`guru`", "`hanidec`", "`khmr`", "`knda`", "`laoo`", "`latn`", "`limb`", "`mlym`", "`mong`", "`mymr`", "`orya`", "`tamldec`", "`telu`", "`thai`", "`tibt`".<br><br>**`ca`**<br>日历。 可能的值包括: "`buddhist`", "`chinese`", "`coptic`", "`ethiopia`", "`ethiopic`", "`gregory`", "`hebrew`", "`indian`", "`islamic`", "`iso8601`", "`japanese`", "`persian`", "`roc`".<br><br>**`hc`**<br>小时周期。 可能的值包括: "`h11`", "`h12`", "`h23`", "`h24`". |
| `options` Optional | 具有以下某些或全部属性的对象: <br><br>**`localeMatcher`**<br>要使用的语言环境匹配算法。 可能的值为“查找”和“最合适”； 默认值为“最适合”。 有关此选项的信息，请参见国际页面。<br><br>**`timeZone`**<br>使用的时区。 实现必须识别的唯一值是“ UTC”。 默认值是运行时的默认时区。 实施还可以识别IANA时区数据库的时区名称，例如“亚洲/上海”，“亚洲/加尔各答”，“美国/纽约”。<br><br>**`hour12`**<br>是否使用12小时制（而不是24小时制）。 可能的值是`true`和`false`； 默认值取决于地区。 如果两者都存在，则此选项将覆盖`hc`语言标记和`/`或`hourCycle`选项。<br><br>**`hourCycle`**<br>使用的小时周期。 可能的值为“`h11`”，“`h12`”，“`h23`”或“`h24`”。 如果同时存在`hc`语言标记，则此选项将覆盖`hc`语言标记，如果同时指定了两个选项，则`hour12`选项优先。<br><br>**`formatMatcher`**<br>要使用的格式匹配算法。 可能的值为“基本”和“最合适”； 默认值为“最适合”。 有关使用此属性的信息，请参见以下段落。<br><br>以下属性描述了在格式化输出中使用的日期时间组件及其所需的表示形式。 需要实现以至少支持以下子集：<br>1、`weekday`, `year`, `month`, `day`, `hour`, `minute`, `second`<br>2、`weekday`, `year`, `month`, `day`<br>3、`year`, `month`, `day`<br>4、`year`, `month`<br>5、`month`, `day`<br>6、`hour`, `minute`, `second`<br>7、`hour`, `minute`<br><br>实施可以支持其他子集，并且将针对所有可用的子集表示组合协商请求以找到最佳匹配。 有两种算法可用于此协商并由`formatMatcher`属性选择：完全指定的“基本”算法和与实现相关的“最佳匹配”算法。|
| `weekday` | 工作日的表示形式。 可能的值为：<br>"`long`" （例如，星期四）<br>"`short`"（例如，星期四）<br>"`narrow`"（例如`T`）。 在某些地区，两个工作日可能具有相同的缩小样式（例如，星期二的缩小样式也为`T`）。 |
| `era` | 时代的代表。 可能的值为：<br>"`long`"（例如Anno Domini）<br>"`short`"（例如，广告）<br>"`narrow`"（例如`A`） |
| `year` | 年份的表示形式。 可能的值为：<br>"`numeric`"（例如2012年）<br>"`2-digit`"（例如`12`） |
| `month` | 月份的表示形式。 可能的值为：<br>"`numeric`"（例如2）<br>"`2-digit`"（例如02）<br>"`long`"（例如，三月）<br>"`short`"（例如`3`月）<br>"`narrow`"（例如`M`）。 对于某些语言环境，两个月的狭窄风格可能相同（例如，`May`的狭窄风格也为`M`）。 |
| `day` | 一天的表示形式。 可能的值为：<br>"`numeric`"（例如: `1`）<br>"`2-digit`"（例如: `01`） |
| `hour` | 小时的表示形式。 可能的值为"`numeric`"，"`2-digit`" |
| `minute` | 分钟的表示形式。 可能的值为"`numeric`"，"`2-digit`" |
| `second` | 第二个的表示形式。 可能的值为"`numeric`"，"`2-digit`"。 |
| `timeZoneName` | 时区名称的表示形式。 可能的值为：<br>"`long`"（例如，英国夏令时）<br>"`short`"（例如: `GMT+1`） |

每个日期时间组件属性的默认值都是`undefined`，但是，如果`weekday`、`year`、`month`、`day`属性都是`undefined`，则为`year`、`month`和`day`。
假定为`"numeric"`。

**返回值**: String

## 示例

### 使用 `toLocaleDateString`

没有指定语言环境（`locale`）时，返回一个使用默认语言环境和格式设置（options）的格式化字符串。

```javascript
var date = new Date(Date.UTC(2012, 11, 12, 3, 0, 0));

// toLocaleDateString without arguments depends on the implementation,
// the default locale, and the default time zone
date.toLocaleDateString();
// → "12/11/2012" if run in en-US locale with time zone America/Los_Angeles
```

### 检测 `locales` 和 `options` 参数支持情况

`locales` 和 `options` 参数不是所有的浏览器都支持。为了检测一种实现环境（implementation）是否支持它们，可以使用不合法的语言标签，如果实现环境支持该参数，
则会抛出一个 `RangeError` 异常，反之会忽略参数。

```javascript
function toLocaleDateStringSupportsLocales() {
    try {
        new Date().toLocaleDateString("i");
    } catch (e) {
        return e​.name === "RangeError";
    }
    return false;
}
```

### 使用`locales`

下例展示了本地化日期格式的一些变化。为了在应用的用户界面得到某种语言的日期格式，必须确保使用 `locales` 参数指定了该语言（可能还需要设置某些回退语言）。

```javascript
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

// formats below assume the local time zone of the locale;
// America/Los_Angeles for the US

// US English uses month-day-year order
alert(date.toLocaleDateString("en-US"));
// → "12/19/2012"

// British English uses day-month-year order
alert(date.toLocaleDateString("en-GB"));
// → "20/12/2012"

// Korean uses year-month-day order
alert(date.toLocaleDateString("ko-KR"));
// → "2012. 12. 20."

// Arabic in most Arabic speaking countries uses real Arabic digits
alert(date.toLocaleDateString("ar-EG"));
// → "٢٠‏/١٢‏/٢٠١٢"

// for Japanese, applications may want to use the Japanese calendar,
// where 2012 was the year 24 of the Heisei era
alert(date.toLocaleDateString("ja-JP-u-ca-japanese"));
// → "24/12/20"

// when requesting a language that may not be supported, such as
// Balinese, include a fallback language, in this case Indonesian
alert(date.toLocaleDateString(["ban", "id"]));
// → "20/12/2012"
```

### 使用`options`

可以使用 `options` 参数来自定义 `toLocaleDateString` 方法返回的字符串。

```javascript
var date = new Date(Date.UTC(2012, 11, 20, 3, 0, 0));

// request a weekday along with a long date
var options = {weekday: "long", year: "numeric", month: "long", day: "numeric"};
alert(date.toLocaleDateString("de-DE", options));
// → "Donnerstag, 20. Dezember 2012"

// an application may want to use UTC and make that visible
options.timeZone = "UTC";
options.timeZoneName = "short";
alert(date.toLocaleDateString("en-US", options));
// → "Thursday, December 20, 2012, GMT"
```

## 性能

当格式化大量日期时，最好创建一个 [`Intl.DateTimeFormat`](/zh-hans/webfrontend/Intl.DateTimeFormat) 对象，然后使用该对象
[`format`](/zh-hans/webfrontend/Intl.DateTimeFormat.format) 属性提供的方法。
