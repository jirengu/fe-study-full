# 定位

## 基本属性

要想了解CSS元素定位就需要了解`position`属性了，position属性有几个常用值如下

值			|	属性
:---		|	:---
inherit		|	规定应该从父元素继承 position 属性的值
static		|	默认值,没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声明）
relative	|	生成相对定位的元素，相对于元素本身正常位置进行定位,因此，`left:20px` 会向元素的 left 位置添加20px
absolute	|	生成绝对定位的元素，相对于`static`定位以外的第一个祖先元素（offset parent）进行定位,元素的位置通过 `left`, `top`, `right` 以及 `bottom` 属性进行规定
fixed		|	生成绝对定位的元素，相对于浏览器窗口进行定位。元素的位置通过 `left`, `top`, `right` 以及 `bottom` 属性进行规定

##  普通流与相对定位

CSS有三种基本的定位机制：普通流，相对定位和绝对定位

普通流是默认定位方式，在普通流中元素框的位置由元素在html中的位置决定，元素position属性为static或继承来的static时就会按照普通流定位，这也是我们最常见的方式

相对定位比较简单，对应position属性的relative值，如果对一个元素进行相对定位，它将出现在他所在的位置上，然后可以通过设置垂直或水平位置，让这个元素相对于它自己移动，在使用相对定位时，无论元素是否移动，元素在文档流中占据原来空间，只是表现出来的位置会改变

**普通流**

	<div style="border: solid 1px #0e0; width:200px;">
	    <div style="height: 100px; width: 100px; background-color: Red;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Green;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Red;">
	    </div>
	</div>

<div style="border: solid 1px #0e0; width:200px;">
    <div style="height: 100px; width: 100px; background-color: Red;">
    </div>
    <div style="height: 100px; width: 100px; background-color: Green;">
    </div>
    <div style="height: 100px; width: 100px; background-color: Red;">
    </div>
</div>

**相对定位**

	<div style="border: solid 1px #0e0; width:200px;">
	    <div style="height: 100px; width: 100px; background-color: Red;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Green; position:relative; top:20px; left:20px;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Red;">
	    </div>
	</div>

<div style="border: solid 1px #0e0; width:200px;">
    <div style="height: 100px; width: 100px; background-color: Red;">
    </div>
    <div style="height: 100px; width: 100px; background-color: Green; position:relative; top:20px; left:20px;">
    </div>
    <div style="height: 100px; width: 100px; background-color: Red;">
    </div>
</div>

上面例子可以看出，对绿色div进行相对定位，分别右移，下移20px后第二个红色div位置并没有相应变化，而是在原位置，绿色div遮挡住了部分红色div

## 绝对定位与固定定位

相对定位可以看作特殊的普通流定位，元素位置是相对于它在普通流中位置发生变化，而绝对定位使元素的位置与文档流无关，也不占据文档流空间，普通流中的元素布局就像绝对定位元素不存在一样

绝对定位的元素的位置是相对于距离最近的非static祖先元素位置决定的。如果元素没有已定位的祖先元素，那么他的位置就相对于初始包含块儿（body或html神马的）元素。

因为绝对定位与文档流无关，所以绝对定位的元素可以覆盖页面上的其他元素，可以通过`z-index`属性控制叠放顺序，z-index越高，元素位置越靠上。

还是刚才的例子，稍微改动一下，让绿色div绝对定位，为了清晰显示，第二个红色div改为黄色

	<div style="border: solid 1px #0e0; width:200px; position:relative;">
	    <div style="height: 100px; width: 100px; background-color: Red;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Green; position:absolute; top:20px; left:20px;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Yellow;">
	    </div>
	</div>

<div style="border: solid 1px #0e0; width:200px; position:relative;">
    <div style="height: 100px; width: 100px; background-color: Red;">
    </div>
    <div style="height: 100px; width: 100px; background-color: Green; position:absolute; top:20px; left:20px;">
    </div>
    <div style="height: 100px; width: 100px; background-color: Yellow;">
    </div>
</div>

这时可以看出，绿色div是相对于父元素，也就是绿框div进行的移位，而红色和黄色div进行布局时就像绿色div不存在一样

最后要说的就是fixed属性了，应用fixed也叫固定定位，固定定位是绝对定位的一种，固定定位的元素也不包含在普通文档流中，差异是固定元素的包含块儿是视口（viewport），经常见一些页面的如人人网看在线好友那个模块总在窗口右下角，估计用的是类似技术

	<div style="border: solid 1px #0e0; width:200px;">
	    <div style="height: 100px; width: 100px; background-color: Red;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Green; position:fixed; bottom:20px; left:20px;">
	    </div>
	    <div style="height: 100px; width: 100px; background-color: Yellow;">
	    </div>
	</div>

![image](http://lsly1989.qiniudn.com/201210131402313535.png)

![image](http://lsly1989.qiniudn.com/201210131402351710.png)

可见红色和黄色div布局没有受到绿色div影响，而无论是页面纵向滚动条在页面顶端还是底端，绿色div总是在视口左下角
