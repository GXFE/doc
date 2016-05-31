# JS编码规范
### 1. 命名
Camel命名法：每个单词首字母大写（第一个单词除外）。
Pascal命名法：每个单词首字母大写。

* __`变量` 使用 Camel命名法；`常量` 使用 `全部字母大写，单词间下划线分隔` 的命名方式。__
```javascript
// 变量
var newsList = {};  

// 常量
var NEWS_COUNT = 20; 
```

* __`函数`、`函数的参数` 使用 `Camel命名法`，__
```javascript
function stringFormat (targetString) {
}
```

* __`类` 使用 `Pascal命名法`。__
```javascript
function TextNode(options) {
}
```

* __类的 `方法`  `属性` 使用 `Camel命名法`。__
```javascript
function TextNode(value, engine) {
    this.value = value;
    this.engine = engine;
}

TextNode.prototype.clone = function () {
    return this;
};
```

* __`类名` 使用 `名词`。__
```javascript
function Engine(options) {
}
```

* __`函数名` 使用 `动宾短语`。__
```javascript
function getStyle(element) {
}
```

* __`boolean` 类型的变量使用 `is` 或 `has` 开头。__
```javascript
var isReady = false;
var hasMoreCommands = false;
```

### 2. 注释
* __`单行注释`：必须独占一行。`//` 后跟一个空格，缩进与下一行被注释说明的代码一致。__

* __`多行注释`：避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。__

* __`文档化注释`：为了便于代码阅读和自文档化，以下内容建议包含以 `/**...*/` 形式的块注释中。__
1. 文件
2. 类
3. 函数或方法
4. 事件
5. 常量
6. 全局变量

* __文档注释前必须空一行。__

* __文件注释__
文件顶部必须包含文件注释，建议格式如下：
```javascript
/**
 * 文件描述
 * @author Created by lizhigao(lizhigao@021.com) on 2016-04-31
 *         Update By wujinhang(wujinhang@021.com) on 2016-05-20
 */

// js代码
```

* __函数/方法注释__
每一个方法上面必须包含注释，建议格式如下：
```javascript
/**
 * 去掉字符串两侧的空白
 * @param {string} ostr 需处理的值
 * @returns {string} 处理后的值
 */
function trim(str){
    return ostr.replace(/^\s+|\s+$/g,'');
}
```

### 3. 变量
* __声明变量必须加上 `var` 关键字。__
当你没有写 `var`, 变量就会暴露在全局上下文中, 这样很可能会和现有变量冲突. 另外, 如果没有加上, 很难明确该变量的作用域是什么, 变量也很可能像在局部作用域中, 很轻易地泄漏到 `Document` 或者 `Window` 中, 所以务必用 `var` 去声明变量.



* __全局变量声明提前。__
在 JavaScript 中变量和方法定义会自动提升到执行之前。JavaScript 只有 `function` 级的定义域，而无其他很多编程语言中的块定义域，所以使得你在某一 `function` 内的某语句和循环体中定义了一个变量，此变量可作用于整个 `function` 内，而不仅仅是在此语句或循环体中，因为它们的声明被 JavaScript 自动提升了。
```javascript
// Good
(function(log) {
    'use strict';

    var a = 10,
        b = 10,
        c,
        d = 100,
        i,
        x;

    function f() {

    }

    for (i = 0; i < 10; i++) {
        c = a * b * i;
    }

    x = function() {
        return d * d;
    };

    log(x());
}(window.console.log));


// Bad
(function(log) {
    'use strict';

    var a = 10;
    var b = 10;

    for (var i = 0; i < 10; i++) {
        var c = a * b * i;
    }

    function f() {
    }

    var d = 100;
    var x = function() {
        return d * d;
    };

    log(x());
}(window.console.log));
```

* __把赋值尽量写在变量申明中。__
```javascript
// Good
var a = 10,
    b = 10,
    c = 100;

// Bad
var a,
    b,
    c;

a = 10;
b = 10;
c = 100;
```


### 4. 缩进
* __使用`4`个空格或者一个`tab`操作（用`4`个空格代表一个制表符）做为一个缩进层级，不允许使用`2`个空格。__
```javascript
// Good
function func(){
    console.log('test');
    return;
}

// Bad
function func(){
  console.log('test');
  return;
}
```

* __`switch` 下的 `case` 和 `default` 必须增加一个缩进层级。__
```javascript
// Good
switch (variable) {
    case '1':
        // do...
        break;
    case '2':
        // do...
        break;
    default:
        // do...
}

// Bad
switch (variable) {
case '1':
    // do...
    break;
case '2':
    // do...
    break;
default:
    // do...
}
```

### 5. 空格
* __二元运算符两侧必须有一个空格，一元运算符与操作对象之间不允许有空格。__ 
```javascript
var a = !arr.length;
a++;
a = b + c;
```

* 用作代码块起始的左花括号 `{` 前必须有一个空格。
```javascript
// Good
if (condition) {

}
function funcName() {

}

// Bad
if (condition){

}
function funcName(){

}
```

* __`if`  `else`  `for`  `while`  `function`  `switch`  `do`  `try`  `catch`  `finally` 关键字后，必须有一个空格。__
* 
```javascript
// Good
if (condition) {
}
while (condition) {
}
(function () {
})();

// Bad
if(condition) {
}
while(condition) {
}
(function() {
})();
```

* __在对象创建时，属性中的 `:` 之后必须有空格，`:` 之前不允许有空格。__
```javascript
// Good
var obj = {
    a: 1,
    b: 2,
    c: 3
};

// Bad
var obj = {
    a : 1,
    b:2,
    c :3
};
```

* __`,` 和 `;` 前不允许有空格。__
```javascript
// Good
func(a, b);

// Bad
func(a , b) ;
```

### 6. 换行
* __每个独立语句结束后必须换行。__
* __运算符处换行时，运算符必须在新行的行首。__
```javascript
// Good
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}
var result = number1 + number2 + number3
    + number4 + number5;

// Bad
if (user.isAuthenticated() &&
    user.isInRole('admin') &&
    user.hasAuthority('add-admin') ||
    user.hasAuthority('delete-admin')) {
    // Code
}
var result = number1 + number2 + number3 +
    number4 + number5;
```

* __在语句的行长度超过 120 时，根据逻辑条件合理缩进。__
```javascript
// 较复杂的逻辑条件组合，将每个条件独立一行，逻辑运算符放置在行首进行分隔，或将部分逻辑按逻辑组合进行分隔。
// 建议最终将右括号 ) 与左大括号 { 放在独立一行，保证与 `if` 内语句块能容易视觉辨识。
if (user.isAuthenticated()
    && user.isInRole('admin')
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')
) {
    // Code
}

// 按一定长度截断字符串，并使用 + 运算符进行连接。
// 分隔字符串尽量按语义进行，如不要在一个完整的名词中间断开。
// 特别的，对于 HTML 片段的拼接，通过缩进，保持和 HTML 相同的结构。
var html = '' // 此处用一个空字符串，以便整个 HTML 片段都在新行严格对齐
    + '<article>'
    +     '<h1>Title here</h1>'
    +     '<p>This is a paragraph</p>'
    +     '<footer>Complete</footer>'
    + '</article>';

// 也可使用数组来进行拼接，相对 `+` 更容易调整缩进。
var html = [
    '<article>',
        '<h1>Title here</h1>',
        '<p>This is a paragraph</p>',
        '<footer>Complete</footer>',
    '</article>'
];
html = html.join('');

// 当参数过多时，将每个参数独立写在一行上，并将结束的右括号 ) 独立一行。
// 所有参数必须增加一个缩进。
foo(
    aVeryVeryLongArgument,
    anotherVeryLongArgument,
    callback
);

// 也可以按逻辑对参数进行组合。
// 最经典的是 baidu.format 函数，调用时将参数分为“模板”和“数据”两块
baidu.format(
    dateFormatTemplate,
    year, month, date, hour, minute, second
);

// 当函数调用时，如果有一个或以上参数跨越多行，应当每一个参数独立一行。
// 这通常出现在匿名函数或者对象初始化等作为参数时，如 `setTimeout` 函数等。
setTimeout(
    function () {
        alert('hello');
    },
    200
);

order.data.read(
    'id=' + me.model.id,
    function (data) {
        me.attchToModel(data.result);
        callback();
    },
    300
);

// 链式调用较长时采用缩进进行调整。
$('#items')
    .find('.selected')
    .highlight()
    .end();

// 三元运算符由3部分组成，因此其换行应当根据每个部分的长度不同，形成不同的情况。
var result = thisIsAVeryVeryLongCondition
    ? resultA : resultB;

var result = condition
    ? thisIsAVeryVeryLongResult
    : resultB;
```

### 7. 语句
* __不得省略语句结束的分号。__
* __在 `if`  `else`  `for`  `do`  `while` 语句中，即使只有一行，也不得省略块 `{...}`。__
```javascript
// Good
if (condition) {
    callFunc();
}

// Bad
if (condition) callFunc();
if (condition)
    callFunc();
```

* __函数定义结束不允许添加分号。__
```javascript
// Good
function funcName() {
}

// Bad
function funcName() {
};

// 如果是函数表达式，分号是不允许省略的。
var funcName = function () {
};
```

* `立即执行函数表达式（IIFE）`必须在函数表达式外添加 `(`，非 `立即执行函数表达式（IIFE）` 不得在函数表达式外添加 `(`。
IIFE = Immediately-Invoked Function Expression.
```javascript
// Good
var task = (function () {
   // Code
   return result;
})();
var func = function () {
};

// Bad
var task = function () {
    // Code
    return result;
}();
var func = (function () {
});
```









