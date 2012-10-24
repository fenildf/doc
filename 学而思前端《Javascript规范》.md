# XESUI JavaScript 规范

## 1. 目录结构

    --- js/				js根文件夹
     |---- app/             应用类，如：AutoCompete、Login
     |---- import/          根据路由规则生成的对应页面的js文件
     |---- ui/             	UI组件库文件，如：Dialog、ScrollBar
     |---- widget/       	非UI组件库文件，如：Lazyload、SwfObject
     |---- tools/			工具类文件，如：JSLint、YUICompressor
     |---- boot.js			JS异步加载之前所需的启动文件
     |---- repeater.js		路由管理文件，用于生成js的规则内容
     |---- common.js		公共JS文件
     |---- readme.md     	说明文档


## 2. 命名规则

### 2.1 变量名称以小写字母开头
### 2.2 构造器的首字母大写。如：

		function Dialog (config) {
			statement;
		}
		var win = new Dialog({...});
		
### 2.3 对象的属性或方法名采用小驼峰式(lower camel-case)。

如 `init` , `bindEvent` , `updatePosition` ：

		Dialog.prototype = {
			init: function () {},
			bindEvent: function () {},
			updatePosition: function () {}
            ...
		};
		
### 2.4 私有变量名用下划线开头。

如：`_current` , `_defaultConfig`

### 2.5 常量名全部大写，单词间用下划线分隔。

如：`CSS_BTN_CLOSE` ,  `TXT_LOADING`

## 3. 代码格式化要求

### 3.1 语句中的必要空格和缩进

#### 3.1.1 用来包含语句的"()"前后需要跟空格。
诸如： `if` / `for` / `while` / `switch ( statements ) { … }` 等

#### 3.1.2 "="前后需要跟空格

#### 3.1.3 数组成员间的","后面需要跟空格

不好：

             for (t in selected) { if (!hash[t]) deselect(t) }

好：

             for ( t in selected ) { 
               if ( !hash[t] ) {
                deselect(t); 
               }
             }

### 3.2 长语句采用断行:

不好：

> TEMPL_SONGLIST.replace('{TABLE}', da['results']).replace('{PREV_NUM}', prev).replace('{NEXT_NUM}', next).replace('{CURRENT_NUM}', current).replace('{TOTAL_NUM}', da.page_total);

好：

             TEMPL_SONGLIST.replace('{TABLE}', da['results'])
             			   .replace('{PREV_NUM}', prev)
             			   .replace('{NEXT_NUM}', next)
             			   .replace('{CURRENT_NUM}', current)
             			   .replace('{TOTAL_NUM}', da.page_total);

### 3.3 格式化对象参数：

不好：

> showSWF(id, { url: '/swf/video.swf?url=' + _href, width: 300, height: 200, params: { wmode:'transparent' }, attributes: { id: "video-player" + i, name: "video-player" + i }});

好：

              showSWF(id, {
                 url: '/swf/video.swf?url=' + _href, 
                 width: 300,
                 height: 200,
                 params: { wmode:'transparent' },
                 attributes: {
                   id: "video-player" + i,
                   name: "video-player" + i
                 }
               });
              


## 4. 校验标准

### 4.1 语句必须以分号结尾，除了for、function、if、switch、try、while以外

### 4.2 避免多余的逗号。如：var a = [1,2,3,];

### 3.3 所有循环体之间必须用“{}”包裹起来。如：

错误：

		if(a=1)
			return;
	
		或者：
		if(a=1) return;
	
	
正确

		if( a = 1 ){
			return;
		}
		
		或者：
		if( a = 1 ) { return; }
	
### 4.4 变量声明。变量声明应放在function的最上面。避免使用未声明的变量。
错：

		if (n > 0) {
			var isvalid = true;
		}

对：

		var isvalid;
		if (n > 0) {
			isvalid = true;
		}


### 4.5 不要使用with, void, evil。

### 4.6 下面类型的对象不建议用new构造：
	new Number, 
	new String, 
	new Boolean, 
	new Object(用{}代替), 
	new Array(用[]代替)。
	

### 4.7 引用对象成员用obj.prop1代替obj[“prop1”]，除非属性名是变量。


## 5. JS合并压缩

### 5.1 合并规则

### 5.2 合并压缩的文件名必须严格按照加载的顺序排序


## 6. 测试

### 6.1 所有JS文件提交SVN之前必须经由本地测试

> JS兼容性：

浏览器	|	兼容情况	|	说明
------- | --------- | -------------------
IE 6	|	  A		| 包括360、遨游2
IE 7	|	  A		|
IE 8	|	  A		|
IE 9	|	  B		|
Firefox	|	  A		|
Chrome	|	  A		|
Safari	|	  C		|
Opera	|	  C		|

* A：确保全部交互效果以及页面性能；
* B：实现主要的交互效果，确保交互体验顺畅即可
* C：基本的交互效果，能保证页面基本功能正常即可

> 本地测试工具：

* 性能测试：PageSpeed、YSlow
* 调试工具：Firebug、IE Developer Toolbar、SuperPreview、IE Debugger


### 6.2 测试机测试

- 将本地测试后的压缩文件上传至SVN，并提交至内网测试机，进行测试；
- 将内容测试通过后的文件提交至线上测试机，进行测试

## 7. 上线




