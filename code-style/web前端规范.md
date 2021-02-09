> 以下所有代码规范均适用于自己写的，非引入的 HTML、CSS、JAVASCRIPT 资源

# 基本通用规范（HTML、CSS、JAVASCRIPT）

## 文件/资源命名

要求如下：

1. 用‘`-`’号分隔文件名

2. 确保文件命名总是以字母开头而不是数字

3. 资源的字母名称必须全为小写

4. 一些情况下，对需要给文件增加前后缀或特定的扩展名的（比如 .min.js, .min.css），抑或一串前缀（比如 3fa89b.main.min.css）的，使用点分隔符

**不允许**

```
MyScript.js
myCamelCaseName.css
i_love_underscores.html
1001-scripts.js
my-file-min.css
```

**规范写法**

```
my-script.js
my-camel-case-name.css
i-love-underscores.html
thousand-and-one-scripts.js
my-file.min.css
```

## 文本编码

1. 所有文本都必须以 UTF-8 无 BOM 编码来书写，以确保不存在编码问题

## 文本缩进

1. 所有文本的缩进方式都是**两个**空格

2. tab键用两个空格代替

**HTML**

```HTML
<ul>
  <li>Fantastic</li>
  <li>Great</li>
  <li>
    <a href="#">Test</a>
  </li>
</ul>
```

**CSS**

```CSS
@media screen and (min-width: 1100px) {
  body {
    font-size: 100%;
  }
}
```

**JAVASCRIPT**

```JAVASCRIPT
(function(){
  var x = 10;
 
  function y(a, b) {
    return {
      result: (a + b) * x
    }
 
  }
}());
```

## 注释

1. 注释一般说明文档结构，或者功能简介，以及这样写的原因，不要写一眼就能看出来的注释

2. 各种注释的具体说明见对应的语言的文档规范

**没用的注释**

```JAVASCRIPT
var offset = 0;
 
if(includeLabels) {
  // 设置 offset 为 20
  offset = 20;
}
```

**正确的注释**

```JAVASCRIPT
var offset = 0;
 
if(includeLabels) {
  // 如果有 label，offset 是从20开始计数的
  offset = 20;
}
```

## 无效或者暂时被替换的代码段处理

1. 被确定无效的代码段不允许通过注释留在原文档中

2. 暂时被替换的代码段，在上线之前不允许留在原文档中，如果有需要，请自行备份文件

3. 上线的文档，不允许出现被注释掉的代码段

**不允许的写法**

```HTML
<!-- 暂时不使用 ul，因为XXXX
<ul class="list">
  <li class="item">1</li>
  <li class="item">2</li>
  <li class="item">3</li>
  <li class="item">4</li>
</ul>
-->
<div class="list">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
  <div class="item">4</div>
</div>
```

# HTML 文档规范

## 文档类型

1. 使用 HTML5 的文档类型申明： <!DOCTYPE html>

## 标签的写法

1. 最好不要将无内容元素的标签闭合，例如：使用 `<br>` 而非 `<br />`。这些标签包括：`area`, `base`, `br`, `col`, `command`, `embed`, `hr`, `img`, `input`, `keygen`, `link`, `meta`, `param`, `source`, `track`, `wbr`

2. 双标记标签一定要闭合，例如：`<div></div>`

## CSS、JS 引入位置

由于HTML文档加载的时候是从上而下加载的，并且在碰到外部引用文件时就去解析对应的文档，因此定义引入资源的方式如下:

1. CSS 由于需要渲染文档最终长的样子，因此需要写解析，因此放在HTML`head`中，使用例如：`<link rel="stylesheet" href="base.css">`

2. JS 由于大部分情况是设计交互的，因此在网页还未加载完成时不需要解析，因此可以放在文档最后引入，来提高网页加载速度。特殊情况除外（比如动态计算文档的font-size的时候，此时必须放在`head`中先引入）。使用例如：`<script src="app.js"></script>`

**具体例子**

```HTML
<!DOCTYPE html>
<html>
  <head>
    <link rel="stylesheet" href="main.css">
  </head>
  <body>
    <!-- 主要内容区域 -->
 
    <script src="main.js"></script>
  </body>
</html>
```

## 标签属性的写法

1. 属性名全部使用小写，因为html最终渲染出来的时候将全部使用小写

2. 词组使用连字符分隔

**错误写法**

```HTML
<div class="navContent" data-id="12" data-userNickname="你好"></div>
```

**正确写法**

```HTML
<div class="nav-content" data-id="12" data-user-nickname="你好"></div>
```

## 多媒体标签的处理

1. 请一定给`img`标签的`alt`属性填写对应的内容，该属性会在图片未加载出来的时候显示，请填写说明该图片所要呈现的内容

2. `video` 和 `audio` 标签一样需要填写如果浏览器不支持时的提示文字

**正确写法**

```HTML
<img src="default-avator.jpg" alt="用户头像">

<audio src="someaudio.wav">
您的浏览器不支持 audio 标签。
</audio>

<video src="movie.ogg" controls="controls">
您的浏览器不支持 video 标签。
</video>
```

## 文档内容说明

1. HTML中应该尽量都是文本内容，样式应该交给CSS处理

2. 非特殊原因，不允许在 HTML 标签上写`style`属性

3. 不允许使用以下标签：`<b>`, `<u>`, `<center>`, `<font>`

## 注释

1. 注释使用 `<!--注释内容-->`

2. 注释一般用于说明文档结构，用`<!--推荐-->`标记开始，用`<!--/推荐-->`标记结束，此种标记一般用于一个区块的文档很长的情况

3. 注释代码段时注意不要破坏原代码结构

**正确的注释方法**

```HTML
<!--注释代码段的方式
<div class="recommend">
  <div class="recommend-user">推荐人</div>
  <div class="recommend-user">推荐人</div>
  ...
</div>
-->

<!--推荐-->
<div class="recommend">
  <div class="recommend-user">推荐人</div>
  <div class="recommend-user">推荐人</div>
  ...
</div>
<!--/推荐-->
```

## 引号

1. HTML 文档中不允许出现单引号，所有都是双引号

# CSS 文档规范

## 换行和空格

1. 每个属性占一行，不允许多个属性写在一行

2. 如果有多个选择器的情况下，每个选择器一行

3. 每个css代码段之后空一行

4. 每个属性之后都必须以分号结尾

5. 属性名和属性值之间加一个空格

6. 所有引号全部使用双引号，无单引号

7. 注释为css前后注释，`/** common */`标记开始，`/** /common */`标记结束

8. 上线的文件中不允许存在被注释掉的属性或者css代码段

**范例**

```CSS
/**
* 该 css 为XXXXX
*/

/** common */
html {
  font-family: "open sans", arial, sans-serif;
}

h1,
h2,
h3 {
  font-weight: normal;
}
/** /common */

/** header */
.header {
  font-size: 20px;
  padding: 5px;
}

.header .title {
  font-size: 16px;
}
/** /header */
```

## id 和 css 选择器

1. 非特殊情况，id 不写任何样式，也不用于任何样式的限定

2. 一般情况下所有样式都使用class来取，尽量避免html标签名

**非推荐**

```CSS
#header {
  font-size: 20px;
}

#header p{
  font-size: 16px;
}
```

**推荐写法**

```CSS
.header {
  font-size: 20px;
}

.header p{
  font-size: 16px;
}
```

## 取名

1. 使用连字符而非驼峰式

2. 样式优先，内容为辅

3. 尽可能精确，避免样式冲突

**范例**

```HTML
<div class="content content-news">
  <span class="title">News event</span>
  <div class="content-body">
    <div class="content-title">
      Check this out
    </div>
    <p>This is a news article content</p>
  </div>
</div>
<div class="content content-recommend">
  <span class="title">News event</span>
  <div class="content-body">
    <p>This is a news article content</p>
  </div>
</div>
```

说明：

- `content-news` 和 `content-recommend` 而非 `news-content` 和 `recommend-content` 体现了样式优先，内容为辅

- 两段内容下都有`title`，因此写的时候应该注意尽量精确

```CSS
.content {
  font-size: 18px;
}

.content.content-news {
  padding: 10px;
}

.content.content-recommend {
  padding: 5px;
}

.content-news .title {
  color: #f00;
}

.content-recommend .title {
  color: #000;
}
```

## 0 和 单位

1. 省略“0”值后面的单位。不要在0值后面使用单位，除非有值。

**推荐**

```CSS
padding-bottom: 0;
margin: 0;
```

## 颜色

1. 使用小写

2. 使用十六进制而非`red`,`grey`等英文

2. 能用3位字符的十六进制就不要用6位的

# JAVASCRIPT 文档规范

> 此处说明用于现阶段 ES6 之前的JS，ES6 的规范后期再定

## 变量

1. 变量使用驼峰式命名

2. 变量申明时一次性指定，避免多次使用 `var`

3. 一个变量独占一行

4. 变量申明尽量提前，避免重复申明

5. 变量未能从名字上提现作用的，一定在后面加上变量的注释说明

**错误写法**

```JAVASCRIPT
var speed = 10;
var isSwitch = false;

if (isSwitch) {
  speed = 20;
}
```

**正确写法**

```JAVASCRIPT
var speed = 10, // 动画速度
    isSwitch = false; // 动画是否启用

if (isSwitch) {
  speed = 20;
}
```

## 编码规则

1. 缩进为两个空格

2. 关键词、条件括弧后面使用空格；运算操作符号两侧使用空格；语句分割符‘,’后面使用空格

```JAVASCRIPT
var name[空格]=[空格]value;
if[空格](a,[空格]b) {
}
```

3. 左大括号"{"居行尾；右大括号"}"单独占一行，居行首

```JAVASCRIPT
if (a && b) {
}
```

4. 句末必须用分号结尾

```JAVASCRIPT
var fn = function () {
}; // 这里没有分号的话，脚本解析器会报错！！！
(function () {
   alert(1);
})();
```

5. 单行过长应在适当位置予以换行,增强可读性

```JAVASCRIPT
if (condition1 
 && condition2 
 || condition3) {
}
```

6. if、while、for、do语句的执行体总是用"{"和"}"括起来，即使在其结构体内只有一条语句

```JAVASCRIPT
if (s==100) {
 alert('shit!');
}
```

7. 语法意义相互独立的代码将用空行分隔

```JAVASCRIPT
// 前一个功能
if (a > b) {
  value = a; // 行间不用空行间隔
}

// 与上一代码行使用空行间隔
var variableName = value;
```

## 注释

1. 文件注释，文件版本、创建或者修改时间、功能、作者

```JAVASCRIPT
/**
* @file Image.js
* @description 功能详细描述
*/
```

2. 函数或者类等必须添加头描述

```JAVASCRIPT
/**
* 简述
* 功能详细描述
* @param arg1 string 参数1
* @param arg2 string 参数2，默认为0
* @return boolean 看xxx是否成功
*/
function fooFunction (arg1, arg2) {
}
```

3. 单行注释,写在代码上面

```JAVASCRIPT
//[空格]循环获取xxxx
for( var i = 0; i < obj.lenght; i++) {
}
```

4. 行尾注释注意空格

```JAVASCRIPT
var variableName = value;[空格]//[空格]注释
```