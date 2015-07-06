# 常见样式效果

## width & height

这两个属性用来定义元素的宽度和高度，使用很简单

	<div style="width:300px;"> 123 </div>
	<img src="https://www.baidu.com/img/bdlogo.png" style="height:100px;"/>

但这两个属性并不是所有的元素都生效

对于`p`、`div`等独占一行的块元素是可以随意使用的，但是对于`span`等行内元素是不生效的，行内元素空间靠内容撑开

## font、文本

1.  font-size：字体大小
2.  font-family：字体，宋体、微软雅黑、Arial等
3.  font-weight：文字粗度，常用的就是默认值`regular`和粗体`bold`
5.  line-height：行高，可以用百分比、倍数或者固定尺寸

&nbsp;

    span{
      line-height: 1.5;
      font-size: 14px;
      font-family: Arial,'微软雅黑','宋体';
      font-weight:bold;
    }

> Chrome等浏览器规定汉字的最小尺寸是`12px`，所以设置更小的尺寸都显示为12px

1.  text-align：文本对其方式 `left`、`center`、`right`、`justify`
2.  text-indent：文案第一行缩进距离
3.  text-decoration： `none`、`underline`、`line-through`、`overline`
4.  color：文字颜色


&nbsp;

		font:bold 12px/1.8em Arial;

可以缩写为一句： 但文字缩写一定要具有字号、字体样式这两个属性。行高用`/`分隔

## background


|属性	|描述|
|---|---|
|background|	简写属性，作用是将背景属性设置在一个声明中|
|background-attachment|	背景图像是否固定或者随着页面的其余部分滚动|
|background-color|	设置元素的背景颜色|
|background-image|	把图像设置为背景|
|background-position|	设置背景图像的起始位置|
|background-repeat|	设置背景图像是否及如何重复|

* background-position：默认左上角
	* x y
	* x% y%
	* [top | center | bottom] [left | center | right]

* background-repeat
	* no-repeat：背景图片在规定位置
	* repeat-x：图片横向重复
	* repeat-y：图片纵向重复
	* repeat：全部重复


&nbsp;

	background-color: #F00;
	background-image: url(background.gif);
	background-repeat: no-repeat;
	background-attachment: fixed;
	background-position: 0 0;

可以缩写为一句：

	  background: #F00 url(background.gif) no-repeat fixed 0 0;

## border

* border-width：边框宽度
* border-color：边框颜色
* border-style：边框样式（`solid`、`dashed`）

支持合写

	border: solid 1px #333;



## padding

padding代表内边距，有四个方向的值，可以合写

* padding-top
* padding-right
* padding-bottom
* padding-left

值可以是数值也可以是百分比（相对于父容器、不是自身）

	padding: 20px; /* padding: 20px 20px 20px 20px; */
	padding: 10px 20px; /* padding: 10px 20px 10px 20px; */
	padding: 10px 20px 30px; /* padding: 10px 20px 30px 20px; */

## margin

外边距，规则和padding一样，但是数值可以是负数，而且父边距在布局中十分有用处



**水平对齐**

对于宽度固定的块元素，设置左右margin值为`auto`可以达到元素水平对齐的效果

	<div style="width:600px;margin:0 auto;"></div>


## display
用于设置元素的显示类型，常用的值有: none, inline, inline-block, block, table-cell;

- none: 隐藏该元素，不占用文档流
- inline: 以行内元素的形式展示
- inline-block: 行内块元素
- block: 块级别元素
- table-cell: 以表格方式展示，常用于垂直居中

[例子：display](http://jsbin.com/bunav/1/edit?html,output)

display:none和visibility:hidden区别：

