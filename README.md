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

** 1.缩进**  

每一行的层级有四个空格缩进(用Sublime配置一个table键为四个空格)。

**2.行的长度**  

每行的长度不超过80个字符，如果一行多余80个字符，应该在一个运算符后换行，并且下一行增加两级缩进(也就是8个空格)

** 3.原始值**  

字符串应该使用双引号且保持一行，避免在字符串中使用斜线另起一行。
```
//好的写法
var name = "gothic"
```

```
//不好的写法
var name = 'gothic'
```

数字应该使用十进制整数，科学计数法表示整数，十六进制整数，或者十进制浮点小数，小数点前后应当至少保留一位数字，避免使用八进制直接量

特殊值null除了下述情况下应当避免使用:
*用来初始化一个变量，这个变量可能被赋值为一个对象。  
*用来和一个已经初始化的变量比较，这个变量可以是也可以不是一个对象。  
*当函数的参数期望是对象时，被用作参数传入。  
*当函数的返回值期望是对象时，被用作返回值传出。  

```
/好的写法
var person = null;
```

```  
//好的写法 
function getPerson() {
	if (condition) {
	return new Person("gothic");
	} else {
	return null;
	}
}
```
```
//不好的写法
var person;
if (person != null) {
	doSomething();
}
```

避免使用特殊值 `undefined`。判断一个变量是否定义应该使用typeof操作符  

```
//好的写法
if (typeof variable == "undefined") {
	//do something
}  
```

**4.运算符间距 **  

二元运算符前后必须使用一个空格来保持表达式的整洁。操作符包括赋值运算符和逻辑运算符。
```
//好的写法
var found = (values[i] === item);

//好的写法
if (found && (count > 10)) {
	process(i)
}

//不好的写法,没有空格
var found = (values[i]===item);
```

**5.括号间距 **
当使用括号时，紧接左括号之后和紧接右括号之前不应该有空格。
```
//好的写法
var found = (values[i] === item);
//好的写法
if (found && (count >10)) {
	doSomething();
}
//不好的写法，左括号之后有空格
var found = ( values[i] === item);
//不好的写法，右括号之前有额外的空格
if (found && (count > 10) ) {
	doSomething();
}
```

** 6.对象直接量**  
对象直接量应该使用如下格式:
*起始左花括号应当通表达式保持同一行。  
*每个属性的名值对应当保持一个缩进，第一个属性应当在左起花括号后另起一行。  
*每个属性的名值对应当使用不含引号的属性名，其后紧跟一个冒号，而后是值。  
*倘若属性值是函数类型，函数体应当在属性名之下另起一行，而且其前后均应保留一个空行。  
*一组相关的属性前后可以插入空行以提升代码的可读性。  
*结束的右花括号应当独占一行。

```
//好的写法
var object = {
	key: value1,
	key2: value2,
	function() {
	//doSomething()
	},
	key3: value3
};
//不好的写法:不恰当的缩进
var object = {
				key1: value1,
				key2: value2,
};
```

当对象字面量作为函数时，如果值是变量，起始花括号应当同函数名再同一行。所有其余先前列出的规则同样适合。

**7.注释**
适当的注释有利于别人理解你的代码，一般以下情况应当使用注释。
*代码晦涩难懂
*可能被误认为错误的代码
*必要但并不明显的针对特定浏览器的代码
*对于对象，方法或者属性，生成文档是必要的
(1)单行注释

单行注释也有多种使用方式
*独占一行，用来解释下一行代码。
*在代码的尾部的注释，用来解释他之前的代码。
*多行，用来注释掉一个代码块。
```
//好的写法
if (condition) {

	//如果代码执行到这里，则表明通过了所有的安全性检查
	allowed();
}
//不好的写法:注释之前没有空行
if (condition) {
	//如果代码执行到这里，则表明通过了所有的安全性检查
	allowed();
}
```
```
//不好的写法：这里应当使用多行注释
//啊啊啊啊啊啊啊啊
//么么么么么
//么么么么么么么么啦啦啦啦啦拉了拉了
//lllllllllll
if (condition) {
	
	//如果代码执行到这里，则表明通过了所有的安全性检查
	allowed();
}
```
对于代码尾行注释的情况，应该确保代码结尾同注释之间至少一个缩进。
```
// 好的写法
var result = something + somethingElse;    // somethingElse will never be null
```
```
// 不好的写法：代码和注释间没有足够的空格
var result = something + somethingElse;// somethingElse will never be null
```

注释一个代码块时在连续多行使用单行注释是唯一可以接受的情况，多行注释不应该在这种情况下使用
// 好的写法
//  if (condition) {
//	doSomething();
//	thenDoSomethingElse();
}

(2)多行注释

多行文字适合在代码需要更多文字去解释的时候使用，每个多行注释都至少有如下三行：
首行仅仅包括`/*`释开始，该行不应当有其他文字。
接下来的行以`*`开头并保持左对齐，这些行可以有文字描述。
最后一行以`*/`开头并同先前行保持对齐，也不应当有其他文字。

多行注释的首行应当保持同他描述的相同层次的缩进。后续的每行应当有同样层次的缩进并附加一个空格。每一个多行代码之前应当预留一个空行。

```
// 好的写法
if (condition) {

	/*
	 * 如果代码执行到这里
	 * 说明通过了所有的安全性检测
	 */
	allowed();
}
```

``` 
// 不好的写法：注释之前无空行
if (condition) {
	/*
	 * 如果代码执行到这里
	 * 说明通过了所有的安全性检测
	 */
	allowed();
}
```

```
// 不好的写法：星号后面没有空格
if (condition) {
	
	/*
	 *如果代码执行到这里
	 *说明通过了所有的安全性检测
	 */
	allowed();
}
```

(3)注释说明

注释有时候也可以用来给一段代码添加额外的信息，比如： 
TODO:说明代码还未完成。应当保函下一步要做的事情。  
HACK:表明代码实现走了一个捷径。应当包含为何使用hack的原因。这也可能表明该问题可能会有更好的解决办法  
XXXX: 说明代码是有问题的并应当尽快修复  
FIXME: 说明代码任何可能的改动都需要评审  
这些声明可在一行也可在多行注释里使用  
```
// 好的写法
//TODO:我希望找到一种更块的方式
doSomething();
```


**8.变量声明**
所有的变量声明在使用前应该事先定义，变量定义应当放在函数开头，使用一个var表达式每行一个变量。除了首行，所有行都应该都多一层缩进。初始化的变量应当在未初始化变量之前。
```
// 好的写法
var count = 10,
	name = "gothic",
	found = false,
	empty;
```

```
// 不好的写法：多个定义在一行
var count = 10,name = "gothic",
	found = false,empty;
```


**9.函数声明**

函数应当在使用前提前定义。一个不是作为方法的函数应该使用函数定义的格式。函数名和开始圆括号之间不应该有空格，结束的圆括号和右边的花括号之间应该留一个空格。右侧的花括号应当同function关键字保持同行，开始和结束之间不应该有空格。参数名之间应当在逗号之后保留一个空格。函数体应当保持一级缩进。

```
//好的写法
function doSomething(arg1,arg2) {
	return arg1 + arg2;
}
```

```
//不好的写法:空格使用不当
function doSomething (arg1,arg2){
	return arg1 + arg2;
}
```

```
//不好的写法:函数表达式
var doSomething = function(arg1,arg2) {
	return arg1 + arg2;
}
//不好的写法：左侧花括号位置不对
function doSomething(arg1,arg2) {
	return arg2 + arg2
}
//错误的写法：使用function构造器
var doSomething = new Function("arg1","arg2","return arg1 + arg2");
```
其他函数内部定义的函数应当在var语句后立即定义。
匿名函数可能作为方法赋值给对象，或者作为其它函数的参数。function关键字同开始括号之间不应有空格。
立即被调用的函数应当在函数调用的外层用圆括号包裹


**10.命名**

变量和函数命名是个大问题。命名应仅限于数字字母字符，某些情况下也可以使用下划线。最好不要在任何命名中使用反斜杠和$。

变量命名应当采用驼峰命名格式，首写字母小写，每个单词首字母大写。变量名的第一个单词应当是一个名词以避免同函数混淆。不要在变量名中使用下划线。

函数命名也应当采用驼峰命名格式，函数命名的第一个单词应当是动词来避免同变量混淆。函数名中最好不要使用下划线。
```
//不好的写法:名词开头
function car() {
	//code
}
//不好的写法：使用下划线
function do_something() {
	//code
}
```
构造函数——通过new运算符创建新对象的函数——也应当以驼峰格式命名并且首字符大写。构造函数名称应当以非动词开头，因为new代表着创建一个对象实例的操作。

```
// 好的写法
function MyObject() {
	//代码
}
//不好的写法：小写字母和下划线
function my_Object() {
	//代码
}
```

常量的命名应当是所有字母大写，不同单词之间用单个下划线隔开。
```
//好的写法
var TOTAL_COUNT = 10;
//不好的写法:驼峰形式
var totalCount = 10;
```
对象的属性同变量的命名规则相同。对象的方法同函数的命名规则相同。如果属性或者方法是私有的。应当在之前加一个下划线。

**11.赋值**

给变量赋值时，如果右侧是含有比较语句的表达式，需要用圆括号包裹。
```
//好的方法
var flag = (i < count);
//不好的写法：遗漏括号
var flag = i < count;
```
**12.等号运算符**  
使用===和!==代替==和!=来避免弱类型转换错误。
var same = (a === b);
//不好的写法
var same = (a == b);

**13.三元操作符**  
三元操作符应当仅仅用在条件赋值语句中，而不要作为if语句的替代品。
```  
//好的写法  
var value = condition ? value1 : value2;

//不好的写法  
condition ? doSomething():do somethingElse();  
```

**14.语句**  

(1)简单语句  
每一行包含一条语句，已分号;结束  
(2)返回语句  
当返回一个值的时候不应当使用圆括号包裹，除非在某些情况下这么做可以让返回值更容易理解。  
(3)复合语句  
*复合语句是大括号括起来的语句列表。 
*括起来的语句应当较复合语句多缩进一个层级  
*开始的大括号应当在复合语句所在的行尾，结束的大括号应当独占一行且同复合语句的开始保持同样的缩进。
*当语句是控制结构的一部分时，诸如if或者for语句，所有的语句都需要大括号括起来，也包括单个语句。  
*像if一样的语句开始的关键字，其后应该紧跟一个空格，起始大括号应当在空格之后。  

```  
if (condition) {
	statements
} else if (condition) {
	statements
} else {
	statements
}  
```  
```  
for (test1; condition; update) {
	statements
}  
for (variable in object) {
	statements
}  
```  

Switch下的每个case都应该保持一个缩进，除第一个之外包括default在内的每个case都应该在之前保持一个空行  
```  
switch (value) {
	case 1:  
	/* 抛出错误 */  

	case 2:  
		doSomething();
		break;

	case 3:
		return true;

	default:  
		throw new Error(this shouldn't happen);
}  
```  
**15.留白**  

在逻辑相关的代码块之间添加空行可以提高代码的可读性。  
两行空行的情况下：  
*在不同的源代码文件之间。  
*在类和接口定义之间。  

单行空行的情况下：  
*方法之间。  
*多行或者单行注释之前。  
*方法中局部变量和第一行语句之间。 
*方法中逻辑代码块之间以提升代码的可读性。  

空格在以下情况：  
*关键词后跟括号的情况应当用空格隔开。  
*参数列表中逗号之后应当保留一个空格。  
*所有的除了点(.)之外的二元运算符，其操作数都应当用空格隔开。单目运算符的操作数之间不应该用空白隔开，诸如一元减号，递增(++),递减(--).
