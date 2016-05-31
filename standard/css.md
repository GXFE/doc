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

### 3. 单词（统一使用小写）
* 字体名称以及特殊的 CSS 属性/值（`translateX`等）不要求强制小写
* 颜色值如果是16进制，推荐小写，更加容易辨识。
* 如果是关键字色值，推荐使用更加直观的[颜色关键字](https://drafts.csswg.org/css-color-3/#svg-color)。  

```css
/* Good */
.foo{
    background: #ccc;
    color: currentColor;
    border-color: red;
    transform: translateX(20px);
}

/* Bad */
.Foo{
    BACKGROUND: #CCC;
    color: currentColor;
    border-color: #F00; /* 红色 */
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

## 属性
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

## 命名和使用规范
* 尽量使用 __英文单词__ 命名（如：header、footer、nav、hot-news、news-list等），__避免使用汉语拼音__ 命名（如：toubu、dibu、daohang、xinwen、liebiao等），下面列出了常用名称：

| 单词 | 意义 |
|:-------:|:---------:|
| header  |  头  |
| content、container | 内容 |
| footer | 尾 |
| nav | 导航 |
| sidebar | 侧边栏 |
| row | 行 |
| column | 栏目/列 |
| wrapper | 包裹层/容器 |
| left center right | 左 中 右 |







