# dom、jquery事件、jquery选择器、jquery dom操作、jquery dom遍历

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
```
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
```
- dom->jquery，加$(dom)
- jquery->dom, jquery元素是以数组形式展现，选取数组的第几项就能转换为dom元素

### Jquery特效方法
##### 1. 隐藏展示

    $(selector).hide(speed,callback);
    $(selector).show(speed,callback);
    $(selector).toggle(speed,callback);

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

本质上是修改dom.style.display属性

    //展示p1
    $("#btn1").on('click', function(e){
        $(".p1").show();
    });
    //隐藏p1
    $("#btn2").on('click', function(){
        $(".p1").hide();
    });
    //隐藏p1，持续时间1s，之后再执行回调
    $("#btn3").on('click', function(){
        $(".p1").hide(1000, function(){
            $(".p2").hide(2000, function(){
                $(".p3").hide(3000);
            });
        });
    });
    $("#btn4").on('click', function(){
        $(".p1").show(1000, function(){
            $(".p2").show(2000, function(){
                $(".p3").show(3000);
            });
        });
    });
    //状态切换
    $("#btn5").on('click', function(){
        $(".p1").toggle();
    });



##### 2. 淡入淡出
    $(selector).fadeIn(speed,callback);  //淡入
    $(selector).fadeOut(speed,callback);  //淡出
    $(selector).fadeToggle(speed,callback); //淡入淡出切换
    $(selector).fadeTo(speed,opacity,callback);  //渐变到透明度


    var $div1 = $(".div1");
    $("#btn6").on('click', function(e){
        $div1.fadeIn();
    });
    $("#btn7").on('click', function(e){
        $div1.fadeIn(4000, function(){
            alert('over');
        });
    });
    $("#btn8").on('click', function(){
        $div1.fadeOut();
    });
    $("#btn9").on('click', function(){
        $div1.fadeToggle();
    });
    $("#btn10").on('click', function(){
        $div1.fadeTo('slow', 0.5);
    });

#### 3.滑入滑出

    $(selector).slideDown(speed,callback);  //滑入
    $(selector).slideUp(speed,callback);  //滑出
    $(selector).slideToggle(speed,callback); //切换

    var $div2 = $(".div2");
    $("#btn11").on('click', function(e){
        $div2.slideUp();
    });
    $("#btn12").on('click', function(e){
        $div2.slideDown();
    });
    $("#btn13").on('click', function(){
        $div2.slideToggle(10000);
    });

#### 4.动画
jQuery animate() 方法用于创建自定义动画。

    $(selector).animate({params},speed,callback);

- 必需的 params 参数定义形成动画的 CSS 属性。
- 可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
- 可选的 callback 参数是动画完成后所执行的函数名称。

### 
    var $div3 = $(".div3");
    $("#btn14").on('click', function(e){
        $div3.animate({width: '200px'});
    });
    $("#btn15").on('click', function(){
        $div3.animate({
            width:'80px',
            height: '80px',
            left: '0px',
            top: '0px'
        }, 500);
    });
    $("#btn16").on('click', function(){
        $div3.animate({
            width:'150px',
            height: '150px',
            left: '100px',
            top: '100px'
        }, 500);
    });
    $("#btn17").on('click', function(){
        $div3.animate({width:'150',height:'150px'})
             .animate({left:'200px'})
             .animate({top:'200px'});
             
        $div3.animate({left:'0px'});
        $div3.animate({top:'0px'});
        $div3.animate({width:'80px',height:'80px'});
    });

### Jquery Dom操作
#### 获取与设置值
三个简单实用的用于 DOM 操作的 jQuery 方法：

- text()  设置或返回所选元素的文本内容
- html()  设置或返回所选元素的内容（包括 HTML 标记）
- val()   设置或返回表单字段的值
- attr()  设置或返回元素的属性

获取
## 
    <p id="test">这是段落中的<b>粗体</b>文本。</p>
    <input id="test-input" type="text" placeholder="测试表单val">
    <a id="test-a" href="http://www.jirengu.com">这是链接</a>
    <img id="test-img" data-src="real.png" src="blank.png">
    <script>
        console.log( $('#test').html() );  // 这是段落中的<b>粗体</b>文本。
        console.log( $('#test').text() );  // 这是段落中的粗体文本
        console.log( $('#test-input').val() );
        console.log( $('#test-a').attr('href') );
        console.log( $('#test-img').attr('data-src') );
    </script>

设置

        $('#test').html('<span>hello</span>');  
        $('#test').text('<span>hello2</span>');
        $('#test-input').val('小明');
        $('#test-a').attr('href','http://www.baidu.com');
        $('#test-img').attr('src',  $('#test-img').attr('data-src'));


### Jquery添加、删除元素
##### 1. 添加元素

- append() - 在被选元素的结尾插入内容
- prepend() - 在被选元素的开头插入内容
- after() - 在被选元素之后插入内容
- before() - 在被选元素之前插入内容


`append`是在父元素内部的最后位置添加元素

    $("ul.set1").append('<li>看电影</li>');  //两种方式都可以
    var $li = $('<li>旅游</li>');
    $(".set1").append($li);  

`prepend`是在父元素的内容的开始位置添加元素
    
    $set1.prepend('<li>遛狗</li>'); 

`after`在匹配元素之后插入内容

    var $firstLi = $set1.find('li:first'),
        $lastLi = $set1.find('li:last');
    //在元素后面插入新内容
    //$firstLi.before('<li>写代码</li>');
    //改变已有元素的位置
    $firstLi.before($lastLi);

`before`在匹配元素之前插入内容

    var $firstLi = $set1.find('li:first'),
        $lastLi = $set1.find('li:last');
    //$lastLi.after('<li>上课</li>');
    $lastLi.after($firstLi);

##### 2. 删除元素
- remove() - 删除被选元素（及其子元素）
- empty() - 从被选元素中删除子元素

##### 
    <ul class="set2" style="border: 1px solid red; height: 40px;">
        <li>吃饭</li>
        <li>睡觉</li>
    </ul>
    <button id="btn2-1">remove</button>
    <button id="btn2-2">empty</button>
    <script type="text/javascript">
        var $set2 = $('.set2');
        $('#btn2-1').on('click', function(){
            $set2.remove();
        });

        $('#btn2-2').on('click', function(){
            $set2.empty();
        });

    </script>

##### 3. 添加与删除class
- hasClass('class') - 判断元素是否拥有某个class
- removeClass('class') - 删除元素的某个class
- addClass('class') - 给元素添加某个class
- toggleClass('class') - 切换添加移除class

###### 
        var $curTab = $(this),
            idx = $curTab.prevAll().size();
        $curTab.addClass('active').siblings().removeClass('active');
        $tabC.removeClass('active').eq(idx).addClass('active');

### Jquery CSS
css() 方法设置或返回被选元素的一个或多个样式属性。

如需返回指定的 CSS 属性的值，请使用如下语法：
    
    $("p").css("background-color");

如需设置指定的 CSS 属性，请使用如下语法：

    $("p").css("background-color","yellow");

如需设置多个 CSS 属性，请使用如下语法：

    $("p").css({
        "background-color":"yellow",
        "font-size":"200%"
    });

### Jquery尺寸
- width() 方法设置或返回元素的宽度（不包括内边距、边框或外边距）。
- height() 方法设置或返回元素的高度（不包括内边距、边框或外边距）。
- innerWidth() 方法返回元素的宽度（包括内边距）。
- innerHeight() 方法返回元素的高度（包括内边距）。
- outerWidth() 方法返回元素的宽度（包括内边距和边框）。
- outerHeight() 方法返回元素的高度（包括内边距和边框）
- outerWidth(true) 方法返回元素的宽度（包括内边距、边框和外边距）。
- outerHeight(true) 方法返回元素的高度（包括内边距、边框和外边距）。

### Jquery遍历

    <div class="c">
        <div class="d1">睡觉</div>
        <div class="d1">工作</div>
        <div class="d1 d2">
            <div class="e1">aaa</div>
            <div class="e1">bbb</div>
            <div class="e2">ccc</div>
        </div>
        <div class="d3">d3</div>
    </div>


##### .children()
获取元素的子元素
    
    // children
    console.log( $('.c').children() );

##### .each()
遍历选择器元素
    
    // each
    $('.e1').each(function(){
        console.log($(this).text());
    });
    $('.e1').each(function(idx, el){
        console.log(idx + ":");
        console.log( $(el).text() );
    });
#### .find()
查找子元素

    //find
    var $c = $('.c'),
        $es = $c.find('.e1');
    $es.on('click', function(){
        console.log($(this).text());
    });
#### .parent() .parents
parent()查找父亲， parents(selector)从祖先里查找

    //parent parents
    var $e2 = $('.e2');
    console.log($e2.parent());
    console.log($e2.parents('.c'));

#### prevAll()
获取自己前面的邻居

    //prevAll
    console.log($e2.prevAll());

#### siblings()
获取自己的邻居

    //sibilings
    console.log($('.d3').siblings());