# CSS、CSS选择器
CSS全称是 Cascading Style Sheets，翻译过来就是层叠样式表

## 引入方式

CSS的引入一般有三种

### 外部资源引入

	<link rel="stylesheet" type="text/css" href="xxx.css">

### style标签

	<style type="text/css">
   div{
		color: red;
		font-size:12px;
	 }
	</style>

### 内联style属性

	<div style="color:red; font-size:12px;">123</div>


## 常用选择器
#### 1、id选择器
选择设置id的元素

    <style>
        #div1{
            color: red;
        }
    </style>
    <div>div</div>
    <div id="div1">div1</div>
    <div id="div2">div2</div>

#### 2、class选择器
选择有相同class的元素

    <style>
        .c1{
            color: red;
        }
        .c2{
            background-color: yellow;
        }
    </style>
    <div class="c1 c2">c1, c2</div>
    <div class="c2">c2</div>
    <div class="c1">c1</div>

#### 3、属性选择器
以某个属性做为选择依据

    input[type="text"]
    {
      width:150px;
      display:block;
      margin-bottom:10px;
      background-color:yellow;
      font-family: Verdana, Arial;
    }

    input[type="button"]
    {
      width:120px;
      margin-left:35px;
      display:block;
      font-family: Verdana, Arial;
    }


#### 4、分组选择器
可以对选择器进行分组，被分组的选择器对应的元素就有相同的样式。
用逗号将需要分组的选择器分开。
    
    <style>
        h1, .p1{
          color: red;
        }
    </style>

h1和.p1都拥有相同的属性红色。


#### 5、派生选择器
选择某个元素下的子元素，通常用于作用域隔离，如
    
    <style>
        .mod-box h1{
            color: red;
        }
    </style>
    <h1>这是大标题</h1>
    <div class="mod-box">
        <h1>这是mod-box里的标题</h1>
        <div class="content">这是mod-box的内容</div>
    </div>

让.mod-box里的h1变为红色，外面的h1不变色。

## 选择器汇总
### 基础选择器

选择器 	| 含义
:---	| :----
\*		| 通用元素选择器，匹配页面任何元素（这也就决定了我们很少使用）
\#id 	| id选择器，匹配特定id的元素
.class	| 类选择器，匹配class**包含**(不是等于)特定类的元素
element	| 标签选择器

	* {
		font-family: '微软雅黑';
	}

	#id-selector{
		color: #333;
	}

	.class-selector{
		background: #f1f1f1;
	}

	p {
		height: 50px;
		line-height: 50px;
	}



### 组合选择器

选择器			| 含义
:---			| :---
E,F				| 多元素选择器，用`,`分隔，同时匹配元素E或元素F
E F				| 后代选择器，用空格分隔，匹配E元素所有的**后代**（不只是子元素、子元素向下递归）元素F
E>F				| 子元素选择器，用`>`分隔，匹配E元素的所有**直接子元素**
E+F				| 直接相邻选择器，匹配E元素之后的相邻的同级元素F
E~F				| 普通相邻选择器（弟弟选择器），匹配E元素之后的同级元素F（无论直接相邻与否）
.class1.class2	| id和class选择器和选择器连写的时候中间没有分隔符，`.` 和 `#` 本身充当分隔符的元素
element#id		| id和class选择器和选择器连写的时候中间没有分隔符，`.` 和 `#` 本身充当分隔符的元素

### 属性选择器

选择器					| 含义
---						| ---
E[attr]					| 匹配所有具有属性attr的元素，div[id]就能取到所有有id属性的div
E[attr = value]			| 匹配属性attr值为value的元素，div[id=test],匹配id=test的div
E[attr ~= value]		| 匹配所有属性attr具有多个空格分隔、其中一个值等于value的元素
E[attr ^= value]		| 匹配属性attr的值以value**开头**的元素
E[attr $= value]		| 匹配属性attr的值以value**结尾**的元素
E[attr *= value]		| 匹配属性attr的值**包含**value的元素

### 伪类选择器

选择器					|	含义
---						|	---
E:first-child			|	匹配元素E的第一个子元素
E:link					|	匹配所有未被点击的链接
E:visited				|	匹配所有已被点击的链接
E:active				|	匹配鼠标已经其上按下、还没有释放的E元素
E:hover					|	匹配鼠标悬停其上的E元素
E:focus					|	匹配获得当前焦点的E元素
E:lang(c)				|	匹配lang属性等于c的E元素
E:enabled				|	匹配表单中可用的元素
E:disabled				|	匹配表单中禁用的元素
E:checked				|	匹配表单中被选中的radio或checkbox元素
E::selection			|	匹配用户当前选中的元素
E:root					|	匹配文档的根元素，对于HTML文档，就是HTML元素
E:nth-child(n)			|	匹配其父元素的第n个子元素，第一个编号为1
E:nth-last-child(n)		|	匹配其父元素的倒数第n个子元素，第一个编号为1
E:nth-of-type(n)		|	与:nth-child()作用类似，但是仅匹配使用同种标签的元素
E:nth-last-of-type(n)	|	与:nth-last-child() 作用类似，但是仅匹配使用同种标签的元素
E:last-child			|	匹配父元素的最后一个子元素，等同于:nth-last-child(1)
E:first-of-type			|	匹配父元素下使用同种标签的第一个子元素，等同于:nth-of-type(1)
E:last-of-type			|	匹配父元素下使用同种标签的最后一个子元素，等同于:nth-last-of-type(1)
E:only-child			|	匹配父元素下仅有的一个子元素，等同于:first-child:last-child或 :nth-child(1):nth-last-child(1)
E:only-of-type			|	匹配父元素下使用同种标签的唯一一个子元素，等同于:first-of-type:last-of-type或 :nth-of-type(1):nth-last-of-type(1)
E:empty					|	匹配一个不包含任何子元素的元素，文本节点也被看作子元素
E:not(selector)			|	匹配不符合当前选择器的任何元素
