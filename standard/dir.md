# 文件目录规范
### 命名规范
1. 尽量使用 `英文单词` 命名（如：index、about、contact等），`避免使用汉语拼音` 命名（如：shouye、guanyu、lianxiwomen等）；
2. 超过一个单词的时候使用下划线 `_` 连接（如：about_us、contact_us等）。

### 目录结构规范
* 结构（html）、样式（css）、行为（js）分离，不到迫不得已，请不要将css和js代码写到html文件中。
* 对于简单的项目（两三个页面，样式、业务逻辑简单），采用目录结构一(pc_dir1)，结构如下图：
![目录结构一](../resources/img/pc_dir1.png)

* 对于复杂的项目（页面数量较多，样式、业务逻辑比较复杂），采用目录结构二（pc_dir2）, 结构如下图：
![目录结构一](../resources/img/pc_dir2.png)

### 目录结构说明
* 结构一

pc-dir1/　　` 项目名称 `  
├── dist/　　` 项目发布目录（压缩、合并后的代码） `  
│　　├── css/  
│　　├── js/  
│　　├── img/  
│　　└── index.html  
└── src/　　` 项目开发目录（源代码） `  
　　├── css/　　` css样式文件目录 `  
　　│　　├── base.css　　` 基础样式（包含reset样式、原子性样式），与项目、功能无关的基础样式（所有项目均可使用） `[查看示例](../resources/css/base.css)  
　　│　　├── common.css　　` 项目公共模块的样式（同一个项目不同页面使用） `  
　　│　　└── page.css　　` 具体业务样式（内含该项目所有页面的样式，通过css注释区分不同页面样式） `  
　　├── js/　　` js脚本文件目录 `  
　　│　　├── jquery-1.12.4.min.js　　` js库文件（针对我们目前的项目、业务，另外考虑到兼容性更强，我们采用jquery 1.x版本进行开发，移动端项目请使用ZeptoJS。） `  
　　│　　├── page_index.js　　` 首页js  `  
　　│　　└── page_about.js　　` 关于页面js  `  
　　├── img/　　` 图片文件目录（用于存放项目用到的所有图片） `  
　　│　　├── img1.png  
　　│　　└── img2.png  
　　├── index.html　　` 首页  `  
　　└── about.html　　` 关于页面  `  

* 结构二

pc-dir2/　　` 项目名称 `  
├── dist/　　` 项目发布目录（压缩、合并后的代码） `  
│　　├── css/  
│　　├── js/  
│　　├── img/  
│　　└── index.html  
└── src/　　` 项目开发目录（源代码） `  
　　├── css/  
　　│　　├── base.css  
　　│　　├── common.css  
　　│　　├── page_index.css　　` 首页样式 `  
　　│　　├── page_about.css　　` 关于页面样式 `  
　　│　　├── page_contact.css　　` 联系页面样式 `  
　　│　　├── page_details.css　　` 详情页面样式 `  
　　│　　└── page_promote.css　　` 推广页面样式 `  
　　├── js/　　` js脚本文件目录 `  
　　│　　├── jquery-1.12.4.min.js　　  
　　│　　├── page_index.js　　  
　　│　　└── page_about.js　　  
　　├── img/　　` 图片文件目录（通过目录区分不同页面图片） `  
　　│　　├── index/　　` 首页图片 `  
　　│　　│　　├── index1.png  
　　│　　│　　└── index2.png  
　　│　　├── about/　　` 关于页面图片 `  
　　│　　│　　├── about1.png  
　　│　　│　　└── about2.png  
　　│　　├── contact/　　` 联系页面图片 `  
　　│　　│　　├── contact1.png  
　　│　　│　　└── contact2.png  
　　│　　├── details/　　` 详情页面图片 `  
　　│　　│　　├── details1.png  
　　│　　│　　└── details2.png  
　　│　　├── promote/　　` 推广页面图片 `  
　　│　　│　　├── promote1.png  
　　│　　│　　└── promote2.png  
　　│　　├── common1.png　　` 公用图片 `  
　　│　　└── common2.png  
　　├── index.html　　` 首页  `  
　　├── about.html　　` 关于页面  `  
　　├── contact.html　　` 联系页面  `  
　　├── details.html　　` 详情页面  `  
　　└── promote.html　　` 推广页面  `  