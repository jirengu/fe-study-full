# Javascript基础

### 认识Javascript
- javascript !== java
- 是客户端脚本语言
- ECMAScript, DOM, BOM 
- ![](http://cdn.jirengu.com/kejian1/13-1.jpg)

### Javascript引入方式
1. 在head或者body中，引入script标签

# 
    <script>
      alert(1);
    </script>

2. 引入js文件，js文件里写js代码

# 
    <script type="text/javascript" src="home.js"></script>

3. 标签的位置，放在body内的最下位置。区别css位置 


### Javascript语法
1. 变量的定义，以var定义。

# 
    var a = 1;
    var b = "hello",
        c = 'world';
    var d = [];

2. 语句以分号结尾.

3. 变量名以$、字母、_开头，其他字符可以是数字，区分大小写。

4. 注释方法

# 
    /* 
      var a = 1;
      var b = 2;
      用单斜线加星号多行注释
    */
    var c = 3; //用双斜线单行注释

5. 赋值语句,用一个=号赋值

### 基本调试
1. 审查元素，打开控制台；
2. console.log();
3. alert();


### 数据类型
typeof 变量； 查看变量类型
  
    var a = 1;
    console.log(typeof a);

#### 数字 number
    var a = 1,b = 0.23,c = 1e10;  //这里多个赋值，中间用逗号，最后用分号
    var d = 1000;
    alert(typeof a); // number

#### 字符串 string
    var str1 = 'hello world';
    var str2 = "我也是字符串";
    var str3 = '"我是带引号的字符串"';
    console.log( typeof str3 );  // string

#### 布尔 boolean
    var flag = true;
    var bad = false;
    if(flag){
      alert('good');
    }else{
      alert('bad');
    }
    alert(typeof flag); //boolean    

#### 对象 object
    var obj = {"name": "小明", "age": 20};
    var empty = {};
    var newObj = {
      name: 'car',
      color: 'red'
    };
    alert(typeof obj); // object

    var empty = null; //null是空对象



#### 数组 （数组也是对象）
    var array = []; //空数组
    var arr2 = [1, 2, 4, 5];
    var arr3 = ['hello', 'world', 100];
    console.log(typeof arr3);
    console.log(arr3.length);
    console.log(arr3[0]);
    console.log(arr3[arr3.length - 1]);

#### 函数 function
    function sum(a,b){
      return a+b;
    }
    sum(2,3);

    var sum2 = function(a, b){
      return a+b;
    }
    sum2(1, 2.3);
    console.log(typeof sum2);

#### 未定义 undefined
    console.log(a);
    var b = undefined;
    console.log(typeof b);

### 语句
#### 1. if语句
如果发生某个条件，就做某件事。

    if(condition) {
        当条件为 true 时执行的代码
    }

如果发生某个条件，就做某件事，否则，做另外的事。

    if(condition) {
        当条件为 true 时执行的代码
    } else {
        当条件不为 true 时执行的代码
    }


    var a = 100;
    if(a > 90){
      console.log('优秀');
    }else if(a > 60){
      console.log('良好');
    }else{
      console.log('不及格');
    }
    

#### 2. do-while
do/while 循环是 while 循环的变体。该循环会在检查条件是否为真之前执行一次代码块，然后如果条件为真的话，就会重复这个循环。

    var i = 0;
    do{
        i += 2;
    }while(i < 10);
    console.log(i);
    

#### 3. while
while 循环会在指定条件为真时循环执行代码块。

    var i = 0;
    while (i < 10) {
        i += 2;
        console.log(i);
    }

    

#### 4. for
初始时i=0，当i小于len时做某件事，把i加1，当i小于len时做某件事...

# 
    var len = 10;
    for (var i = 0; i < len; i++){
        console.log(i);
    }
    

#### 5. for-in
用于循环输出对象里的值

    var man = {
        'name': 'kevin',
        'sex': 'man'
    }
    for(var key in man){
        console.log(man[key]);
    }
    

#### 6. break、continue
用于循环语句中，当break时，跳出循环，循环结束。
当continue时，跳出本次循环，循环继续。

    var i = 0;
    for(i = 0; i < 10; i++){
        if(i == 5){
            break;
        }
        console.log(i);
    }
    
    var j = 0;
    for(j = 0; j < 10; j++){
        if(j == 5){
            continue;
        }
        console.log(j);
    }

##### 7. switch
判断语句，if else的简化版

    switch(a){
        case 1: 
            //todo...
            break;
        case 2:
            //todo...
            break;
        default:
            //todo
    }
    
    var score = 70;
    if(score >= 90){
        console.log('优');
    }else if(score >= 70){
        console.log('良');
    }else if(score >= 60){
        console.log('中');
    }else{
        console.log('差');
    }
    
    switch(true){
        case score >= 90:
            console.log('优');
            break;
        case score >= 70:
            console.log('良');
            break;
        default:
            console.log('差');
    }
    

### 函数 
函数是被调用时执行的可重复使用的代码块

1. 以function定义

```
    function f1(){
        alert(1);
    }

   
    //带参数的函数
    function sayHi (name, msg) {
        alert("Hello " + name + "," + msg);
    }
    //函数的调用
    sayHi("keivn", "this is msg");
    
    //带返回值的函数 return
    //返还值后结束执行
    function sum (num1, num2) {
        console.log(num1 + num2);
        return num1 + num2;
        console.log(num2); //return后不在执行
    }
    sum(10, 20);  
 ```   

2. 函数作用域
在函数内定义的变量只能在函数内访问。

```
    var a = 1; //这里是全局变量
    var b = 2;
    function f1(){
        var a = 2; //这里是局部变量，只再函数体内有效
        var c = 3;
        console.log(a);
        console.log(b); //在函数内可以访问全局变量
    }
    f1();
    console.log(a);
    console.log(c); //出错，全局不能访问函数内局部变量

```
3. 理解参数
    - 数组 ［］
    - arguments为参数数组

```
    function sum(){
        console.log(arguments);
    }
    sum(1);
    sum(1, 2, 3);
    
    /* js中的函数无传统意义的重载 */
    function sum(a, b){
        return a + b;
    }
    function sum(a, b, c){
        return a + b + c;
    }
    sum(1, 2); //出错
    sum(1, 2, 3);
    
    /*用arguemnts实现重载*/
    function newSum(){
        var sum = 0;
        for(var i = 0; i< arguments.length; i++){
            sum += arguments[i];
        }
        return sum;
    }
    
```


### 操作符
- 递增递减

```
    var a = 10;
    var c = ++a;    //a自己加1，再赋值给c
    var d = a++;    // a赋值给d, 再自己加1，
    var b = 'hello';    
    b += 'kevin';  // b = b + 'kevin'; b的值是hello kevin
``` 
- 非与或 ! && ||

!是非，true的非是false，false的非是true。
&&是且， 当两边都为真时才为真。
||是或，当一边为真是才为真。

```
    alert( !flase );
    alert( !0 );
    alert( !'');
    var a = true;
    alert( !a );
    alert( a && 1 == true); 
    alert(a || 1 == 0);
    
    // && 可用来判断是否存在
    $obj && $obj.on('click', fuction(){});
    
    function sum(val){
        reutrn ++val;
    }
    function sum2(val){
        val = val || 1; // || 可用与赋值
        reutrn ++val;
    }
    sum();
    sum2();
```
- 乘*, 除法/, 求余%
    1. 对与乘除减, 非number相乘会转换乘成number；如果转换失败返还NaN

``` 
    var a = 10,
        b = "2",
        c = true,
        d = "hello";
    alert(a - b);
    alert(a / b);
    alert(a * c);
    alert(b % a);
    alert( a - c);
 ```   

- 加+
    1. 对于加，任何与字符串相加会转换成字符串，再加

``` 
    var a = 10,
        b = "2",
        c = true,
        d = false,
        e = null,
        f = 'hello';
    console.log( a + a );
    console.log( a + b );
    console.log( a + c );
    console.log( d + c );
    console.log( e + f );
    console.log( a + f );
    console.log( f + (a + a) );
```
- 关系> <
    1. 如果都是number， 直接比较
    2. 如果都是string, 直接比较
    3. 如果一个是number，把另一个转换为number，比较

``` 
    2 > 1; //true
    "b" > "abc" //true
    "23" < 3 //false
    NaN < 3 // false
    NaN >= 3 // false
    "a" > 3 //fasle
    "a" <= 3 //false

- 等号== 和!=, 全等=== 和!==, 区别于赋值=

# 
    11 == "11" //true
    11 === "11" //false
    true == 1  //true
    true == 2 //false
    false == 0 //true
    NaN == NaN // false
    NaN != NaN //true
    undefined == 0 //false
    null == 0 //false;

    if(null){alert(2)}  //false
    if(0){alert(2)}
    if(undefined){alert(2)}
    if(false){alert(2)}
    if(''){alert(2)}

    if({}){alert(2)} //true
    if([]){alert(2)}
```
- 条件操作符

``` 
    var num1 = 2,
        num2 = 1;
    var max = (num1 > num2 ) ? num1: num2;
```
- 赋值操作符

```
    var num = 10;
    num = num + 10;
    num += 10;
    num = num - 2;
    num -= 2;
    num %= 3;
 ```   
     



