# ajax, jsonp, jquery ajax

AJAX = Asynchronous JavaScript and XML 异步的 JavaScript 和 XML
通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。



### 看代码
    var xmlhttp=new XMLHttpRequest();
    xmlhttp.onreadystatechange=function(){
        if (xmlhttp.readyState==4 && xmlhttp.status==200){
            document.getElementById("myDiv1").innerHTML=xmlhttp.responseText;
        }
    }
    xmlhttp.open("GET","ajax_simple.php",true);
    xmlhttp.send();

[演示地址](http://kejian.jirengu.com/data/fe/%E8%AF%BE%E4%BB%B6/24-ajax/code/index.html)

1. 创对象
2. 绑事件
3. 给参数
4. 发送
 
 #### readystatechange 事件
当请求被发送到服务器时，我们需要执行一些基于响应的任务。
每当 readyState 改变时，就会触发 readystatechange 事件。
readyState 属性存有 XMLHttpRequest 的状态信息。
下面是 XMLHttpRequest 对象的三个重要的属性：

`onreadystatechange` : 存储函数（或函数名），每当 readyState 属性改变时，就会调用该函数。|

`readyState` :  XMLHttpRequest 的状态。从 0 到 4 发生变化。

- 0: 请求未初始化
- 1: 服务器连接已建立
- 2: 请求已接收
- 3: 请求处理中
- 4: 请求已完成，且响应已就绪

`status` : 

- 200: "OK"
- 404: 未找到页面


在 onreadystatechange 事件中，我们规定当服务器响应已做好被处理的准备时所执行的任务。
当 readyState 等于 4 且状态为 200 时，表示响应已就绪：
```    
    xmlhttp.onreadystatechange=function(){
        console.log(xmlhttp.readyState);
        console.log(xmlhttp.status);
        if (xmlhttp.readyState==4 && xmlhttp.status==200){
            document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
        }
    }
```
 
#### open方法
open(method,url,async)  

- 规定请求的类型、URL 以及是否异步处理请求。
- method：请求的类型；GET 或 POST
- url：文件在服务器上的位置
- async：true（异步）或 false（同步）

#### send方法
send(string)    

- 将请求发送到服务器。
- string：仅用于 POST 请求

#### 同步vs异步
    xmlhttp.open("GET", "ajax_test.php", true);

第三个参数是true是异步，false是同步。

当是`异步`时，浏览器把请求发送后就继续做自己的事，当onreadystatechange事件到来时说明服务端的数据来了，这时再处理数据。类似于一个节点绑定点击事件后就做后面的事，当用户点击了再执行绑定的处理函数。

当是`同步`时，JavaScript 会等到服务器响应就绪才继续执行。如果服务器繁忙或缓慢，应用程序会挂起或停止。
当使用 async=false 时，不用编写 onreadystatechange 函数，把代码放到 send() 语句后面即可：

    xmlhttp.open("GET","ajax_test.php",false);
    xmlhttp.send(); //这里发送后代码就卡在这里等待服务器响应
    document.getElementById("myDiv").innerHTML=xmlhttp.responseText; 

不推荐使用 async=false，但是对于一些小的简单的请求，也是偶尔可以用一下。

#### POST 请求
一个简单 POST 请求：

    xmlhttp.open("POST","ajax_post.php",true);  // type为 POST
    xmlhttp.send("name=kevin&age=100");    //send 要发送数据



### jquery ajax函数
ajax() 方法通过 HTTP 请求加载远程数据。

    $.ajax(opts);

opts为ajax所需的参数，为json格式

常用参数有：

`url`: 后端接口地址

`type`: 数据传输方式，GET或者POST

`dataType`: 预期服务器返回的数据类型。常用为json、jsonp

`data`: 发给服后端的数据

`cache`: 是否开启缓存，默认为true开启

`success`: 成功后的回调函数，返还的数据做为参数

`error`: 接口失败的回调函数

`complete`: 请求完成的回调函数

如：
 
        var opts = {
            url: 'getMoreItem.php',
            type: 'GET',
            dataType: 'json',
            data: {
                name: 'xiaoming'
            },
            success: function(data){
                console.log(data.items);
            },
            error: function(){
                alert('error');
            }
        };
        $.ajax(opts);

### 跨域和jsonp

本域指的是？

- 同协议：如都是http或者https
- 同域名：如都是http://1688.com/a 和http://1688.com/b
- 同端口：如都是80端口


jsonp可实现跨域，原理是

1. 定义数据处理函数_fun
2. 创建script标签，src的地址执行后端接口，最后加个参数callback=_fun
3. 服务端在收到请求后，解析参数，计算返还数据，输出 fun(data) 字符串。
4. fun(data)会放到script标签做为js执行。此时会调用fun函数，将data做为参数。

    echo $cb . '&&' . $cb . '(' . json_encode($ret) . ')';



