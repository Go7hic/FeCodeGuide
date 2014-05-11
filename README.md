FeCodeStyle
===========

前端代码书写规范


总结自己的前端书写规范，包括html ,css ,js.

参照了Bootstrap的规范指南。


##**0x0 介绍**
	

我一直觉得规范没有绝对的，每个团队都有自己的代码规范，每个都有自己习惯的代码风格，规范是一面镜子，对于好的规范我们应该去参考学习，从合作效率,规范上来讲我们应该去适应团队的规范,即使有的时候和你的习惯不一样，真正牛逼的人可以习惯适应各种风骚的代码。 	
##**0x1 html规范** 	
**1.语法**

 - 使用四个空格为一次缩进(Tab)。嵌套的节点应该缩进。

 	

 - 在属性上，使用双引号，不要使用单引号。
 - 不要在自动闭合标签结尾处使用斜线 - HTML5 规范 指出他们是可选的。

 	

 - 不要忽略可选的关闭标签。

**2.使用html5 doctype** 	
```<!DOCTYPE html>```

**3.指定网站的语言** 	
```
    <html lang="zh-CN"> 	
       <!-- ... --> 	
    </html>
```
**4.使用UTF-8编码**

**5.IE兼容模式**

```<meta http-equiv="X-UA-Compatible" content="IE=Edge">```
**6.正确引入css,js文件** 	

    <!-- External CSS -->	 	
    <link rel="stylesheet" href="code-guide.css">
    
    <!--  CSS --> 
    <style> 		
    /* ... */ 	
    </style>
    
    <!-- JavaScript --> 	
    <script src="code-guide.js"></script>
    
**7. 按顺序书写html属性** 

HTML 属性应该按照特定的顺序出现以保证易读性。
```
class 	
id, name 	
data-* 	
src, for, type, href 	
title, alt 	
aria-*, role 	
```
Classes 是为高可复用组件设计的，所以他们处在第一位。Ids 更加具体而且应该尽量少使用（例如, 页内书签），所以他们处在第二位。

**8.可以不必为Boolean属性取值** 

```<input type="checkbox" value="1" checked="chencked">```
可以写成
```<input type="checkbox" value="1" checked>```

**9.尽量减少标签数量** 	
编写 HTML 代码时，尽量避免多余的父元素。很多时候，这需要迭代和重构来实现。请看下面的案例：
```
<!-- 不推荐 -->
<span class="avatar">
  <img src="...">
</span>

<!-- 推荐 -->
<img class="avatar" src="...">
```

**10.标签嵌套规范** 

.a 块元素可以包含内联元素或某些块元素, 但内联元素却不能包含块元素, 它只能包含其它的内联元素;
```
<div><h1></h1><p></p></div> --- 对
<a href="#"><span></span></a> --- 对
<span><div></div></span> --- 错
```
.b 块级元素不能放在`<p>`里面;
```
<p><ol><li></li></ol></p> --- 错
<p><div></div></p> --- 错
```
.c 有几个特殊的块级元素只能包含内嵌元素, 不能再包含块级元素, 这几个特殊的标签是;
`h1`, `h2`, `h3`, `h4`, `h5`, `h6`, `p`, `dt` 

.d `<li> `内可以包含 `<div> `标签;

.e 块级元素与块级元素并列, 内嵌元素与内嵌元素并列;

```
<div><h2></h2><p></p></div> --- 对
<div><a href="#"></a><span></span></div> --- 对
<div><h2></h2><span></span></div> --- 错
```

**11.对页面中的每一个html模块使用注释包裹** 

```
<!-- content --> 	
 <div class="container"> 		
 ... 	
  </div> 	
 <!-- content end -->
```
**12.修改了别人的代码最好添加注释**


##**0x2 css规范指南**

**1.语法**

 - 使用四个空格缩进(Tab)。
 - 使用组合选择器时，保持每个独立的选择器占用一行。

 
 - 为了代码的易读性，在每个声明的左括号前增加一个空格。
 - 声明块的右括号应该另起一行。

 
 - 每条声明 : 后应该插入一个空格。

 - 每条声明应该只占用一行来保证错误报告更加准确。

 - 所有声明应该以分号结尾。虽然最后一条声明后的分号是可选的，但是如果没有他，你的代码会更容易出错。

 - 逗号分隔的取值，都应该在逗号之后增加一个空格。

 - 不要在颜色值 `rgb()` 和 `rgba()`中增加空格，并且不要带有取值前面不必要的 `0` (比如，使用 `.5` 替代 `0.5`)。

 - 所有的十六进制值都应该使用小写字母，例如`#fff`。因为小写字母有更多样的外形，在浏览文档时，他们能够更轻松的被区分开来。

 - 尽可能使用短的十六进制数值，例如使用 #fff 替代 `#ffffff`。

 - 为选择器中得属性取值添加引号，例如 `input[type="text"]`。 他们只在某些情况下可有可无，所以都使用引号可以增加一致性。

 - 不要为 0 指明单位，比如使用`margin: 0;` 代替` margin: 0px;`。
 
 
举个例子:
```
    .selector,
    .selector-secondary,
    .selector[type="text"] {
      padding: 15px;
      margin: 0 0 15px;
      background-color: rgba(0,0,0,.5);
      box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
    }
```
**2.声明顺序**

相关的属性声明应该以下面的顺序分组处理：

`Positioning`

`Box model` 盒模型

`Typographic` 排版

`Visual` 外观

Positioning 处在第一位，因为他可以使一个元素脱离正常文本流，并且覆盖盒模型相关的样式。盒模型紧跟其后，因为他决定了一个组件的大小和位置。

其他属性只在组件 内部 起作用或者不会对前面两种情况的结果产生影响，所以他们排在后面。
这里推荐一个网站给大家，http://csscomb.com/online/      
可以在线格式化你的css代码，还有插件哦。
```

    .declaration-order {
      /* Positioning */
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      z-index: 100;
    
      /* Box-model */
      display: block;
      float: right;
      width: 100px;
      height: 100px;
    
      /* Typography */
      font: normal 13px "Helvetica Neue", sans-serif;
      line-height: 1.5;
      color: #333;
      text-align: center;
    
      /* Visual */
      background-color: #f5f5f5;
      border: 1px solid #e5e5e5;
      border-radius: 3px;
    
      /* Misc */
      opacity: 1;
    }
```

**3.媒体查询位置**

尽量将媒体查询的位置靠近他们相关的规则。不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部。这样做只会让大家以后更容易忘记他们。这里是一个典型的案例。

```
    .element { ... }
    .element-avatar { ... }
    .element-selected { ... }
    
    @media (min-width: 480px) {
      .element { ...}
      .element-avatar { ... }
      .element-selected { ... }
    }
```

**4.不要使用 @import**

**5.前缀属性**


当使用厂商前缀属性时，通过缩进使取值垂直对齐以便多行编辑。

```
    .selector {
      -webkit-box-shadow: 0 1px 2px rgba(0,0,0,.15);
              box-shadow: 0 1px 2px rgba(0,0,0,.15);
    }
```

**6.单条声明的声明块**

在一个声明块中只包含一条声明的情况下，为了易读性和快速编辑可以考虑移除其中的换行。所有包含多条声明的声明块应该分为多行。

```
    /* Single declarations on one line */
    .span1 { width: 60px; }
    .span2 { width: 140px; }
    .span3 { width: 220px; }
    
    /* Multiple declarations, one per line */
    .sprite {
      display: inline-block;
      width: 16px;
      height: 15px;
      background-image: url(../img/sprite.png);
    }
    .icon           { background-position: 0 0; }
    .icon-home      { background-position: 0 -20px; }
    .icon-account   { background-position: 0 -40px; }
```

**7.属性简写**

坚持限制属性取值简写的使用，属性简写需要你必须显式设置所有取值。常见的属性简写滥用包括:
`padding`
`margin`
`font`
`background`
`border`
`border-radius`

大多数情况下，我们并不需要设置属性简写中包含的所有值。例如，HTML 头部只设置上下的 margin，所以如果需要，只设置这两个值。过度使用属性简写往往会导致更混乱的代码，其中包含不必要的重写和意想不到的副作用。
```
    /* 坏习惯 */
    .element {
      margin: 0 0 10px;
      background: red;
      background: url("image.jpg");
      border-radius: 3px 3px 0 0;
    }
```   
```
    /* 好习惯 */
    .element {
      margin-bottom: 10px;
      background-color: red;
      background-image: url("image.jpg");
      border-top-left-radius: 3px;
      border-top-right-radius: 3px;
    }
```

**8.代码注释**

代码是由人来编写和维护的。保证你的代码是描述性的，包含好的注释，并且容易被他人理解。好的代码注释传达上下文和目标。不要简单地重申组件或者 class 名称。每个注释块之间最好空一行。

```
    /* 不好的习惯 */
    /* Modal header */
    .modal-header {
      ...
    }
    
    /* 好的规范 */
    /* Wrapping element for .modal-title and .modal-close */
    .modal-header {
      ...
    }
```

**9.Class 命名**

保持 Class 命名为全小写，可以使用短划线（不要使用下划线和 camelCase 命名）。短划线应该作为相关类的自然间断。(例如，.btn 和 .btn-danger)。
避免过度使用简写。.btn 可以很好地描述 button，但是 .s 不能代表任何元素。
Class 的命名应该尽量短，也要尽量明确。
使用有意义的名称；使用结构化或者作用目标相关，而不是抽象的名称。
命名时使用最近的父节点或者父 class 作为前缀。
使用 .js-* classes 来表示行为(相对于样式)，但是不要在 CSS 中包含这些 classes。

```
/* 不好的规范 */

    .t { ... }
    .red { ... }
    .header { ... }

/* 好的规范 */

    .tweet { ... }
    .important { ... }
    .tweet-header { ... }
```

**10.选择器**

使用 classes 而不是通用元素标签来优化渲染性能。
避免在经常出现的组件中使用一些属性选择器 (例如，[class^="..."])。浏览器性能会受到这些情况的影响。
减少选择器的长度，每个组合选择器选择器的条目应该尽量控制在 3 个以内。
只在必要的情况下使用后代选择器 (例如，没有使用带前缀 classes 的情况).
```
/* 不好的习惯 */

    span { ... }
    .page-container #stream .stream-item .tweet .tweet-header .username { ... }
    .avatar { ... }

/* 好的规范 */

    .avatar { ... }
    .tweet-header .username { ... }
    .tweet .avatar { ... }
```

**11.CSS文件头部声明 @charset**


为了避免 HTML 和 CSS 文件编码不同时造成中文解析乱码，造成的不必要的麻烦，CSS 文件头部统一加上文件对应的编码，例如文件编码为 UTF-8 时：

`@charset "utf-8"`;
/* 开始书写样式 */
需要注意的是：

`@charset `前面不能有任何字符。
`@charset `必须出现在 CSS 文件的最开始。
注：在使用 SASS 时如果不指定 @charset 也可能造成乱码。


##**0x3 JavaScript规范指南**

