JavaScript Note
===============


Array.prototype.slice.call(arguments);
Object.assign({}, a, b, ...)
function.call(obj, param1, param2...);
function.bind(obj)(param1, param2...);
function.apply(obj) == function.bind(obj)()
Object.defineProperty(obj, 'name', {
        configurable: true,
        enumerable: true,
        get: function() { return _name; },
        set: function(n) { _name = n; }
    })
`obj.__proto__` parent prototype

// Create object with an existing object as prototype
Object.create()

// Adding or changing an object property
Object.defineProperty(object, property, descriptor)

// Adding or changing object properties
Object.defineProperties(object, descriptors)

// Accessing Properties
Object.getOwnPropertyDescriptor(object, property)

// Returns all properties as an array
Object.getOwnPropertyNames(object)

// Accessing the prototype
Object.getPrototypeOf(object)

// Returns enumerable properties as an array
Object.keys(object)
bject.preventExtensions(object)

// Returns true if properties can be added to an object
Object.isExtensible(object)

// Prevents changes of object properties (not values)
Object.seal(object)

// Returns true if object is sealed
Object.isSealed(object)

// Prevents any changes to an object
Object.freeze(object)

// Returns true if object is frozen
Object.isFrozen(object)


instanceof
typeof

JSON.parse
JSON.stringify




AJAX
// XMLHttpRequest 的实例化
var xhttp;
if (window.XMLHttpRequest) {
    xhttp = new XMLHttpRequest();
} else {
    // code for IE6, IE5
    xhttp = new ActiveXObject("Microsoft.XMLHTTP");
}

// Get请求，第三个参数为是否异步
xhttp.open("GET", "demo_get2.asp?fname=Henry&lname=Ford", true);
xhttp.send();

// Post 请求
xhttp.open("POST", "ajax_test.asp", true);
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("fname=Henry&lname=Ford");

// responseText
document.getElementById("demo").innerHTML = xhttp.responseText;

// responseXML
xmlDoc = xhttp.responseXML;
txt = "";
x = xmlDoc.getElementsByTagName("ARTIST");
for (i = 0; i < x.length; i++) {
  txt += x[i].childNodes[0].nodeValue + "<br>";
  }
document.getElementById("demo").innerHTML = txt;


// Event:
// xhttp.onreadystatechange()
// xhttp.readState, xhttp.status

Property
Description
onreadystatechange
Stores a function (or the name of a function) to be called automatically each time the readyState property changes
readyState
Holds the status of the XMLHttpRequest. Changes from 0 to 4:  0: request not initialized  1: server connection established 2: request received  3: processing request  4: request finished and response is ready
status
200: "OK" 404: Page not found

```html
// Example:
<!DOCTYPE html>
<html>
<body>
<button type="button" onclick="loadDoc()">Change Content</button>
<table id="demo"></table>

<script>
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (xhttp.readyState == 4 && xhttp.status == 200) {
    myFunction(xhttp);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}
function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) {
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
</script>

</body>
</html>
```

-----------------
# Worker

JS线程
var worker = new Worker('xxxxx.js');
worker.onmessage = function(e){
    // e.data = "Message to main thread";
}
worker.postMessage("Message text");// send message to worker
//--------------------------------------------
// xxxxx.js
function onmessage(e) {
    // e.data = "Message text";
}
postMessage('Message to main thread');

WebAssembly
WebGL

WebSocket
```
if ('WebSocket' in window) {
    ws = new WebSocket("ws://localhost/examples");
} else if ('MozWebSocket' in window) {
    ws = new MozWebSocket("ws://localhost/examples");
} else {
    return;
}

ws.onopen = function () {};
ws.onmessage = function (event) {
    //    log('Received: ' + event.data);
};
ws.onclose = function (event) {
    //     event.code, event.reason
};

ws.send("Message");
ws.close();
```




# 正则表达式
##元字符
( [ { \ ^ $ | ) ? * + .

预定义的特殊字符
字符 正则 描述
\t     /\t/     制表符
\n     /\n/     制表符
\r     /\r/     回车符
\f     /\f/     换页符
\a     /\a/     alert字符
\e     /\e/     escape字符
\cX     /\cX/     与X相对应的控制字符
\b     /\b/     与回退字符
\v     /\v/     垂直制表符
\0     /\0/     空字符

字符类
简单类
原则上正则的一个字符对应一个字符，我们可以用[]把它们括起来，让[]这个整体对应一个字符。如
/ruby/.test("ruby")//true
/[abc]/.test("a")//true
/[abc]/.test("b")//true
/[abc]/.test("c")//true
"a bat ,a Cat,a fAt bat ,a faT cat".match(/[bcf]at/gi)//bat,Cat,fAt,bat,faT,cat

负向类
也是在那个括号里做文章，前面加个元字符进行取反，表示匹配不能为括号里面的字符。
/[^abc]/.test("a")//false
/[^abc]/.test("b")//false
/[^abc]/.test("6")//true
/[^abc]/.test("gg")//true

范围类
还是在那个中括号里面做文章。有时匹配的东西过多，而且类型又相同，全部输入太麻烦，我们可以用它。特征就是在中间加了个横线。

组合类
还是在那个中括号里面做文章。允许用中括号匹配不同类型的单个字符。
/[a-f]/.test("b")//true
/[a-f]/.test("k")//false
/[a-z]/.test("h")//true
/[A-Z]/.test("gg")//false
/[^H-Y]/.test("G")//true
/[0-9]/.test("8")//true
/[^7-9]/.test("6")//true
/[a-m1-5\n]/.test("a")//true
/[a-m1-5\n]/.test("3")//true
var a = "\n";
/[a-m1-5\n]/.test(a)//true
/[a-m1-5\n]/.test("r")//false

预定义类
还是在那个中括号里面做文章，不过它好像已经走到尽头了。由于是中括号的马甲，因此它们还是对应一个字符。
字符  等同于 描述
.         [^\n\r] 除了换行和回车之外的任意字符
\d     [0-9] 数字字符
\D     [^0-9] 非数字字符
\s       [\t\n\x0B\f\r] 空白字符
\S      [^\t\n\x0B\f\r] 非空白字符
\w     [a-zA-Z_0-9] 单词字符(所有的字母)
\W     [^a-zA-Z_0-9] 非单词字符
/\d/.test("3")//true
/\d/.test("w")//false
/\D/.test("w")//true
/\w/.test("w")//true
/\w/.test("司")//false
/\W/.test("徒")//true
/\s/.test(" ")//true
/\S/.test(" ")//false
/\S/.test("正")//true
/./.test("美")//true
/./.test(" ")//true
var a = "\n\"
/./.test(a)//true

量词
由于元字符与特殊字符或字符类或者它们的组合（中括号）甚至它们的马甲（预定义类）都是一对一进行匹配。我们要匹配“司徒正美这个词”，最简单都要/..../，如果长到50多个字符岂不是要死人。因此我们逼切需要一个简单的操作，来处理这数量关系。

简单量词
代码 类型 描述
? 软性量词 出现零次或一次
* 软性量词 出现零次或多次(任意次)
+ 软性量词 出现一次或多次（至道一次）
{n} 硬性量词 对应零次或者n次
{n,m} 软性量词 至少出现n次但不超过m次
{n,} 软性量词 至少出现n次(+的升级版)
/..../.test("司徒正美")//true
/司徒正美/.test("司徒正美")//true
/[\u4e00-\u9fa5]{4}/.test("司徒正美")//true
/[\u4e00-\u9fa5]{4}/.test("司徒正美55")//true
/^[\u4e00-\u9fa5]+$/.test("正则表达式")//true
/^[\u4e00-\u9fa5]+$/.test("正则表达式&*@@")//false
/\d{6}/.test("123456")//true
/[ruby]{2}/.test("rr")//true
/[ruby]{2}/.test("ru")//true
/[ruby]{2}/.test("ry")//true
/[\u4e00-\u9fa5]/用于匹配单个汉字。

贪婪量词，惰性量词与支配性量词
贪婪量词，上面提到的所有简单量词。就像成语中说的巴蛇吞象那样，一口吞下整个字符串，发现吞不下（匹配不了），再从后面一点点吐出来（去掉最后一个字符，再看这时这个整个字符串是否匹配，不断这样重复直到长度为零）

隋性量词，在简单量词后加问号。由于太懒了，先吃了前面第一个字符，如果不饱再捏起多添加一个（发现不匹配，就读下第二个，与最初的组成一个有两个字符串的字符串再尝试匹配，如果再不匹配，再吃一个组成拥有三个字符的字符串……）。其工作方式与贪婪量词相反。

支配性量词，在简单量词后加加号。上面两种都有个不断尝试的过程，而支配性量词却只尝试一次，不合口味就算了。就像一个出身高贵居支配地位的公主。但你也可以说它是最懒量词。由于javascript不支持，所以它连出场的机会也没有了。

var re1 = /.*bbb/g;//贪婪
var re2 = /.*?bbb/g;//惰性
// var re3 = /.*+bbb/g;//支配性,javascript不支持，IE与所有最新的标准浏览器都报错
re1.test("abbbaabbbaaabbbb1234")+""//true
re1.exec("abbbaabbbaaabbbb1234")+""//null
"abbbaabbbaaabbbb1234".match(re1)+""//abbbaabbbaaabbbb
re2.test("abbbaabbbaaabbbb1234")+""//true
re2.exec("abbbaabbbaaabbbb1234")+""//aabbb
"abbbaabbbaaabbbb1234".match(re2)+""//abbb,aabbb,aaabbb

分组
到目前为止，我们只能一个字符到匹配，虽然量词的出现，能帮助我们处理一排密紧密相连的同类型字符。但这是不够的，下面该轮到小括号出场了，中括号表示范围内选择，大括号表示重复次数。小括号允许我们重复多个字符。

//分组+量词
/(dog){2}/.test("dogdog")//true
//分组+范围
"baddad".match(/([bd]ad?)*/)//baddad,dad
//分组+分组
"mon and dad".match(/(mon( and dad)?)/)//mon and dad,mon and dad, and dad

反向引用
反向引用标识由正则表达式中的匹配组捕获的子字符串。每个反向引用都由一个编号或名称来标识，并通过“\编号”表示法进行引用。

var color = "#990000";
/#(\d+)/.test(color);
RegExp.$1//990000

/(dog)\1/.test("dogdog")//true

var num = "1234 5678";
var newNum = num.replace(/(\d{4}) (\d{4})/,"$2 $1");

候选
继续在分组上做文章。在分组中插入管道符（“|”），把它划分为两个或多个候多项。

var reg = /(red|black|yellow)!!/;
reg.test("red!!")//true
reg.test("black!!")//true
reg.test("yellow!!")//true

非捕获性分组
并不是所有分组都能创建反向引用，有一种特别的分组称之为非捕获性分组，它是不会创建反向引用。反之，就是捕获性分组。要创建一个非捕获性分组，只要在分组的左括号的后面紧跟一个问号与冒号就行了。

var color = "#990000";
/#(?:\d+)/.test(color);
RegExp.$1//""
题目，移除所有标签，只留下innerText!

var html = "<p><a href='http://www.cnblogs.com/rubylouvre/'>Ruby Louvre</a>by <em>司徒正美</em></p>";
var text = html.replace(/<(?:.|\s)*?>/g, "");
注意：javascript不存在命名分组

前瞻
继续在分组内做文章。前瞻与后瞻其实都属于零宽断言，但javascript不支持后瞻。

零宽断言
正则 名称 描述
(?=exp) 正向前瞻 匹配exp前面的位置
(?!exp) 负向前瞻 匹配后面不是exp的位置
(?<=exp) 正向后瞻 匹配exp后面的位置不支持
(?<!exp) 负向后瞻 匹配前面不是exp的位置不支持
正向前瞻用来检查接下来的出现的是不是某个特定的字符集。而负向前瞻则是检查接下来的不应该出现的特定字符串集。零宽断言是不会被捕获的。

var str1 = "bedroom";
var str2 = "bedding";
var reBed = /(bed(?=room))///在我们捕获bed这个字符串时，抢先去看接下来的字符串是不是room
reBed.test(str1)//true
RegExp.$1//bed
RegExp.$2 === ""//true
reBed.test(str2)//false
var str1 = "bedroom";
var str2 = "bedding";
var reBed = /(bed(?!room))/ //要来它后面不能是room
reBed.test(str1)//false
reBed.test(str2)//true
题目，移除hr以外的所有标签，只留下innerText!

var html = "<p><a href='http://www.cnblogs.com/rubylouvre/'>Ruby Louvre</a></p><hr/><p>by <em>司徒正美</em></p>";
var text = html.replace(/<(?!hr)(?:.|\s)*?>/ig,"")
text//Ruby Louvre<hr/>by 司徒正美
边界

一个要与字符类合用的东西。

边界
正则 名称 描述
^ 开头 注意不能紧跟于左中括号的后面
$ 结尾
\b 单词边界 指[a-zA-Z_0-9]之外的字符
\B 非单词边界
题目，设计一个字符串原型方法，实现首字母大写！

var a = "ruby";
String.prototype.capitalize = function () {
return this.replace(/^\w/, function (s) {
return s.toUpperCase();
});
}
a.capitalize()//Ruby
单词边界举例。要匹配的东西的前端或未端不能为英文字母阿拉伯字数字或下横线。

var str = "12w-eefd&efrew";
str.match(/\b\w+\b/g)//12w,eefd,efrew
实例属性 描述
global 是当前表达式模式首次匹配内容的开始位置，从0开始计数。其初始值为-1，每次成功匹配时，index属性都会随之改变。
ignoreCase 返回创建RegExp对象实例时指定的ignoreCase标志（i）的状态。如果创建RegExp对象实例时设置了i标志，该属性返回True，否则返回False，默认值为False。
lastIndex 是当前表达式模式首次匹配内容中最后一个字符的下一个位置，从0开始计数，常被作为继续搜索时的起始位置，初始值为-1， 表示从起始位置开始搜索，每次成功匹配时，lastIndex属性值都会随之改变。(只有使用exec()或test()方法才会填入，否则为0)
multiLine 返回创建RegExp对象实例时指定的multiLine标志（m）的状态。如果创建RegExp对象实例时设置了m标志，该属性返回True，否则返回False，默认值为False。
source 返回创建RegExp对象实例时指定的表达式文本字符串。
var str = "JS's Louvre";
var reg = /\w/g;
reg.exec(str)//J
reg.lastIndex//1
reg.exec(str)//S
reg.lastIndex//2
reg.exec(str)//s
reg.lastIndex//4
reg.exec(str)//L
reg.lastIndex//6





---------------------
# 类的模拟
## class
```js
class SuperClass {
	constructor(params) {
		super(params)
		....
	}
	method1(){
    ...
	}
	static smethod(){
		.....
	}
}

class ClassName extends SuperClass {
	constructor(params) {
		super(params)
		....
	}
	get property() {return this._value;}
	set property(v) { this._value = v;}
	method1() {
	  super.method1();
  }
}
```
## 一、构造函数法
这是经典方法，也是教科书必教的方法。它用构造函数模拟"类"，在其内部用this关键字指代实例对象。
　　function Cat() {
　　　　this.name = "大毛";
　　}
生成实例的时候，使用new关键字。
　　var cat1 = new Cat();
　　alert(cat1.name); // 大毛
类的属性和方法，还可以定义在构造函数的prototype对象之上。
　　Cat.prototype.makeSound = function(){
　　　　alert("喵喵喵");
　　}
关于这种方法的详细介绍，请看我写的系列文章《Javascript 面向对象编程》，这里就不多说了。它的主要缺点是，比较复杂，用到了this和prototype，编写和阅读都很费力。

## 二、Object.create()法
为了解决"构造函数法"的缺点，更方便地生成对象，Javascript的国际标准ECMAScript第五版（目前通行的是第三版），提出了一个新的方法Object.create()。
用这个方法，"类"就是一个对象，不是函数。
　　var Cat = {
　　　　name: "大毛",
　　　　makeSound: function(){ alert("喵喵喵"); }
　　};
然后，直接用Object.create()生成实例，不需要用到new。
　　var cat1 = Object.create(Cat);
　　alert(cat1.name); // 大毛
　　cat1.makeSound(); // 喵喵喵
目前，各大浏览器的最新版本（包括IE9）都部署了这个方法。如果遇到老式浏览器，可以用下面的代码自行部署。
　　if (!Object.create) {
　　　　Object.create = function (o) {
　　　　　　 function F() {}
　　　　　　F.prototype = o;
　　　　　　return new F();
　　　　};
　　}
这种方法比"构造函数法"简单，但是不能实现私有属性和私有方法，实例对象之间也不能共享数据，对"类"的模拟不够全面。

## 三、极简主义法
荷兰程序员Gabor de Mooij提出了一种比Object.create()更好的新方法，他称这种方法为"极简主义法"（minimalist approach）。这也是我推荐的方法。
3.1 封装
这种方法不使用this和prototype，代码部署起来非常简单，这大概也是它被叫做"极简主义法"的原因。
首先，它也是用一个对象模拟"类"。在这个类里面，定义一个构造函数createNew()，用来生成实例。
　　var Cat = {
　　　　createNew: function(){
　　　　　　// some code here
　　　　}
　　};
然后，在createNew()里面，定义一个实例对象，把这个实例对象作为返回值。
　　var Cat = {
　　　　createNew: function(){
　　　　　　var cat = {};
　　　　　　cat.name = "大毛";
　　　　　　cat.makeSound = function(){ alert("喵喵喵"); };
　　　　　　return cat;
　　　　}
　　};
使用的时候，调用createNew()方法，就可以得到实例对象。
　　var cat1 = Cat.createNew();
　　cat1.makeSound(); // 喵喵喵
这种方法的好处是，容易理解，结构清晰优雅，符合传统的"面向对象编程"的构造，因此可以方便地部署下面的特性。
3.2 继承
让一个类继承另一个类，实现起来很方便。只要在前者的createNew()方法中，调用后者的createNew()方法即可。
先定义一个Animal类。
　　var Animal = {
　　　　createNew: function(){
　　　　　　var animal = {};
　　　　　　animal.sleep = function(){ alert("睡懒觉"); };
　　　　　　return animal;
　　　　}
　　};
然后，在Cat的createNew()方法中，调用Animal的createNew()方法。
　　var Cat = {
　　　　createNew: function(){
　　　　　　var cat = Animal.createNew();
　　　　　　cat.name = "大毛";
　　　　　　cat.makeSound = function(){ alert("喵喵喵"); };
　　　　　　return cat;
　　　　}
　　};
这样得到的Cat实例，就会同时继承Cat类和Animal类。
　　var cat1 = Cat.createNew();
　　cat1.sleep(); // 睡懒觉
3.3 私有属性和私有方法
在createNew()方法中，只要不是定义在cat对象上的方法和属性，都是私有的。
　　var Cat = {
　　　　createNew: function(){
　　　　　　var cat = {};
　　　　　　var sound = "喵喵喵";
　　　　　　cat.makeSound = function(){ alert(sound); };
　　　　　　return cat;
　　　　}
　　};
上例的内部变量sound，外部无法读取，只有通过cat的公有方法makeSound()来读取。
　　var cat1 = Cat.createNew();
　　alert(cat1.sound); // undefined
3.4 数据共享
有时候，我们需要所有实例对象，能够读写同一项内部数据。这个时候，只要把这个内部数据，封装在类对象的里面、createNew()方法的外面即可。
　　var Cat = {
　　　　sound : "喵喵喵",
　　　　createNew: function(){
　　　　　　var cat = {};
　　　　　　cat.makeSound = function(){ alert(Cat.sound); };
　　　　　　cat.changeSound = function(x){ Cat.sound = x; };
　　　　　　return cat;
　　　　}
　　};
然后，生成两个实例对象：
　　var cat1 = Cat.createNew();
　　var cat2 = Cat.createNew();
　　cat1.makeSound(); // 喵喵喵
这时，如果有一个实例对象，修改了共享的数据，另一个实例对象也会受到影响。
　　cat2.changeSound("啦啦啦");
　　cat1.makeSound(); // 啦啦啦


Function class() {
    This.x = 0;
}

class.prototype.fun1 = function(){
    ….
}
