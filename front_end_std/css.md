# CSS编码规范
css模板
````css
@charset "utf-8";
/**
 * 样式描述信息
 * @author 作者信息
 * @date 日期信息
 */
html,body{/*...*/}
.test{/*...*/}

/*=================
 样式一
 =================*/
 .class{/*...*/}
 .class{/*...*/}
 .class{/*...*/}

 /*=================
 样式二
 =================*/
 .class{/*...*/}
 .class{/*...*/}
 .class{/*...*/}
````


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
| left right center | 左 右 中 |

* 类名如果超过一个单词时，请使用 __中横线“-”__ 连接：
```html
...
<!-- 推荐写法 -->
<ul class="news-list">
    <li class="news-item">...</li>
    <li class="news-item">...</li>
    <li class="news-item">...</li>
</ul>
<!-- 不推荐写法 -->
<ul class="news_list">
    <li class="news_item">...</li>
    <li class="news_item">...</li>
    <li class="news_item">...</li>
</ul>
...
```
* 避免使用ID选择器、标签选择器，尽量 __使用类选择器__：
```html
<!-- 不推荐 -->
...
<style>
    #news{/*...*/}
    .news-list a{/*...*/}
</style>
...
<div id="news">...</div>
<div class="news-list">
    <a href="javascript:;">...</a>
    <a href="javascript:;">...</a>
    <a href="javascript:;">...</a>
</div>
...

<!-- 推荐 -->
...
<style>
    .news{/*...*/}
    .news-list .news-item{/*...*/}
</style>
...
<div id="news" class="news">...</div>
<div class="news-list">
    <a class="news-item" href="javascript:;">...</a>
    <a class="news-item" href="javascript:;">...</a>
    <a class="news-item" href="javascript:;">...</a>
</div>
...
```
* 