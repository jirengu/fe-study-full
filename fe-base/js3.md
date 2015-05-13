# dom、jquery选择器、jquery dom操作、jquery dom遍历、jquery事件、

## 认识DOM
当网页被加载时，浏览器会创建页面的文档对象模型（Document Object Model）。

#### 1.1 DOM节点树
![](http://cdn.jirengu.com/kejian1/141212-1.png)
 
#### 1.2节点关系
![](http://cdn.jirengu.com/kejian1/141212-2.png)

# 
	<html>
	  <head>
	    <title>DOM 教程</title>
	  </head>
	  <body>
	    <h1>DOM 第一课</h1>
	    <p>Hello world!</p>
	  </body>
	 </html>

从上面的 HTML 中：

```<html>``` 节点没有父节点；它是根节点

```<head>``` 和 ```<body>``` 的父节点是``` <html>``` 节点

文本节点 "Hello world!" 的父节点是 ```<p>``` 节点

并且：

```<html>``` 节点拥有两个子节点：```<head>``` 和 ```<body>```
```<head>``` 节点拥有一个子节点：```<title>``` 节点
```<title>``` 节点也拥有一个子节点：文本节点 "DOM 教程"
```<h1>``` 和 ```<p>``` 节点是同胞节点，同时也是``` <body>``` 的子节点

## jquery的使用

这是为了防止文档在完全加载（就绪）之前运行 jQuery 代码,如果在文档没有完全加载之前就运行函数，操作可能失败。必须在文档加载完成后在执行操作，可使用ready事件，作用相当于我们把js写到body的末尾。

    $(document).ready(function(){
        //your code here
    });
	
## jq选择器
和css的选择器类似

$(this) 当前 HTML 元素

$("p")  所有 <p> 元素

$("p.intro")    所有 class="intro" 的 <p> 元素

$(".intro") 所有 class="intro" 的元素

$("#intro") id="intro" 的元素

$(".a .b .c")    class a的子元素class b的子元素class c.

$("[data-flag=true]") 所有带有data-flag属性 并且值是true的元素

$("div#intro .head")  id="intro" 的 <div> 元素中的所有 class="head" 的元素

$("div#intro").find(".head");

    #div1, #div2 .intro{

    }
$('#div1, #div2 .intro')

### 事件
常见事件有：click、dblclick、mousedown、mouseenter、resize等
参考[w3c事件](http://www.w3school.com.cn/jquery/jquery_ref_events.asp)

#### 事件绑定写法

    $("button").click(function() {
        alert(1);
    } );

    $("button").on('click', function(){
        console.log(e);
        console.log(this);
        console.log($(this));
    });
	
	 //使用代理的方式
	 $( "#doc" ).on( "click", "button", function( e ) {
	 });  

### DOM元素 vs Jquery元素
dom元素： 通过原生js获取的dom节点是dom元素；

jquery元素： 通过jquery选择器选择的元素是jquery元素

    <div id="mydiv">test</div>
    <button id="btn">隐藏</button>
    <script>
        var div1 = document.getElementById("mydiv");
        var div2 = $("#mydiv");
        console.log(div1); //dom元素
        console.log(div2); //jquery元素
        $('#btn').on('click', function(){
            div2.hide();
        });
        document.getElementById("btn").onclick=function(){
            div1.show();
        }
    </script>

1. dom->jquery，加$(dom)
2. jquery->dom, jquery元素是以数组形式展现，选取数组的第几项就能转换为dom元素