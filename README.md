# TMTPOST-Front-end-Web-Development-Norms 钛媒体前端开发规范
![TMTPOST](http://www.tmtpost.com/public/css/img/tmt_logo.png)

本文为钛媒体[TMTPOST](http://www.tmtpost.com)前端开发团队遵循和约定的开发规范，为了提高代码的规范性和可维护性，望相关人员准守并维护本规范。

本文会根据实际使用情况不断的进行维护更新！

2016年11月16日 下午12:18:37
## 规范内容
***

### HTML编码规范

***
#### 语法

* 用两个空格来代替制表符（tab） -- 这是唯一能保证在所有环境下获得一致展现的方法。
* 嵌套元素应当缩进一次（即两个空格）。
* 对于属性的定义，确保全部使用双引号，绝不要使用单引号。
* 不要在自闭合（self-closing）元素的尾部添加斜线 -- [HTML5 规范](href "http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag")中明确说明这是可选的。
* 不要省略可选的结束标签（例如，\</li> 或 \</body>）。
	
		<!DOCTYPE html>
		<html>
			<head>
				<title>Page title</title>
			</head>
			<body>
				<img src="images/company-logo.png" alt="Company">
				<h1 class="hello-world">Hello, world!</h1>
			</body>
		</html>
	
***
####HTML5 doctype
为每个 HTML 页面的第一行添加标准模式（standard mode）的声明，这样能够确保在每个浏览
器中拥有一致的展现。

	<!DOCTYPE html>
	<html>
		<head>
		</head>
	</html>
***
####语言属性
根据 HTML5 规范：

		<html lang="zh-CN">
			<!-- ... -->
		</html>
	
####基本meta信息
好的meta，对呀页面的seo和不同浏览器的呈现一致性非常重要，页面中必须包含的mete信息如下，

字符编码

	<meta charset="UTF-8">

IE 兼容模式 设置为edge 

	<meta http-equiv="X-UA-Compatible" content="IE=Edge">

页面的tdk信息

	<title>我是页面的标题 </title>
	<meta name="description" content="hello">//网页描述
	<meta name="keywords" content="a,b,c">//关键字,“，”分隔

内容终端页设置author
	<meta name="author" content="hopekayo, hopekayo@gmail.com">

为移动设备添加viewport
* width: 浏览器宽度，输出设备中的页面可见区域宽度；
* device-width: 设备分辨率宽度，输出设备的屏幕可见宽度；
* initial-scale: 初始缩放比例；
* maximum-scale: 最大缩放比例；

	<meta name="viewport" content="width=device-width; initial-scale=1.0, maximum-scale=1.0, user-scalable=no">



####引入 CSS 和 JavaScript 文件

根据 HTML5 规范，在引入 CSS 和 JavaScript 文件时一般不需要指定 type 属性，因为 text/css 和 text/javascript 分别是它们的默认值。

* css引入一般放在head标签里面
* JavaScript引入放在底部
	<!-- External CSS -->
	<link rel="stylesheet" href="code-guide.css">

	<!-- In-document CSS -->
	<style>
	  /* ... */
	</style>

	<!-- JavaScript -->
	<script src="code-guide.js"></script>

####属性


HTML 属性应当按照以下给出的顺序依次排列，确保代码的易读性。

* class
* id, name
* data-*
* src, for, type, href
* title, alt
* aria-*, role async defer
* disabled checked selected

属性值尽量语义化
class 用于标识高度可复用组件，因此应该排在首位。
id 独一无二的标识（一个页面不能出现相同id的标签），用于标识具体组件，应当谨慎使用，因此排在第二位。

布尔（boolean）型属性 **不用赋值**，排在最后。

属性的定义，统一使用**双引号**，不准出现单引号或者没有引号。

img标签必须设置alt属性，a标签当标签内非文字时必须设置title属性

####Class 与 ID
* class 应以功能或内容命名，不以表现形式命名，尽量避免无样式的class存在；
* class 与 id 单词字母小写，多个单词组成时，采用中横线 - 或下划线 _ 分隔，更推荐使用下划线；
* 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class；
* 用于js绑定的class或id，以js—或js_开头:

		<!-- Not recommended -->
		<div class="click left contentWrapper "></div>

		<!-- Recommended -->
		<div id="js-click" class="sidebar content-wrapper"></div>

####减少标签的数量
编写 HTML 代码时，尽量避免多余的父元素。

	<!-- Not so great -->
	<span class="avatar">
	  <img src="...">
	</span>

	<!-- Better -->
	<img class="avatar" src="...">

####JavaScript 生成的标签
通过 JavaScript 生成的标签让内容变得不易查找、编辑，并且降低性能。能避免时尽量避免。



####嵌套

a 不允许嵌套 div这种约束属于语义嵌套约束，与之区别的约束还有严格嵌套约束，比如a 不允许嵌套 a。

严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

语义嵌套约束

* \<li> 用于 \<ul> 或 \<ol> 下；
* \<dd>, \<dt> 用于 \<dl> 下；
* \<thead>, \<tbody>, \<tfoot>, \<tr>, \<td> 用于 \<table> 下；

严格嵌套约束

* inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
* \<a>里不可以嵌套交互式元素\<a>、\<button>、\<select>等;
* \<p>里不可以嵌套块级元素\<div>、\<h1>~\<h6>、\<p>、\<ul>/\<ol>/\<li>、\<dl>/\<dt>/\<dd>、\<form>等。


####语义化
通常情况下，每个标签都是有语义的，此外语义化的 HTML 结构，有助于机器（搜索引擎）理解，另一方面多人协作时，能迅速了解开发者意图。

* 尽量使用语言话标签， 如  article aside details figcaption figure footer header main mark nav section summary time
* 尽量使用语义化的属性值 


****
### CSS编码规范

####代码组织
* CSS换行制表：使用 4 个空格，而非[tab];
* 以组件为单位组织代码段；并加上合理注释说明组件；最少以两个单词命名，通过 -/_ 分离，例如：点赞按钮 (.like-button)
* 声明块的左括号 { 前添加一个空格；声明块的右括号 } 应单独成行；
* 为了获得更准确的错误报告，每条声明都应该独占一行；以逗号分隔的选择器也最好单独成行；
* 所有声明语句都应当以分号结尾, 最后一行虽然是可选的，但如果省略更容易出错；
* 不要使用 @import；
* 必须添加浏览器厂商前缀，可以使用工具完成；
* 减少html 中的css的代码，除非相对独立的功能


###代码优化
* 尽量使用class选择器
* 尽量避免css污染，除了组件代码块或者工具类样式，尽量避免全局样式；
* 尽量少使用元素选择器，尤其尽量避免元素选择器嵌套；
* 尽量避免在CSS中使用大量的ID选择器；避免元素选择器和 Class、ID 叠加使用；
* 经常出现的，避免使用属性选择器；
* 避免选择器嵌套层级过多，尽量少于 3 级；
* 声明语句中的 : 后应添加一个空格；
* 对于属性值或颜色参数，省略小于 1 的小数前面的 0 （例如，.5 代替 0.5；-.5px 代替 -0.5px）。
* 十六进制值应该全部小写，例如，#fff ；尽量简写用#ddd 代替 #dddddd；
* 避免为 0 值指定单位，例如，用 margin: 0; 代替 margin: 0px;
* 合理使用代码继承，避免重复代码；
* 慎重选择高消耗的样式
 * box-shadows
 * border-radius
 * transparency
 * transforms
 * CSS filters（性能杀手）
* 避免过分重排，覆盖，浏览器需要重新计算布局位置与大小
* 不滥用 Float，Float在渲染时计算量比较大，尽量减少使用
* 正确使用 Display 的属性
 * display: inline后不应该再使用 width、height、margin、padding 以及 float；
 * display: inline-block 后不应该再使用 float；
 * display: block 后不应该再使用 vertical-align；
 * display: table- 后不应该再使用 margin 或者 float；
* 尽量使用animate实现动画，translate实现变形，避免使用js（setTimeout, setInterval.）、jQuery animate()等

#编辑器配置

* 用4个空格代替制表符（soft-tab 即用空格代表 tab 符）。
* 保存文件时，删除尾部的空白符。
* 设置文件编码为 UTF-8。
* 在文件结尾添加一个空白行。



## 声明顺序
推荐的样式编写顺序

* Positioning
* Box model
* Typographic
* Visual

demo：

	.declaration-order {
	    /* Positioning */
	    position: absolute;
	    top: 0;
	    right: 0;
	    bottom: 0;
	    left: 0;
	    z-index: 10;
	
	    /* Box model */
	    display: block;
	    box-sizing: border-box;
	    width: 100px;
	    height: 100px;
	    padding: 10px;
	    border: 1px solid #e5e5e5;
	    border-radius: 3px;
	    margin: 10px;
	    float: right;
	    overflow: hidde;

	    /* Typographic */	
	    font: normal 13px "Helvetica Neue", sans-serif;
	    line-height: 1.5;
	    text-align: cente;

	    /* Visual */	
	    background-color: #f5f5f5;
	    color: #fff;
	    opacity: .1;      
	
	    /* Other */
	    cursor: pointer;
	}

****
###JS 编码规范：

* 文件编码统一为utf-8, 书写过程过, 每行代码结束必须有分号;
* 命名语义化, 尽可能利用英文单词或其缩写(驼峰式或下划线);
* 引入jQuery库,库和插件的命名规则为 库名称-版本号-是否为压缩.js 
* 常量, 使用全部字母大写，单词间下划线分隔的命名方式。
* boolean 类型的变量使用 is 或 has 开头。
* 不要在 Array 上使用 for-in 循环， for-in 循环只用于 object/map/hash 的遍历
* 可以的时候三元操作符(?:)、&& 和 ||，用于替代 if 条件判断语句
* 使用namespace，避免js 全局污染
* 正则表达式仅准用 .test() 和 .exec() 。避免用 "string".match() ；
* 推荐使用'use strict'，严格模式避免很多错误。
* 减少html 中的js的代码，除非相对独立的功能

* 推动es6，使用[babel](href 'https://babeljs.io/')解决兼容性

#### jquery 使用规范
* jQuery变量要求首字符为 '$', 私有变量:首字符为'_'; 要求变量集中声明, 避免全局变量.
* 使用最新版本的 jQuery，版本越新，性能越好；
* 不要将 CSS 写在 jQuery 里面；
* 对 Ajax 加载的 DOM 元素绑定事件时尽量使用事件委托。


		// Not recommended
		$("#list a").on("click", myClickHandler);

		// Recommended
		$("#list").on("click", "a", myClickHandler);

###选择器

* 尽可能的使用 ID 选择器，
* 在父元素中选择子元素使用 .find() 方法性能会更好

		// Not recommended
		var $productIds = $("#products .class");

		// Recommended
		var $productIds = $("#products").find(".class");
#链式写法
* 尽量使用链式写法而不是用变量缓存或者多次调用选择器方法；

		 // Not recommended
		$("#myDiv").addClass("error");
		$("#myDiv").show();
		// Recommended
		$("#myDiv").addClass("error").show();
* 当链式写法超过三次或者因为事件绑定变得复杂后，使用换行和缩进保持代码可读性；

		$("#myLink")
		  .addClass("bold")
		  .on("click", myClickHandler)
		  .on("mouseover", myMouseOverHandler)
		  .show();


####js 性能优化

* 浏览器遍历 DOM 元素的代价是昂贵的。 简化DOM和减少不必要DOM操作
* 异步加载第三方内容 为script增加 async（仅适用于外部脚本）
* 尽量不使用 animate() 方法
* 避免使用 eval()，setTimeOut使用调用函数
* 只使用一次的函数使用匿名函数
* 禁止使用 slideUp/Down() fadeIn/fadeOut() 等方法；
* 缓存数组长度

		var arr = new Array(1000),
		len, i;
		// Recommended - size is calculated only 1 time and then stored
		for (i = 0, len = arr.length; i < len; i++) {
		}
		// Not recommended - size needs to be recalculated 1000 times
		for (i = 0; i < arr.length; i++) {
	
		}
	
****
### 注释约定

在必要的地方添加注释，尤其是用到特殊算法的地方，

#### 文件注释

创建前端文件时添加文件注释

	/*
	@author:         hopeakyo@gmail.com
	@description:    
	@time:           2016-12-19 2:10 PM
	*/

修改文件时注释

	/*
	@editor:          hopeakyo@gmail.com
	@description:    content整理后
	@time:           2016-12-19 2:10 PM
	*/
简写 
	// by hopekayo@gmail.com  实现某某功能 2016-12-19 2:10
****

###活动页面制作规范

###EDM页面制作规范

	