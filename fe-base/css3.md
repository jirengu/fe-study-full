# 盒模型


CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。

- Margin - 清除边框区域。Margin没有背景颜色，它是完全透明
- Border - 边框周围的填充和内容。边框是受到盒子的背景颜色影响
- Padding - 清除内容周围的区域。会受到框中填充的背景颜色影响
- Content - 盒子的内容，显示文本和图像

## 边距宽高
设置宽度和高度是指Content部分的宽度和高度
	
	width:250px;
	padding:10px;
	border:5px solid gray;
	margin:15px;

div总宽度为：`250 ＋ 10*2 ＋ 5*2 + 15＊2＝ 310`

如果只有固定宽度250像素的空间，那么设置宽度为:`250-padding*2-border*2-margin*2 = content`

## 边距写法
	padding: 10px 10px 10px 10px; /* 上边距 右边距 下边距 左边距 */
	padding: 10px;                /* 等同于 10px 10px 10px 10px */
	margin: 10px 5px;             /* 等同于 10px 5px 10px 5px */
	margin: 0 auto;               /* 等同于 0 auto 0 auto */
	margin-left: auto;
	margin-right: auto;
	margin-top: 0;
	margin-bottom: 0;




## 区别
![](http://lsly1989.qiniudn.com/201503151.JPG)


<br/>


![](http://lsly1989.qiniudn.com/201503152.JPG)


W3C标准中`padding`、`border`所占的空间不在width、height范围内，大家俗称的IE的盒模型width包括`content尺寸`＋`padding`＋`border`

## 兼容方案

### 使用css3新样式box-sizing

box-sizing有两个值

1.  content-box：w3c标准盒模型
2.  border-box：“IE盒模型”

		<div style="height:200px;width:200px;border:solid 10px #333;padding:100px;box-sizing: border-box;">
		</div>


