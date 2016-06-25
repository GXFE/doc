# HTML编码规范

## 一、模板规范
### PC页面模板
1. 指定文档类型（推荐使用 HTML5 的文档类型申明： &lt;!DOCTYPE html&gt;）
2. 指定文档编码为utf-8
3. 指定兼容方案
4. 编写网站关键字、描述信息、网站标题（SEO优化）
5. 页面头部&lt;/head&gt;标签前引入css样式文件，页面底部&lt;/body&gt;标签前引入js文件（提升网站性能和用户体验）

```html
<!-- 推荐使用html5规范 -->
<!DOCTYPE html>　
<!-- 制定文档语言 -->
<html lang="zh-cn">　
<head>
    <!-- 指定编码 -->
    <meta charset="UTF-8">　
    <!-- 兼容模式方案：IE以最高级模式渲染文档；使用Chrome Frame渲染。 -->
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">  
    <!-- 网站关键字 -->
    <meta name="keywords" content="关键词">　
    <!-- 网站描述 -->
    <meta name="description" content="描述信息">　
    <!-- 作者信息 -->
    <meta name="author" content="lizhigao">
    <!-- 网站标题 -->
    <title>首页</title>　
    <!-- 基础样式（reset等） -->
    <link rel="stylesheet" href="css/base.css">　
    <!-- 公用模块样式 -->
    <link rel="stylesheet" href="css/common.css">　
    <!-- 具体页面样式 -->
    <link rel="stylesheet" href="css/page.css">　
</head>
<body>
    <!-- html code -->
    <div>....</div>
    <p>...</p>
    <!-- /html code -->
    
    <!-- js库文件 -->
    <script src="js/jquery-1.12.4.min.js"></script>
    <!-- 页面js业务逻辑 -->
    <script src="js/page_index.js"></script>

    <div style="display: none">
        <!-- 统计代码 -->
    </div>
</body>
</html>
```
### 移动页面模板
待完善...（部分可参考PC页面模板）

## 二、书写规范
### 1. 缩进与换行
统一采用`4个空格`作为一个代码缩进层级，不允许使用`2个空格`；

```html
<ul class="news-list">
    <li class="news-item">...</li>
    <li class="news-item">...</li>
</ul>
```

### 2. 命名
* `class`必须单词全字母小写，单词间以中横线`-`分隔（为了方便代码阅读与维护,用于js操作的class，建议新增一个以`J-`开头作为class名，该class只用于js操作）;
* `id`建议单词全字母小写，单词间以下划线`_`分隔，（为了方便代码阅读与维护,用于js操作的id，建议以`J_`开头作为id名）。(经过讨论，根据自己习惯，ID也可以选用Camel命名法（如：newsList）)

```html
<!-- J_news_list：用于js业务逻辑操作 -->
<ul id="J_news_list" class="news-list">
    <li class="news-item">...</li>
    <li class="news-item">...</li>
</ul>

<!-- J-news-list：用于js业务逻辑操作； news-list：用于样式 -->
<ul class="J-news-list news-list">
    <li class="news-item">...</li>
    <li class="news-item">...</li>
</ul>
```

* `class`必须代表相应模块或部件的内容或功能，不得以样式信息进行命名。  
```html
<!-- Good -->
<div class="warn"></div>
<div class="sidebar"></div>

<!-- Bad -->
<div class="red"></div>
<div class="left"></div>
```

### 3. 标签
* 标签名必须使用小写字母。
```html
<!-- Good -->
<div>lowercase</div>

<!-- Bad -->
<DIV>upcase</DIV>
```

* 空标签不要闭合（`input`  `br`  `img`  `hr`）
```html
<!-- Good -->
<br> <hr>  

<!-- Bad -->
<br /> <hr />  
```

* 标签尽量简洁，不添加不必要的标签。
* 在CSS布局可以实现相同需求的情况下，不要使用表格进行布局。  

* HTML 标签的使用应该遵循标签的语义（`开发过程中一定要尽量根据上下文语义来选择语义化标签`），标签语义化主要有以下好处：
`1. 利于SEO（搜索引擎会根据标签的语义确定上下文和权重问题）。`
`2. 去掉样式或者样式丢失时页面结构依然清晰分明。`  
常用的语义化标签有：  

| 标签 | 描述 |
|:-------|:---------|
| h1~h6  |  标题1~标题6  |
| p | 段落 |
| b | 加粗 |
| em | 强调 |
| strong | 更强的强调（强调用&lt;em&gt;和&lt;strong&gt;，纯粹加粗用&lt;b&gt;） |
| ul | 无序列表（当涉及到列表的项目，应该用&lt;ul&gt; &lt;li&gt;或&lt;ol&gt; &lt;li&gt;（或者是&lt;dl&gt; &lt;dt&gt; &lt;dd&gt;来布局），而不是用&lt;table&gt;或&lt;p&gt;甚至&lt;span&gt;。）  |
| ol | 有序列表  |
| li | 列表项目  |
| dl | 定义列表 （当我们用带标题的列表时，即可采用&lt;dl&gt; &lt;dt&gt; &lt;dd&gt;自定义列表实现） |
| dt | 定义列表中的项目（即术语部分）  |
| dd | 定义列表中定义条目的定义部分 |
| span | 被用来组合文档中的行内元素 |
| q | 用来标记简短的单行引用 |
| blockquote | 用来标记那些一段或者好几段的长篇引用 |
| cite | &lt;cite&gt;标签既可以与&lt;q&gt; 一起用，也可以与&lt;blockquote&gt;一起用，用来提供引用内容的来源地址。|
| table | 表格 |
| caption | 表格标题 |
| th | 表头单元格 |
| td | 单元格 |
| button | 按钮 |
| input | 用于搜集用户信息; 根据type不同而产生不同作用 |
| textarea | 文本输入控件 |
| label | 为input元素定义标注（标记） |
| ins | 已经被插入文档中的文本 |
| del | 文档中已被删除的文本。 |

> __注意__：如果是开发针对高版本浏览器的项目或者是开发移动端项目，可以使用html5新增的语义化更好的标签（如：header、footer、article、aside、section、hgroup、nav、figure等）。

### 4. 属性
* 属性名必须使用`小写字母`。
* 属性值必须用双引号（`""`）包围。
```html
<!-- Good -->
<div class="hot-news">...</div>  

<!-- Bad -->
<div class='hot-news'>...</div>  
```

* 布尔类型的属性，建议不添加属性值。
```html
<input type="text" disabled>
<input type="checkbox" value="checkbox" checked>
```

* 自定义属性建议以`xxx-`为前缀，推荐使用`data-`。
```html
<img src="xxx.png" alt="test img" data-width="400" data-height="300">
```

* 分块注释，推荐两种注释写法：
```html
<!-- 注释规范一： -->
<!-- 头部 -->
<div class="header">
    此处省略100行...
</div>  <!-- /头部 -->
<!-- 底部 -->
<div class="footer">
    此处省略100行...
</div>  <!-- /底部 -->

<!-- 注释规范二： -->
<!-- 头部 start -->
<div class="header">
    此处省略100行...
</div>  <!-- 头部 end -->
<!-- 底部 start -->
<div class="footer">
    此处省略100行...
</div>  <!-- 底部 end -->
```








