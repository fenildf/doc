# XESUI CSS 规范

## 1. CSS浏览器支持

浏览器 	| WinXP | Win7 	| OS X 
----- 	| ----- | ---- 	| -----
IE 9  	| 	A	|	A	|
IE 8  	|	A	|	A	|
IE 7  	|	B	|	B	|
IE 6  	|	B	|	B	|
Chrome	|	A	|	A	|	A
Firefox |	A	|	A	|	A
Safari  |	C	|	C	|	C
Opera 	|	C	|	C	|	C


* A级－交互和视觉完全符全设计的要求
* B级－视觉上允许有所差异，但不破坏页面的整体效果
* C级－可忽略设计上的细节，但不防碍使用

## 2. CSS目录结构
>文件存放服务器：

http://css01.xesimg.com    `前台`  
http://css02.xesimg.com 	`个人中心`

    --- css/				样式根文件夹
     |---- base/            基础样式（public.css / layout.css）
     |---- lib/             通用UI样式：head.css / foot.css
     |---- ui/             	JS组件所需样式：dialog.css / datepicker.css / foucsswitch.css
     |---- style/       	页面风格文件：blue.css / red.css / green.css
     |---- tpl.css       	模板文件，用于生成css的规则内容
     |---- readme.md     	说明文档



## 3. 命名规范


	* 文件名全部小写，必须以英文字母开头，只能出现英文字母、数字、连字符(英文句号：`.`)
	* 命名由英文单词/产品拼音/`.`连字符组成
	* 压缩后的文件以`.min`结尾，如：`xes.public.min.css`
	
## 4. 书写规范

### 4.1 统一用UTF-8编码

### 4.2 单条CSS规则的书写格式要求

单行形式适用于直接写在页面中和长文件的情况。声明写在一行。需要在“{"和"}”前后加空格。 （注：在很长的文件中，单行形式有利于检索选择器）

	.selector{property:value;property:value;}

简短规则声明（1或2个）也适用单行形式。
	
	.selector{property:value;}
	
格式化书写形式。适用于不是很长的模块文件或CSS3语法。冒号后加空格。

	.selector{property:value;property:value;}

多个(>2)selector每个占一行：

	.selector1,.selector2,.selector3{...}

规则声明的顺序：定位、盒模型（width/height/padding/border/margin）、行高、字体/字号/颜色、背景、CSS3效果等

兼容多个浏览器时，将标准规则声明写在后面，如：

	-webkit-border-radius:4px;-moz-border-radius:4px;border-radius:4px;


### 4.3 ID和Class命名。

命名不要用缩写，单词间用"-"做为连接符

   * ID是用来标识具体模块，命名必须具体且唯一，由前缀和名字组成。不要滥用ID。如： #db-video-list、#group-member-list等。
   * id是唯一的并是父级的, class是可以重复的并是子级的, 所以id仅使用在大的模块上, class可用在重复使用率高及子级 中; id原则上都是由框架文件时命名的, 为JavaScript预留钩子的除外;
   * JS预留钩子命名，以J_开头，如 J_list
   * Class是用来标识某一类型的对象，命名简洁表意清楚。如：.list。
   * class 命名单词之间用下划线连接，如：.top_list
   * 命名示例：

坏：

	#rec.gray-link.broadsmr.pl
好：

	#db-nav-main.infobox.item
	
	
### 避免滥用CSS Hack

推荐：

> 区别属性：

浏览器		|		属性			|
----------- | ----------------- |
IE 6		| _property:value	|
IE 6/7		| *property:value	|
IE 6/7/8/9	| property:value\9	|

> 区别规则：

浏览器			|					规则			
--------------- | -----------------------------------------------------------
IE 6			| * html selector { ... }	
IE 7			| *:first-child+html selector { ... }
非IE 8			| html>body selector { ... }
firefox only 	| @-moz-document url-prefix() { ... }
saf3+/chrome1+	| @media all and (-webkit-min-device-pixel-ratio:0) { ... } 




