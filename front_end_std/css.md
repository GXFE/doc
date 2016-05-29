# CSS规范
## 命名规范
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
| left right center | 左右中 |

* 类名多个单词用 __中横线“-”__ 连接：
```html
...
<style>
    #news{/*...*/}  /* 不推荐 */
    .news-list li{/*...*/}  /* 不推荐 */

    .news{/*...*/}  /* 推荐 */
    .news-list .news-item{/*...*/}  /* 推荐 */
</style>
...
<div id="news" class="news">...</div>
<ul class="news-list">
    <li class="news-item">...</li>
    <li class="news-item">...</li>
    <li class="news-item">...</li>
</ul>
...
```
* 避免使用ID选择器、标签选择器，尽量 __使用类选择器__：
```html
...
<style>
    #news{/*...*/}  /* 不推荐 */
    .news-list li{/*...*/}  /* 不推荐 */

    .news{/*...*/}  /* 推荐 */
    .news-list .news-item{/*...*/}  /* 推荐 */
</style>
...
<div id="news" class="news">...</div>
<ul class="news-list">
    <li class="news-item">...</li>
    <li class="news-item">...</li>
    <li class="news-item">...</li>
</ul>
...
```
* 