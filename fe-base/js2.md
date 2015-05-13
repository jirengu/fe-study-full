# 符串操作，数组操作、日期、数学函数、定时循环

### 数组
#### 1.数组定义， 访问
    var arr1 = new Array(),
        arr2 = ['dog', 'cat'],
        arr3 = ['dog', 1, {a:1, b:2}],  //数组元素是任意值
        arr4 = [1, 2, , 3],  //1,2,undefined, 3
        arr5 = [1, 2, 3,],  // ie8及以下是1,2,3,undefined 长度为4， chrome 为1，2，3 长度为3  不推荐
        len = arr2.length;
        
    var a = arr2[0];  // 访问第1个元素
    var b = arr2[2];  //undefined
    arr3[1] = 2;   //设置元素
    arr4[arr4.length] = 4;
    arr4[arr4.length] = 5;
    arr2[99] = 1;  // arr2.length = 100

#### 2.数组的检测，转换
    var arr = [1, 3, 4];
    arr instanceof Array
    $.isArray(arr) // jquery
    console.log(arr.join('-')); //数组链接成字符串

#### 3.数组遍历 添减
    var arr = ['a', 'b', 'c'];
    for(var i = 0; i< arr.length; i++){
      console.log(arr[i]);
    }
    $.each(arr, function(idx, value){
        cosnole.log(i+":"+value);
    });
  
    arr.push('d', 'e');
    arr.pop();  //推出最后一项
    arr.shift(); //推出第一项
    arr.unshift('f'); //推入第一项

#### 4.排序
    var arr = [2, 1, 4, 0, 5];
    arr.reverse();
    arr.sort();

#### 5.删减
    var a1 = [1,2,3];
    var a2 = [4,5,6];
    var a3 = a1.concat(a2);
    a3.slice(2,4); // 3,4

### 字符串
#### 1. 长度计算,连接
    var str = "hello";
    console.log( str.length );
    console.log( str[0] );
    console.log( str[str.length - 1]  );
    console.log( str.charAt(0) );
    console.log( str.charCodeAt(0) );
    
    var str2 = " world";
    var str3 = str1 + str2;
    cosnole.log( str3 );
    
#### 2. 字符串截取 
    var str = "hello world";
    var sub1 = str.subStr(1, 3); // 第一个是开始位置， 第二个是长度  ell
    var sub2 = str.subString(1, 3); // 第一个是开始位置，第二个是结束位置，长度为第二个－第一个  el
    var sub3 = str.slice(1, 3); // 同上 允许负参

#### 3. 查找
    var str = "hello my world";
    var s1 = str.search('my');   //6 找不到为-1
    var s2 = str.replace('my', 'your'); //
    var s3 = str.match('my'); //返回匹配的数组

#### 4. 大小写
    var str = "Hello";
    str.toUpperCase();
    str.toLowerCase();

### JSON对象操作
josn是轻量级的数据交换格式

#### 1. JSON格式, 读取, 设置
    var obj = {"name":"keivn", "age": 100}; 
    var obj2 = {name: 'car', color: 'red'};
    var obj3 = {1: 'a', 100: 'b'};
    
    console.log( obj.name );
    console.log( obj['age'] );
    var key = "age";
    cosnole.log( obj[key]);
    console.log( obj3.1 ); //error
    console.log( obj3[1] ) //ok
    console.log( obj3["1"] ) //ok
    
    obj.name = "Peter";
    obj.sex = "man";
    obj['height'] = "1.82";
    
    console.log('json.....');
    var people = {
        name: 'kevin',
        age: 100,
        dog: {
            name: 'yellow',
            age: 3
        }
    };
    console.log(people.name);
    console.log(people.dog);
    console.log(people.dog.name);
    console.log(people['name']);
    console.log(people['dog']['age']);

    var obj = {
        1: 'hello',
        2: 'world'
    }
    console.log('obj...');
    console.log(obj['1']);
    //console.log(obj.1); //error
    
    var ke = 'name';
    console.log('---另一种形式--');
    console.log( people[ke] );

    console.log('for-----');
    for(var k in people){
        console.log( k + ':' + people[key]  );
    }


#### 2. JSON解析
    var obj = {"name":"keivn", "age": 100}; 
    var objStr = JSON.stringify(obj);  // ie8+
    var str = '{"a":1, "b":2}';
    var o = JSON.parse(str);
    console.log(o)

### 日期的使用
    //创建日期对象，当前日期
    var d = new Date();   
    console.log(d);
    //设置日期，创建日期对象
    var d1 = new Date('5/12/2014');
    //设置日期，时分秒
    var d2 = new Date(2014, 5, 18, 22, 23, 40);
    var date = d1.getDate(), //从日期对象中获取一月中得天数， 1~31, 
        month = d1.getMonth(), //获取月份，注意从0开始，一月份的值是0， 0~11,
        year = d1.getFullYear(), //获取年份，2014,
        hour = d1.getHours(), //获取小时， 0~23,
        min = d1.getMinutes(), //获取分，0~59,
        sec = d1.getSeconds(), //获取秒，0~59,
        milSec = d1.getMillseconds(), //获取毫秒，0~999
        day = d1.getDay(); //获取星期几，周日是0，周一是1， 0~6
    
    
    //单独设置年份
    var d3 = new Date();
        d3.setFullYear(2014);
        
    
    //1970.1.1 到当前日期的毫秒数
    var oldDate = new Date(2014, 11, 21),
        time = oldDate.getTime(); 
    var time2 = new Date().getTime();
    var during = time2 - time;
    console.log(during);

    var start = Date.now();  // ie9+ 
    for(var i = 0; i< 10000; i++){
      console.log(i);
    }
    var end = Date.now();
    alert(end - start);
    
    var start2 = +new Date();
    var end2 = +new Date();
    console.log(end2 - start2);
    
 
### 数学函数
#### 数学常用函数的使用
    var n = Math.random();
    Math.ceil(2.34);
    Math.floor(3.33);
    Math.max(100, 90);
    Math.min(100, 90);
    Math.round(2.35)//
    
### setTimeout
`作用`：延时指定的毫秒数再执行指定代码。
	
setTimeout是全局作用域下函数，因此可加window，也可不加
# 
	window.setTimeout("javascript 函数",毫秒数);
	
推荐下面这种写法
# 
	setTimeout(function(){
		//延时1000毫秒后执行的代码
		console.log('延时1s执行');
	}, 1000);

如果要取消timeout，需要保存setTimeout的返回值，用clearTimeout取消掉这个返还值。

`clearTimeout()`方法用于停止执行setTimeout()。
# 
	var clock;
	clock = setTimeout(function(){
		console.log('延时3s开始执行')
	}, 3000);
	clearTimeout(clock);


### setInterval
`作用`：间隔指定的毫秒数不停地执行指定的代码

setInterval是全局作用域下函数，因此可加window，也可不加
# 
	setInterval("javascript 函数",毫秒数);
	
推荐下面这种写法
# 
	setInterval(function(){
		//每隔1000毫秒执行一次
		console.log('每隔1s秒执行一次');
	}, 1000);

如果要取消interval，需要保存setInterval的返回值，用clearInterval取消掉这个返还值。

`clearInterval()`方法用于停止执行setInterval()。
# 
	var clock;
	clock = setInterval(function(){
		console.log('每隔3s执行一次')
	}, 3000);
	clearInterval(clock);

    function countDown (dateStr) {
        var end = +new Date(dateStr),
            start = +new Date(),
            during = Math.floor((end - start)/1000);

        var day = Math.floor( during/(24*60*60) ),
            t1 = during - (day*24*60*60),
            hour = Math.floor( t1/(60*60) ),
            t2 = t1 - hour*60*60,
            min = Math.floor( t2/60 ),
            sec = t2%60;

        return day + '天' + hour + '小时' + min + '分' + sec + '秒';
    }
    
    var clk = setInterval(function(){
        var str = countDown('2015-1-1');
        console.log('距元旦还有：' + str);
    }, 1000);
	

### setTimeout注意点（扩展）
[js计时器原理](http://www.daqianduan.com/1112.html)

[js定时机制参考](http://www.phpv.net/html/1700.html)



     
     


