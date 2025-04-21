# Spralang语法教程

1. Spralang是一种新型的文档编写语言，能够解决传统文档在渲染及交互方面存在的限制问题，旨在实现文档的高效编写。
2. Spralang（/sprə-lɑːŋ/）由Spring（春天/弹性）和Lang（语言/龙读音/朗读音）组成，具有新生力量、轻量灵活、清晰简洁等寓意。
3. Spralang语言解析依赖于[EHEditor编辑器](https://editor.benhuisen.com/go)。

# 标签属性规则

1. 各属性以半角逗号（,）隔开，属性和值以等号（=）相连。
2. CSS类名属性，如果有多个类名，各个类名用空格隔开。
3. HTML样式属性是由逗号分隔的CSS属性和值组成，如：border=none, font-size=10等。
4. 当属性值单位为像素（px）时，px可省略。
5. 当属性值中有半角逗号或半角括号，文本需要用半角双引号或半角单引号括起来。
6. 如果文本中有半角单引号或双引号或回车等特殊字符，需要在特殊字符左侧添加转义字符“\”。

# 标签种类

Spralang语法中定义了`区块(block)`、`文本(text)`、`图片(image|gif)`、`链接(link)`、`锚点(anchor)`、`表格(table)`、`标签(tag)`、`音频(audio)`、`视频(video)`等多种标签。通过在各标签中引入标签自有属性、CSS类名或HTML样式等，可轻松实现文档的渲染和交互。各标签介绍如下：

## 区块

区块标签（`:::block(…)…:::`）用于组合其他元素。在页面中会独占一行。可将`文本(text)、图片(image|gif)、链接(link)、锚点(anchor)`等元素包裹在一个区块内，以方便进行整体样式的设置（如改变背景颜色、设置边框等），使文档内容更有层次感。

### 语法

```
:::block(css=className, html样式, badge-text=徽章文字, badge-css=徽章className, badge-*=徽章html样式值, id=ID, data-*=数据属性值, role=角色, aria-*=ARIA属性值)
区块内容
:::
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `:::block … :::` | 是 | 区块标识，被包围的部分为区块内容 |
| `(…)` | 是 | 括号`()`中的内容由`css、html样式、badge-text、badge-css、badge-*、id、data-*、role、aria-*`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `css` | 否 | 区块CSS，值为CSS类名（className），类名之间以空格隔开，推荐引用bootstrap5中的className，如`css=alert alert-success` |
| `html样式` | 否 | 区块HTML样式，由逗号分隔的CSS属性和值组成，如`border=none, font-size=10`等 |
| `badge-text` | 否 | 徽章文字 |
| `badge-css` | 否 | 徽章CSS，值为CSS类名（className）：`eh-block-badge lt|rt|lb|rb`、`eh-block-badge triangle lt|rt|lb|rb`，其中`lt|rt|lb|rb`分别表示`左上角|右上角|左下角|右下角` |
| `badge-*` | 否 | 徽章HTML样式，`badge-`后连接CSS属性和值，如`badge-color=red, badge-background=cyan` |
| `id` | 否 | ID，在文档范围内值要唯一 |
| `data-*` | 否 | 数据属性值 |
| `role`@[link](href=#anchor-1008,title=[7],css=link-primary,offset=up) | 否 | HTML增强属性，角色，通常和aria-*属性结合使用 |
| `aria-*`@[link](href=#anchor-1007,title=[8],css=link-primary,offset=up) | 否 | ARIA属性值 |

### 示例

<img width="1194" alt="image" src="https://github.com/user-attachments/assets/c8aad8bd-9c61-408b-934d-42eb35a80f4b" />

## 文本

文本标签（`@[text](…)`）用于设置文本样式。

### 语法

```
@[text](css=className, html样式, value=文本内容, id=ID, type=类型, title=标题, path=文本文件路径, href=链接, data-*=数据属性值, role=角色, aria-*=ARIA属性值)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[text]` | 是 | 文本标识 |
| `(…)` | 是 | 括号`()`中的内容由`value、css、html样式、type、title, path, href、role、data-*、aria-*`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `value` | 否 | 文本内容，如果文本中有逗号或括号（`,|(|)`），文本需要用引号(`"|'`)括起来；如果文本中有引号或回车（`"|'|\n`）等特殊字符，需要在特殊字符左侧添加转义字符（`\`）。path和value属性不能同时存在 |
| `css` | 否 | 文本CSS，值为CSS类名（className），类名之间以空格隔开 |
| `html样式` | 否 | 文本HTML样式，由逗号分隔的CSS属性和值组成，如：`border=none, font-size=10px（px可省略）`等 |
| `id` | 否 | ID，在文档范围内值要唯一 |
| `type` | 否 | HTML标签类型，值：`p(默认)|button|span|div|a等`。不建议设置此属性，优选通过CSS类名或HTML样式设置即可 |
| `title` | 否 | 标题，鼠标悬停在文本上时，弹出的提示内容 |
| `path` | 否 | 文本文件路径，当path和value属性不能同时存在 |
| `href` | 否 | 链接 |
| `data-*` | 否 | 数据属性值 |
| `role`@[link](href=#anchor-1007,title=[7], css=link-primary, offset=up) | 否 | HTML增强属性，角色，通常和aria-*属性结合使用 |
| `aria-*`@[link](href=#anchor-1008,title=[8], css=link-primary, offset=up) | 否 | ARIA属性值 |

### 示例

<img width="1222" alt="image" src="https://github.com/user-attachments/assets/bfe858a1-f7ab-40ae-9eaf-91495b082c82" />

## 图片

图片标签（`@[image](…)`）用于插入图片。

### 语法

```
@[image](src=图片地址, alt=图片描述, href=链接, css=className, html样式)
```
| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[image]` | 是 | 图片标识 |
| `(…)` | 是 | 括号`()`中的内容由`src、alt、href、css、html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `src` | 是 | 图片地址 |
| `alt` | 否 | 图片描述，图像无法显示时的替代文本 |
| `href` | 否 | 链接，即点击图片跳转的地址 |
| `css` | 否 | 图像CSS，值为CSS类名（className），类名之间以空格隔开，推荐引用bootstrap5中的className，如`css=alert alert-success` |
| `html样式` | 否 | 图片HTML样式，由逗号分隔的CSS属性和值组成，如`border=none, font-size=10px`等 |

### 示例

<img width="1223" alt="image" src="https://github.com/user-attachments/assets/8c643a5e-86f4-4136-a993-0dfde0d6cfde" />

## GIF图片

GIF图片标签（`@[gif](…)`）用于插入GIF图片。

### 语法

```
@[gif](src=gif图片地址, poster=封面地址, autoplay=是否自动播放, alt=图片描述, css=className, html样式, btn-css=播放按钮className, btn-*=播放按钮html样式)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[gif]` | 是 | GIF图像标识 |
| `(…)` | 是 | 括号`()`中的内容由`src、poster、autoplay、alt、css、html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `src` | 是 | GIF图片地址 |
| `poster` | 否 | 封面地址，设置poster，则必须设置宽高（width和height） |
| `autoplay` | 否 | 是否自动播放，值：`true|false` |
| `alt` | 否 | 图片描述，图像无法显示时的替代文本 |
| `css` | 否 | 图像CSS，值为CSS类名（className），类名之间以空格隔开，推荐引用bootstrap5中的className，如`css=alert alert-success` |
| `html样式` | 否 | GIF图片HTML样式，由逗号分隔的CSS属性和值组成，如`border=none, font-size=10px`等 |
| `btn-css` | 否 | 播放按钮CSS，值为CSS类名（className） |
| `btn-*` | 否 | 播放按HTML样式，`btn-`后连接CSS属性和值，如`btn-color=red, btn-background=cyan` |

<img width="814" alt="image" src="https://github.com/user-attachments/assets/7bf2ebb6-6f42-4b79-8e97-ee85a05d06f5" />

## 链接

链接标签（`@[link](…)`）用于在文档内部或外网链接之间实现跳转，方便引用其他资源。

### 语法

```
@[link](href=链接, css=className, offset=up|down, title=标题, html样式)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[link]` | 是 | 链接标识 |
| `(…)` | 是 | 括号`()`中的内容由`href、css、offset、title、html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `href` | 是 | 链接分为相对链接（即文档内链接）和绝对链接（即全路径链接），相对链接以`#`开头，如`href=#anchor-11`，绝对链接如：`href=www.baidu.com` |
| `css` | 否 | 图像CSS，值为CSS类名（className），类名之间以空格隔开，推荐引用bootstrap5中的className，比如`css=alert alert-success` |
| `offset` | 否 | 偏移位置，值为`up|down`。`up`：向上偏移；`down`：向下偏移 |
| `title` | 否 | 标题 |
| `html样式` | 否 | 链接HTML样式，由逗号分隔的CSS属性和值组成，如`border=none, font-size=10px`等 |

### 示例

<img width="1217" alt="image" src="https://github.com/user-attachments/assets/f8a8f2c3-e8ad-48de-be89-ed9e4b91defc" />

## 锚点

锚点标签（`@[anchor](…)`）用于在文档中建立锚点，通常需要结合`@[link](…)`或`[链接描述](url)`标签实现快速定位功能。

**锚点**是一种用于快速定位到特定位置的标记，在网页或文档中广泛应用。若要实现快速定位功能，需历经**设置锚点**和**引用锚点**这两个步骤。

### 语法

```
@[anchor](id=锚点编号, href=链接, css=className, offset=up|down, title=标题, show=none|id|title, html样式)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[anchor]` | 是 | 锚点标识 |
| `(…)` | 是 | 括号`()`中的内容由`id, href, css, offset, title, show, html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `id` | 是 | 锚点编号，同一文档中id不能重复 |
| `href` | 否 | 链接分为相对链接（即文档内链接）和绝对链接（即全路径链接），相对链接以`#`开头，如`href=#anchor-11`，绝对链接如：`href=www.baidu.com` |
| `css` | 否 | 层叠样式表（Cascading Style Sheets），可选，值为css类名（className），推荐引用bootstrap5中的className |
| `offset` | 否 | 偏移位置（可选），值为`up|down`。`up`：向上偏移；`down`：向下偏移 |
| `title` | 否 | 标题（可选） |
| `show` | 否 | 显示的文本（可选），值为`none|id|title`，默认显示id |
| `html样式` | 否 | 链接HTML样式（可选），由逗号分隔的CSS属性和值组成，如：`color=red!important, margin-left=20px` |

### 示例

<img width="1031" alt="image" src="https://github.com/user-attachments/assets/a9b7e09b-bcc3-4943-8278-5f82c9f1b05d" />

## 表格

表格标签（`:::table(…)…:::`）用于将CSV@[link](href=#anchor-210,title=[210],offset=up,css=small,color=red)格式内容以表格形式呈现。该标签支持嵌入`文本(text)、图片(image|gif)`、`链接(link)`、`锚点(anchor)`、`标签(tag)`等子标签，可轻松实现插入图片、链接、锚点以及合并行/列等功能；通过引入加载器，可轻松实现表格分页、排序、搜索等功能。

### 语法

```
:::table(border=是否显示边框，header=是否有表头，css=className, html样式, loader=表格加载器, search=是否支持搜索, page-size=一页数据条数, page-list=可选每页数据条数, sort-index=排序列索引, column-width=列宽度, merge-list=合并单元格规则列表, tr-css_{row}=className, tr-{css属性}_{row}=css属性值, td-css_{row}_{column}=className, td-{css属性}_{row}_{column}=css属性值)
CSV格式数据
:::
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `:::table … :::` | 是 | 表格标识，被包围的部分为表格CSV格式内容 |
| `(…)` | 是 | 括号`()`中的内容由`border、header、css、html样式、loader、search、page-size、page-list、sort-index、column-width、merge-list、tr-css_{row}、tr-{css属性}_{row}、td-css_{row}_{column}、td-{css属性}_{row}_{column}`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `border` | 否 | 是否显示边框（可选），值`0（默认）|1`。`border=1`表示显示边框；`border=0`表示无边框 |
| `header` | 否 | 是否有表头（可选），值`0（默认）|1`。`header=1`表示有表头；`header=0`表示无表头 |
| `css` | 否 | 表格CSS（可选），值为CSS类名（className），类名之间以空格隔开，推荐引用bootstrap5中的className，比如`css=table table-hover` |
| `html样式` | 否 | 表格HTML样式（可选），由逗号分隔的CSS属性和值组成，如：`border=none, font-size=10px`等 |
| `loader` | 否 | 表格加载器（可选），值`空（默认）|bootstrap|layui`@[link](href=#anchor-1005,title=[5],offset=up)@[link](href=#anchor-1006,title=[6],offset=up)。通过该属性，可实现表格分页、搜索、排序等交互效果。`loader`不为空时，`search、page-size、page-list、sort-index`有效 |
| `search` | 否 | 是否支持搜索（可选），值`0（默认）|1`。`search=1`表示支持搜索；`search=0`表示不支持搜索 |
| `page-size` | 否 | 当数据分页显示时，一页数据显示的条数（可选），值`0（默认）|正整数` |
| `page-list` | 否 | 当数据分页显示时，可选每页数据条数（可选），`page-list=10-20-50`表明支持每页展示10、20和50条 |
| `sort-index` | 否 | 支持排序的列的索引（可选），`sort-index=0-1-3`表明第1、2、4列支持排序 |
| `column-width` | 否 | 列宽度（可选），`column-width=0_120-2_80`表明第1列宽度120px、第三列宽度90px |
| `merge-list` | 否 | 合并单元格规则列表（可选）。格式：`row_column_colspan_rowspan-…`。其中：`row`，起始行索引，从0开始；`column`，起始列索引，从0开始；`colspan`，合并列跨度（横向合并单元格数量）；`rowspan`，合并行跨度（纵向合并单元格数量）。例如`merge-list=0_0_2_1-3_2_1_2`表明第1行、1列横向合并两个单元格、纵向合并一个单元格（即不合并）；第4行、3列横向合并一个单元格、纵向合并两个单元格 |
| `tr-css_{row}` | 否 | 表格行CSS（可选），值为CSS类名（className），类名之间以空格隔开。其中`{row}`值：`空|rowIndex|startIndex~endIndex`。例如：`tr-css=text-danger`表示所有行CSS为text-danger；`tr-css_1=text-danger`表示`第2行`CSS为text-danger；`tr-css_0~3=text-danger`表示`第1~4行`CSS为text-danger |
| `tr-{css属性}_{row}` | 否 | 表格行CSS属性（可选），值为CSS属性值。其中`{css属性}`也叫style属性，如`background-color`等；`{row}`值：`空|rowIndex|startIndex~endIndex`。例如：`tr-background-color=red`表示`所有行`背景为红色；`tr-background-color_1=red`表示`第2行`背景为红色；`tr-background-color_0~3=red`表示`第1~4行`背景为红色 |
| `td-css_{row}_{column}` | 否 | 表格单元格CSS（可选），值为CSS类名（className），类名之间以空格隔开。其中`{row}`和`{column}`分别代表行和列的索引（从0开始），值均为：`空|index|startIndex~endIndex`。例如：`td-css=text-danger`表示`所有`单元格CSS为text-danger；`td-css_1_2=text-danger`表示`2行3列`的单元格CSS为text-danger；`tr-css_0~3_1~2=text-danger`表示`1~4行2~3列`的单元格CSS为text-danger |
| `td-{css属性}_{row}_{column}` | 否 | 表格单元格CSS属性（可选），值为CSS属性值。其中`{css属性}`也叫style属性，如`background-color`等；`{row}`和`{column}`分别代表行和列的索引（从0开始），值均为：`空|index|startIndex~endIndex`。例如：`td-background-color=red`表示`所有`单元格背景为红色；`td-background-color_1_2=red`表示`2行3列`的单元格背景为红色；`tr-background-color_0~3_1~2=red`表示`1~4行2~3列`的单元格背景为红色 |

### 备注：CSV（Comma-Separated Values，逗号分隔值）内容格式规范:
1. 每条记录占一行：以逗号为分隔符。
2. 逗号前后的空格会被忽略。
3. 字段中包含有逗号：该字段必须用双引号括起来。
4. 字段中包含有换行符：该字段必须用双引号括起来。
5. 字段前后包含有空格：该字段必须用双引号括起来。
6. 字段中的双引号：用两个双引号表示。
7. 字段中如果有双引号：该字段必须用双引号括起来。

### 示例

<img width="1222" alt="image" src="https://github.com/user-attachments/assets/9d3a05fd-f100-4e12-93cc-1dd65a93fa07" />

<img width="1221" alt="image" src="https://github.com/user-attachments/assets/94395b9f-3ef4-4d90-b665-9a6716d504e8" />

<img width="1224" alt="image" src="https://github.com/user-attachments/assets/2ee7a739-6e04-4061-8194-f1a421cdcd5c" />

<img width="1219" alt="image" src="https://github.com/user-attachments/assets/5fa471df-f708-4a0c-aa45-2be5cf212f24" />

## 标签

TAG标签（`@[tag]()`）用于设定其所在布局的HTML样式。将`@[tag]()`标签放于文本段落中的任意位置，即可设定此段落的HTML样式。

### 语法

```
@[tag](title=标题, href=链接, colspan=合并列数, rowspan=合并行数, css=className, html样式, inner-property=内层标签属性, inner-css=内层标签className, inner-html样式=内层标签html样式)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[tag]` | 是 | 标签标识 |
| `(…)` | 是 | 括号`()`中的内容由`title、href、colspan、rowspan、css、html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `title` | 否 | 标题 |
| `href` | 否 | 链接 |
| `colspan` | 否 | 合并列数 |
| `rowspan` | 否 | 合并行数 |
| `css` | 否 | CSS，值为CSS类名（className），类名之间以空格隔开，推荐引用bootstrap5中的className，比如`css=text-warning` |
| `html样式` | 否 | HTML样式，由逗号分隔的CSS属性和值组成，如`border=none, font-size=10px`等 |
| `inner-property` | 否 | 内层标签属性 |
| `inner-css` | 否 | 内层标签className |
| `inner-html样式` | 否 | 内层标签html样式 |

### 示例

<img width="1226" alt="image" src="https://github.com/user-attachments/assets/1a396a9d-30c7-4a48-b871-5f67c47454c7" />

## 音频

音频标签（`@[audio]()`）用于在文档中插入音频。

### 语法

```
@[audio](title=标题, src=音频链接, type=音频MIME类型, autoplay=是否自动播放, loop=是否循环播放, muted=是否静音播放, preload=音频加载方式，css=className, html样式)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[audio]` | 是 | 音频标识 |
| `(…)` | 是 | 括号`()`中的内容由`title、src、type、autoplay、loop、muted、preload、css、html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `title` | 否 | 标题 |
| `src` | 是 | 音频链接 |
| `type` | 否 | 音频MIME类型@[link](href=#anchor-1004, title=[4], offset=up)，如：`audio/ogg、audio/mpeg、audio/wav`等 |
| `autoplay` | 否 | 是否自动播放（可选），值`false（默认）|true` |
| `loop` | 否 | 是否循环播放（可选），值`false（默认）|true` |
| `muted` | 否 | 是否静音播放（可选），值`false（默认）|true` |
| `preload` | 否 | 音频加载方式（可选），值`auto|metadata（默认）|none`。none：不预加载音频，适用于用户确认播放时才加载的情况，metadata：预加载音频的元数据，但不加载整个文件，auto：预加载整个音频文件，适用于需要实时播放的场景 |
| `css` | 否 | 层叠样式表（Cascading Style Sheets），可选，值为css类名（className） |
| `html样式` | 否 | 音频HTML样式（可选），由逗号分隔的CSS属性和值组成，如：`width=200px` |

### 示例

<img width="986" alt="image" src="https://github.com/user-attachments/assets/953e452e-b69b-4303-8347-2af65d4b9037" />

## 视频

视频标签（`@[video]()`）用于在文档中插入视频。

### 语法

```
@[video](title=标题, src=视频链接, type=视频MIME类型, autoplay=是否自动播放, loop=是否循环播放, muted=是否静音播放, preload=视频加载方式，css=className, html样式)
```

| 标识或属性 | 是否必需 | 描述 |
| --- | --- | --- |
| `@[video]` | 是 | 视频标识 |
| `(…)` | 是 | 括号`()`中的内容由`title、src、type、autoplay、loop、muted、preload、css、html样式`组成，各属性以`,`隔开，属性和值以`=`相连 |
| `title` | 否 | 标题 |
| `src` | 是 | 视频链接 |
| `poster` | 否 | 视频封面链接 |
| `type` | 否 | 视频MIME类型@[link](href=#anchor-1004, title=[4], offset=up)，如：`audio/ogg、audio/mpeg、audio/wav`等 |
| `autoplay` | 否 | 是否自动播放（可选），值`false（默认）|true` |
| `loop` | 否 | 是否循环播放（可选），值`false（默认）|true` |
| `muted` | 否 | 是否静音播放（可选），值`false（默认）|true` |
| `preload` | 否 | 视频加载方式（可选），值`auto|metadata（默认）|none`。none：不预加载音频，适用于用户确认播放时才加载的情况，metadata：预加载音频的元数据，但不加载整个文件，auto：预加载整个音频文件，适用于需要实时播放的场景 |
| `css` | 否 | 层叠样式表（Cascading Style Sheets），可选，值为css类名（className） |
| `html样式` | 否 | 视频HTML样式（可选），由逗号分隔的CSS属性和值组成，如：`width=200px` |

### 示例

<img width="971" alt="image" src="https://github.com/user-attachments/assets/bb4c33b3-4331-4f3c-bc47-81d682addfae" />

## 轮播

轮播标签（`:::carousel(…)…:::`）用于循环浏览一系列内容，轮播标签中可插入图片`@[image](…)`、视频`@[video](…)`等以及HTML代码。

### 语法

```
@[carousel](css=className, html样式, theme=主题, anim=动画, interval=间隔时间, indicator=是否显示指示器, control=是否显示控制器, caption-title-{index}=字幕标题, caption-content-{index}=字幕内容, caption-css=字幕className, caption-{css属性}=字幕css属性值)
轮播内容
:::
```


