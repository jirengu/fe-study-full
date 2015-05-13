# HTML结构、样式引入、常见标签
HTML: HyperText Markup Language，超文本标记语言
HTML5: HTML 5.0, HTML最新的修订版本

## 基本结构

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
		<link rel="stylesheet" href="http://1688.com/cart/merge.css">
		<style>
			#doc{
			}
		</style>
	</head>
	<body>
		<h1>这是大标题</h1>
		<p>这是段落</p>
		<a href="http://www.1688.com" title="1688">这是链接</a>
		
		<script src="http://1688.com/cart/merge.js"></script>
	</body>
	</html>

##HTML常见标签及其属性


### 标题 h1~h6

	<h1>h1</h1>
	<h4>h4</h4>
	<h6>h6</h6>

### 段落和块

	<p>Text</p>
	<div>Text</div>

区别

1. div就是普通的块标签，多用于布局；p是语义化的段落标签，用于文章分段
2. div默认没有边距，p标签为了表示文章分段，有默认的间距


### 行内书写

	<span>Text</span>

使用 `<span>` 来组合行内元素，以便通过样式来格式化它们


### 图片

	<img  src="xxx.jpg" alt="图片替代文案"/>

属性

1. src：图片地址
2. alt： 图片因为网络等原因未成功加载时候的显示文案内容
3. width/height：可以是像素值或者相对于父容器的百分比，两个属性仅设置一个，另外一个值会按相应等比缩放

###  有序列表

	<ol>
		<li>Coffee</li>
		<li>Tea</li>
		<li>Milk</li>
	</ol>

<ol>
	<li>Coffee</li>
	<li>Tea</li>
	<li>Milk</li>
</ol>
### 无序列表

	<ul>
	  <li>Coffee</li>
	  <li>Tea</li>
	  <li>Milk</li>
	</ul>

<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
### a
超链接

	<a target="_blank" href="http://www.baidu.com/">百度</a>
	<a href="mailto:xxx@qq.com">联系我们</a>
	<a href="#menu1">联系我们</a>

target = "_blank"：新的选项卡打开

## 按钮

	<button>按钮</button>

<button>按钮</button>
## table
	<style>
	table{
	  border-collapse: collapse;
	  width: 100%;
	}
	th{
	  background-color: #22aaaa;
	}
	th, td{
	  text-align: center;
	  border: 1px solid green;
	  line-height: 30px;
	} 
	</style>   
	
	<table>
	    <tr>
	        <th>姓名</th>
	        <th>性别</th>
	    </tr>
	    <tr>
	        <td>小明</td>
	        <td>男</td>
	    </tr>
	    <tr>
	        <td>小花</td>
	        <td>女</td>
	    </tr>
	</table>
<style>
	#mytable{
	  display: table;
	  border-collapse: collapse;
	  width: 100%;
	}
	#mytable th{
	  background-color: #22aaaa;
	}
	#mytable th, #mytable td{
	  text-align: center;
	  border: 1px solid green;
	  line-height: 30px;
	}     
</style>
<table id="mytable">
    <tr>
        <th>姓名</th>
        <th>性别</th>
    </tr>
    <tr>
        <td>小明</td>
        <td>男</td>
    </tr>
    <tr>
        <td>小花</td>
        <td>女</td>
    </tr>
</table>
