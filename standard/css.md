# CSS编码规范
## 一、示例模板
```css
@charset "utf-8";
/**
 * Doxygen 风格的注释示例
 * 样式描述信息
 * @author lizhigao(lizhigao@021.com)
 * @date 2016-05-31
 */
html,
body {
    margin: 0;
    padding: 0;
}
/* ===========================================================
   一级区块注释
   =========================================================== */
.section1 {
    color: red;
    border: 1px solid #000;
}
/* -----------------------------------------------------------
   二级区块注释
   ----------------------------------------------------------- */
.section2 {
    color: #f00;
}
/* 一般注释 */
.section2 { color: green; }

```

## 二、代码风格
### 1. CSS文件头部声明`@charset`
为了避免 HTML 和 CSS 文件编码不同时造成中文解析乱码，造成的不必要的麻烦，CSS 文件头部统一加上文件对应的编码。
```css
@charset "utf-8";
/* css样式 */
```
> 注意：
> 1、`@charset` 前面不能有任何字符。
> 2、`@charset` 必须放在css文件的第一行。

### 2. 注释
* 普通注释，注释文字左右各留一个空格。
```css
/* 普通注释 */
```

* 区块注释
一级区块注释
```css
/* ===========================================================
   一级区块注释
   =========================================================== */
```
二级区块注释
```css
/* -----------------------------------------------------------
   二级区块注释
   ----------------------------------------------------------- */
```

* Doxygen 风格的注释
每个 CSS 文件的头部或区块的开始处应当包含Doxygen风格的注释，以阐明该文件或这段代码的 作用、作者、最后更新时间等信息。
以 `/**` 开始，每行以 `*` 号开头，最后以 `*/` 结束。
```css
/**
 * Doxygen 风格的注释示例
 * 样式描述信息
 * @author lizhigao(lizhigao@021.com)
 * @date 2016-05-31
 */
```

* `clean-css` 等压缩工具中的注释
clean-css是一个CSS压缩工具，为了保留CSS文件的版权信息等特殊需求，支持以下形式的注释。
```css
/*!
  这里是版权信息或者重要的注释，压缩后不会被删除
*/
```

### 3. 颜色与单词（统一使用小写）
* 字体名称以及特殊的 CSS 属性/值（`translateX`等）不要求强制小写
* 颜色值如果是16进制，推荐小写，更加容易辨识。
* 如果是关键字色值，建议使用16进制颜色值代替[颜色关键字](https://drafts.csswg.org/css-color-3/#svg-color)。  

```css
/* Good */
.foo{
    background: #ccc;
    color: #00f;
    border-color: #F00; /* 红色 */
    transform: translateX(20px);
}

/* Bad */
.Foo{
    BACKGROUND: #CCC;
    color: blue;
    border-color: red;
    transform: translateX(20px);
}
```

### 4. 缩进
* 使用`4`个空格或者一个`tab`操作（用`4`个空格代表一个制表符）做为一个缩进层级，不允许使用`2`个空格。
```css
/* Good */
.list {
    font-size: 14px;
}

/* Bad */
.list {
  font-size: 14px;
}
```

* 每个声明前保留一级缩进
```css
/* Good */
h3 {
    font-weight: bold;
}

/* Bad */
h3 {
font-weight: bold;
}
```

* 右大括号保持与该规则集第一个字符对齐
```css
/* Good */
h3 {
    font-weight: bold;
}

/* Bad */
h3 {
    font-weight: bold;
    }
```

### 5. 空格
* `选择器` 与 `{` 之间必须包含空格。
```css
.selector {

}
```

* `属性名` 与之后的 `:` 之间不允许包含空格， `:` 与 `属性值` 之间必须包含空格。
```css
/* Good */
.selector {
    margin: 0;
}
```

* `列表型属性值` 书写在单行时，`,` 后必须跟一个空格。
```css
.selector {
    font-family: Arial, sans-serif;
}
```

### 6. 选择器
* 当一个样式规则包含多个选择器时，每个选择器声明必须独占一行。
```css
/* Good */
.post,
.page,
.comment {
    line-height: 1.5;
}

/* Bad */
.post, .page, .comment {
    line-height: 1.5;
}
```

* `>`、`+`、`~` 选择器的两边各保留一个空格。
```css
/* Good */
main > nav { padding: 10px; }
label + input { margin-left: 5px; }
input:checked ~ button { background-color: #69C; }

/* Bad */
main>nav { padding: 10px; }
label+input { margin-left: 5px; }
input:checked~button { background-color: #69C; }
```

* 属性选择器中的值必须用双引号`""`包围。
```css
/* Good */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female;
}

/* Bad */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female;
}
```

### 7. 属性
* 选择器内只有一个声明时可以写在一行，有多个声明时，每条声明都应该独占一行。
```css
/* Good */
h1 { font-size: 32px; }
h2 { font-size: 26px; }
h3 { font-size: 22px; }

/* Bad */
h1 { 
    font-size: 32px; 
}
h2 { 
    font-size: 26px; 
}
h3 { 
    font-size: 22px; 
}

/* Good */
.selector {
    margin: 0;
    padding: 0;
}

/* Bad */
.selector { margin: 0; padding: 0; }
```

* 声明定义后必须以分号结尾
```css
/* Bad */
.selector { 
    margin: 0
    padding: 0
}

/* Good */
.selector {
    margin: 0;
    padding: 0;
}
```

### 8. 声明书写顺序
同一规则下的声明在书写时，应按功能进行分组，并以 Formatting Model（`布局方式、位置`） > Box Model（`尺寸`） > Typographic（`文本相关`） > Visual（`视觉效果`） 的顺序书写，以提高代码的可读性。  
* Formatting Model 相关属性包括：`position` / `top` / `right` / `bottom` / `left` / `float` / `display` / `overflow` 等
* Box Model 相关属性包括：`border` / `margin` / `padding` / `width` / `height` 等
* Typographic 相关属性包括：`font` / `line-height` / `text-align` / `word-wrap` 等
* Visual 相关属性包括：`background` / `color` / `transition` / `list-style` 等
另外，如果包含 content 属性，应放在最前面。
```css
.sidebar {
    /* 布局方式、位置  */
    position: absolute;
    top: 50px;
    left: 0;
    overflow-x: hidden;

    /* 尺寸（盒子模型）  */
    width: 200px;
    padding: 5px;
    border: 1px solid #ddd;

    /* 文本相关 */
    font-size: 14px;
    line-height: 20px;

    /* 视觉效果 */
    background: #f5f5f5;
    color: #333;
    -webkit-transition: color 1s;
       -moz-transition: color 1s;
            transition: color 1s;
}
```

### 9. 单位
长度为 `0` 时须省略单位。 （也只有长度单位可省）
```css
/* Good */
.selector {
    margin: 0 5px;
}

/* Bad */
.selector {
    margin: 0px 5px;
}
```

### 10. 清除浮动
请使用 `base.css` 中定义的清除浮动的类（`clearfix`）来清除浮动，请不要使用增加空标签的形式来清除浮动。

### 11. !important
非必要情况下，请不要使用`!important`。

### 12. 使用双引号`""`
用到引号的地方建议使用双引号。
```css
/* Good */
input[type="text"]{ /*...*/ }
.selector { background-image: url("xxxx.png"); }

/* Bad */
input[type=text]{ /*...*/ }
input[type='text']{ /*...*/ }
.selector { background-image: url(xxxx.png); }
.selector { background-image: url('xxxx.png'); }
```

### 13. 字体命名
* `font-family` 属性中的字体族名称应使用字体的英文 `Family Name`，其中如有空格，须放置在引号中。
所谓英文 Family Name，为字体文件的一个元数据，常见名称如下：

| 字体 | 操作系统 | Family Name |
|:-------:|:---------:|:---------:|
| 宋体 (中易宋体)  |  Windows  | SimSun             |
| 黑体 (中易黑体)  |  Windows  | SimHei             |
| 微软雅黑         |  Windows  | Microsoft YaHei    |
| 微软正黑         |  Windows  | Microsoft JhengHei |
| 华文黑体         |  Mac/iOS  | STHeiti            |
| 冬青黑体         |  Mac/iOS  | Hiragino Sans GB   |
| 文泉驿正黑       |  Linux    | WenQuanYi Zen Hei  |
| 文泉驿微米黑     |  Linux    | WenQuanYi Micro Hei|

```css
h1 { font-family: "Microsoft YaHei"; }
```

* `font-family` 按「西文字体在前、中文字体在后」、「效果佳 （质量高/更能满足需求）的字体在前、效果一般的字体在后」的顺序编写，最后必须指定一个通用字体族（ `serif` / `sans-serif` ）

```css
body {
    font-family: "Helvetica Neue", Arial, "Hiragino Sans GB", "WenQuanYi Micro Hei", "Microsoft YaHei", sans-serif;
}
```

## 三、 命名规则
尽量使用 `英文单词` 命名（如：header、footer、nav、hot-news、news-list等）， `避免使用汉语拼音` 命名（如：toubu、dibu、daohang、xinwen、liebiao等），下面列出了常用名称：

| 单词 | 意义 |
|:-------|:---------|
| header  |  头  |
| content、container | 内容 |
| footer | 尾/页脚 |
| nav | 导航 |
| sidebar | 侧边栏 |
| subnav | 子导航 |
| menu | 菜单 |
| submenu | 子菜单 |
| search | 搜索 |
| row | 行 |
| column | 栏目/列 |
| wrapper | 包裹层/容器 |
| left center right | 左 中 右 |
| login | 登录 |
| loginbar | 登录条 |
| regsiter | 注册 |
| logo | 标志 |
| banner | 广告 |
| main | 页面主体 |
| hot | 热点 |
| news | 新闻 |
| download | 下载 |
| friendlink | 友情链接 |
| copyright | 版权 |
| scroll | 滚动 |
| content | 内容 |
| tab | 标签页 |
| list | 文章列表 |
| msg | 提示信息 |
| tips | 小技巧 |
| title | 栏目标题 |
| joinus | 加入我们 |
| guild | 指南 |
| service | 服务 |
| status | 状态 |
| partner | 合作伙伴 |







