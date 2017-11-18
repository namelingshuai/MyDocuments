# BOM讲解
## 体验window对象
```javascript
    js把浏览器抽象成了一个对象，这个对象就是js中的顶级对象window;
        window里面有很多的属性和方法，我们学习BOM就是学习这些属性和方法;

    console.log(window);//js内置对象
    console.log(typeof window);//js内置对象

    window有很多内置的属性和方法;

    属性和方法;
    console.log(window.top);//属性之一；只读;
    console.log(window.name);//属性之一；可以被赋值；
    console.log(window.aaa);//undefined；

    window可以省略
    window.alert("我是window的一个方法");

    console是window的一个属性，只不过这个属性本身也是一个对象;
    window.console.log(111);
```

## 全局变量和顶级函数
```javascript
   全局变量和顶级函数都是window里面的属性和方法;

    全局变量和顶级函数
    var num = 111;
    function fn(){
        alert(222);
        //函数内部的函数就不是window的方法了
        function fn2(){
            alert(333);
        }
    }

    window的属性和方法
    alert(window.num);
    window.fn();
    window.fn2();
```

## 方法-alert-confirm-prompt
```javascript
   window中有很多的方法：其中alert();confirm();prompt();都是

    window.alert("我是window的一个方法");//没有返回值
    window.confirm("我是window的一个方法");//返回值boolean
    window.prompt("我是window的一个方法");//返回值string，点击取消返回值null；

    都可以省略window
```

## 定时器方法
```javascript
    定时器就是过多长之间执行一段逻辑;
        有两种：1.循环定时器;    2.炸弹定时器;
    
    1.循环定时器;   (每过多久执行一次) (就像闹钟)(反复使用)
        用法：轮播图;
    setInterval(function () {
        console.log(111);
    },1000);
    
    2.炸弹定时器;   (过多久执行完毕) (就像炸弹)(一次性)
        用法：关闭广告;
    setTimeout(function () {
        console.log(222);
    },1000);
```

## 定时器高级操作
```javascript
   定时器的高级操作
    
    1.定时器有返回值;返回值就是这个页面上的定时器的编号(就是第几个执行的定时器)
        返回值是数值类型，用来关闭定时器的;
    var timer1 = null;//  "";  0;   undefined;
    var timer2 = null;//  "";  0;   undefined;

    //定义定时器
    timer1 = setInterval(function () {
        console.log(111);
    },1000);

    alert(timer1);
    alert(typeof timer1);

    //第几个执行的定时器，返回值就是几;
    timer2 = setInterval(function () {
        console.log(111);
    },1000);

    alert(timer2);
    alert(typeof timer2);
    
    2.停止定时器;(也叫清除定时器)  （两种定时器都可以清除）
        clearInterval/clearTimeout();
    var num = 1;
    var timer = setInterval(function () {
        if(num == 4){//等于4的时候只打印了3次
            clearInterval(timer);//停止定时器
            return;//禁止下面的代码执行是return;
        }
        console.log(111);
        num++;
    },1000);

    注意点：clearInterval是下一次定时器不在执行了！函数要执行完毕;
    注意点：return是函数到此停止，下次是否执行和return无关;
    
    3.定时器的执行是在script标签内全部代码执行完毕值后;
    setInterval(function () {
        console.log(111);
    },1000);//定时器是在页面加载完毕就执行的，但是要在script标签内其他逻辑之后;

    //for循环在定时器之后
    for(var i=1;i<=100000;i++){
        console.log("我是for循环执行的内容");
    }
    
    4.定时器的名字;（保证一个定时器一个名字，不能两个公用一个名字，将来关闭不了）
        定时器不会层叠,所以一个定会器一个名字，能够想要关闭的时候关闭掉;

```

## 浏览器对象里面有很多属性
```javascript
     有很多属性;
        
            1.普通属性;  name；值是简单类型;

            2.特殊属性;  history/location/navigator/document(DOM)/console/screen....
                属性值都是对象;

```

## 属性（都是对象）- lpcation和地址有关
```javascript
       location使用的时候可以省略window;是window下面的一个属性;
            是一个对象，里面有属性和方法;这是一个和地址有关的属性;
        
        window.location的属性;
        都是和服务器有关的属性
        console.log(window.location.href);    //地址
        console.log(window.location.hash    );//返回url中#后面的内容，包含#
        console.log(window.location.host    );//主机名，包括端口
        console.log(window.location.hostname);//主机名
        console.log(window.location.pathname);//url中的路径部分
        console.log(window.location.protocol);//协议 一般是http、https
        console.log(window.location.search	);//查询字符串
        
        location的方法;  页面跳转
            assign()/replace(): 页面跳转
            reload(): 刷新页面;
            href属性;

        点击页面触动函数;
        document.onclick = function () {
            assign();让页面跳转到其他页面;(能够回退--有历史记录)
            location.assign("http://www.jd.com");

            replace();让页面跳转到其他页面;(不能回退--无历史记录)
            location.replace("http://www.taobao.com");

            reload(): 刷新页面;
            location.reload();
        
            href属性; 也是页面地址;可以控制页面跳转(能够回退--有历史记录)
            location.href = "http://www.baidu.com";//用的最多;
        }
```

## 属性（都是对象）- history和历史有关
```css
   div {
            width: 100px;
            height: 100px;
            background-color: skyblue;
            margin: 10px;
            cursor: pointer;
        }
```
```html
    <input type="text"/>
    <div id="box1">前进</div>
    <div id="box2">刷新</div>
    <div id="box3">点击我跳转到domo页面</div>

```

```javascript
        history使用的时候可以省略window;是window下面的一个属性;
            是一个对象，里面有方法;这是一个和历史记录有关的属性;
        back();forward();go();

        用document页面跳转
        var box1 = document.getElementById("box1");
        var box2 = document.getElementById("box2");
        var box3 = document.getElementById("box3");
        点击box3跳转页面
        box3.onclick = function () {
            location.href = "demo.html";
        }

        点击box2,前进
        box1.onclick = function () {
            //history.forward();//前进
            history.go(1);//前进
        }

        点击box2是刷新
        box2.onclick = function () {
            history.go(0);//0刷新;  1前进，  -1后退
        }
```

## 属性（都是对象) - navigator和浏览器和系统有关
```javascript
    navigator和系统和浏览器有关;
    
    - platform
    通过platform可以判断浏览器所在的系统平台类型.
    console.log(navigator.platform);


    - userAgent
    通过userAgent可以判断用户浏览器的类型
    console.log(navigator.userAgent);
    
    浏览器识别
    function myBrowser(){
        var userAgent = navigator.userAgent; //取得浏览器的userAgent字符串
        var isOpera = userAgent.indexOf("Opera") > -1;
        if (isOpera) {
            return "Opera"
        }; //判断是否Opera浏览器
        if (userAgent.indexOf("Firefox") > -1) {
            return "FF";
        } //判断是否Firefox浏览器
        if (userAgent.indexOf("Chrome") > -1){
            return "Chrome";
        }
        if (userAgent.indexOf("Safari") > -1) {
            return "Safari";
        } //判断是否Safari浏览器
        if (userAgent.indexOf("compatible") > -1 && userAgent.indexOf("MSIE") > -1 && !isOpera) {
            return "IE";
        }; //判断是否IE浏览器5-10

    }
    
    以下是调用上面的函数
    var mb = myBrowser();
    if ("IE" == mb) {
        alert("我是 IE");
    }
    if ("FF" == mb) {
        alert("我是 Firefox");
    }
    if ("Chrome" == mb) {
        alert("我是 Chrome");
    }
    if ("Opera" == mb) {
        alert("我是 Opera");
    }
    if ("Safari" == mb) {
        alert("我是 Safari");
    }
```
# DOM的概述
## DOM概述
```javascript
    DOM：文档对象模型;（还是一个js的内置对象，以window的一个属性形式存在）
        里面的顶级对象是document；   window.document；window可以省略
    console.log(window.document);
    console.dir(document);//以对象形式打印内容
    
    DOM对象也是对象，里面有很多的属性和方法;（类似Array，Date...但是属性和方法不同）
    
    DOM是由节点构成的;以树状结构在内存中加载!
    
    常见节点包括四类：
        1.document;                   文档节点;
        2.各种标签;                    元素节点;
        3.各种标签上的属性;             属性节点;
        4.标签内容                     文本节点;
    
    DOM对象，节点，DOM元素.....  都可以成为DOM对象;
            就有属于DOM的属性和方法;

```

## 获取节点
```html
    <ul class="ul">
        <li name="aaa">我是li1</li>
        <li class="box">我是li2</li>
        <li id="li3" name="bbb">我是li3</li>
        <li class="box">我是li4</li>
        <li name="aaa">我是li5</li>
    </ul>
```
```javascript
    1.元素节点的获取常见的有6种：常用2种;
    a.通过id获取标签;document.getElementById(id名);
    console.dir(document);
    console.log(document.getElementById("li3"));
    注意点：通过id获取;  获取的是单个元素节点;   如果无法获取返回null;
    console.log(document.getElementById("li3333333"));
    调用者：只能是document，不能是任何标签;
    console.dir(document.getElementById("li3"));

    b.通过标签名获取标签;  document.getElementsByTagName();
        返回一个伪数组;哪怕只有1个也返回数组;
    console.log(document.getElementsByTagName("li"));//[5*li]
    console.log(document.getElementsByTagName("ul"));//[ul]
    console.log(document.getElementsByTagName("a"));//[]
        //注意点：1.如果想要使用元素，必须从数组中取出来，一般都是for循环;
        //注意点：2.如果只有一个[0]; 切记不能直接操作数组;
    var ul = document.getElementsByTagName("ul")[0]
    console.log(ul);
    //不同点：可以利用标签缩小范围查找;
    console.log(document.getElementsByTagName("li"));//[5*li]
    console.log(document.getElementsByTagName("ul"));//[ul]
    console.log(document.getElementsByTagName("a"));//[]
        //注意点：1.如果想要使用元素，必须从数组中取出来，一般都是for循环;
        //注意点：2.如果只有一个[0]; 切记不能直接操作数组;
    var ul = document.getElementsByTagName("ul")[0]
    console.log(ul);
    //不同点：可以利用标签缩小范围查找;
    console.log(ul.getElementsByTagName("li"));//ul里面的所有li

    c.通过类名获取标签;  document.getElementsByClassName();
        返回一个伪数组;哪怕只有1个也返回数组;
        console.log(document.getElementsByClassName("box"));//[5*li]
        console.log(document.getElementsByClassName("ul"));//[ul]
        console.log(document.getElementsByClassName("a"));//[]
            注意点：1.如果想要使用元素，必须从数组中取出来，一般都是for循环;
            注意点：2.如果只有一个[0]; 切记不能直接操作数组;
        var ul = document.getElementsByClassName("ul")[0]
        console.log(ul);
        不同点：可以利用标签缩小范围查找;
        console.log(ul.getElementsByClassName("li"));//ul里面的所有li
        ie678不支持这个方法;

    d.通过name属性获取标签;  document.getElementsByName();
        返回一个伪数组;哪怕只有1个也返回数组;
        console.log(document.getElementsByName("aaa"));//[5*li]
        console.log(document.getElementsByName("bbb"));//[ul]
        console.log(document.getElementsByName("ccc"));//[]
        注意点：1.如果想要使用元素，必须从数组中取出来，一般都是for循环;
        ie678支持这个方法,但是获取不到元素;

    e.document.querySelector();根据css获取标签;  获取单个标签
    console.log(document.querySelector("ul"));//找到第一个符合条件的立刻返回
    console.log(document.querySelector("li"));//找到第一个符合条件的立刻返回
    console.log(document.querySelector("#li3"));//找到第一个符合条件的立刻返回
    console.log(document.querySelector(".box"));//找到第一个符合条件的立刻返回

    f.document.querySelectorAll();  根据css获取标签;  获取全部标签
        全部都是数组;
    console.log(document.querySelectorAll("ul"));//满足条件全部获取
    console.log(document.querySelectorAll("li"));//满足条件全部获取
    console.log(document.querySelectorAll("#li3"));//满足条件全部获取
    console.log(document.querySelectorAll(".box"));//满足条件全部获取

    总结：
        1.用的最多：byId/byTagName();          获取单个/多个DOM对象;
        2.几步不用：byClassName/byName();      几乎不用
        3.H5C3用： querySelector/All()        H5C3喜欢用

    2.属性节点的获取;
        了解
    var box3 = document.getElementById("li3");
    console.log(box3.getAttributeNode("id"));

    3.文本节点的获取;
    var box3 = document.getElementById("li3");
    console.log(box3.firstChild);
    console.dir(box3.firstChild);

```

## 时间三要素
```css
   div {
            width: 100px;
            height: 100px;
            cursor: pointer;
            background-color: lightgreen;
        }
```
```html
    <div id="box">
        生活让你俯下身子，是为了让你飞的更高...
    </div>
```
```javascript
       很久以前...   js是一门以事件驱动为核心的语言;(三要素)
                (1.事件源;   2.事件;   3.事件驱动程序;)

        经典三部曲;
        1.获取事件原;(几乎全部都是标签(元素节点))
        2.绑定事件;(全部是js定义好的，我们不能自定义: onclick)
        3.书写事件驱动程序;(函数中的功能和逻辑代码，大部分DOM操作)
        
        1.获取事件原;
        var box = document.getElementById("box");//获取单个
        2.绑定事件;onclick:事件源被点击的时候触动事件，事件被触动匿名函数就被执行了
        box.onclick = function () {
            //3.书写事件驱动程序;
            console.log(111);
        }
```

## window.onload事件介绍
```css
    div {
            width: 100px;
            height: 100px;
            cursor: pointer;
            background-color: lightgreen;
        }
```
```javascript
   js和html是顺序执行加载的;如果js获取元素的时候还没有这个元素，那么就会获取null;
            为了避免这个问题,使用window.onload事件;
                作用：页面中所有元素加载完毕才执行函数内部的代码;


        1.获取事件原;
        var box = document.getElementById("box");//获取单个
        console.log(box);
        2.绑定事件;onclick:事件源被点击的时候触动事件，事件被触动匿名函数就被执行了
        box.onclick = function () {
            //3.书写事件驱动程序;
            console.log(111);
        }

        入口函数;
        window.onload = function () {
            //整个页面所有标签全部加载完毕，才执行这个函数，
            //  这时肯定已经有了div标签;

            //1.获取事件原;
            var box = document.getElementById("box");//获取单个
            console.log(box);
            //2.绑定事件;onclick:事件源被点击的时候触动事件，事件被触动匿名函数就被执行了
            box.onclick = function () {
                //3.书写事件驱动程序;
                console.log(111);
            }

            //事件加载也会出现层叠；所以一个元素上的同一事件只能绑定一次;
                //绑定两次后面的把前面的层叠掉
            //box.onclick = function () {
                //3.书写事件驱动程序;
              //  console.log(222);
            }

        }

        所以，一个页面中最好只有一个window.onload；
        window.onload = function () {

        }
```

```html
    <div id="box">
        生活让你俯下身子，是为了让你飞的更高...
    </div>
```

## 案例1-点击按钮弹窗
```javascript
   写到上面必须写入口函数
        window.onload = function () {
            //需求：点击按钮，弹窗;
            //步骤：
            //1.获取事件源;
            //2.绑定事件
            //3.书写事件驱动程序

            //1.获取事件源;
            //获取一个数组，里面只有一个元素，用[0]取出来
            var btn = document.getElementsByTagName("button")[0];
            2.绑定事件
            btn.onclick = function () {
                //3.书写事件驱动程序
                alert("我是一个按钮");
            }

            //方法2：
           // btn.onclick = fn;//千万不能带括号；
            //事件绑定第二种
          //  function fn() {
                //3.书写事件驱动程序
            //    alert("我是一个按钮");
           // }

        }
        
        //供第三种方法使用;
        //function fn() {
            //3.书写事件驱动程序
            //alert("我是一个按钮");
       // }

```
```html
    <!--事件绑定第三种: 执行函数必须带括号;-->
    <button onclick="fn()">按钮1</button>
    <!--<input type="button" value="按钮2"/>-->
```

## 案例2-点击盒子修改样式
```css
   div {
            width: 100px;
            height: 100px;
            cursor: pointer;
            background-color: lightgreen;
        }
        .current {
            width: 300px;
            height: 300px;
            background-color: pink;
        }
```
```javascript
    //写在上面必须写入口函数
        window.onload = function () {
            //需求：点击盒子，改变盒子的样式;(添加类名)
                    //技术点：标签上面的属性全部内置到了元素DOM节点上面：

            //步骤：
            //1.获取事件源
            //2.绑定事件
            //3.书写事件驱动程序

            //1.获取事件源
            //获取的是div的数组，但是里面只有一个，从数组中取出来用
            var div = document.getElementsByTagName("div")[0];
            //2.绑定事件
            div.onclick = function () {
                //3.书写事件驱动程序
                div.title = "aaa";//往div的title属性上添加值;
                //js中的className属性对应的是css中的class;
                div.className = "aaa current";
            }

        }
```
```html
   <div class="aaa">
        天行健，君子以自强不息,<br>
        地势坤，君子以厚德载物;
   </div>
```
#  属性操作
## DOM元素节点属性操作划分、
```css
    div {
            height: 5000px;
        }
```
```html
    <div></div>
    <!--href: 如果什么都不写，刷新页面;(出bug最多)-->
    <!--href: #，跳转到页面最顶端;-->
    <!--href: javascript:;         点了也白点;-->
    <!--href: javascript:void(0);  点了也白点;-->
    <a href="http://www.jd.com">我是a链接</a>
```
```javascript
    元素节点上的css属性我们把他们化为四类：
        1.普通属性;     title; id; src; name...  改了也没有特殊返回;
        2.特殊属性;     href; className; tagName; inerHTML/innerText
        3.表单属性;     type; value;   disabled;checked;selected;
        4.style属性;    style属性是唯一一个值以对象形式存在的属性;
    
    1.普通属性;     title; id; src; name...  改了也没有特殊返回;
    div.onclick = function () {
        div.title = "bbb";
        div.name = "aaa";//....
    }
    
    2.特殊属性;     href; className; tagName; inerHTML/innerText
        href: 页面跳转;如果点击不想跳转return false;
        className: 对应css中的class属性;
        tagName: 标签名全部大写, 只读，不能修改;
        inerHTML/innerText: 两个都是双闭合标签内部的内容;
    
    var input = document.getElementsByTagName("input")[0];
    var div = document.getElementsByTagName("div")[0];
    var a = document.getElementsByTagName("a")[0];
    a.onclick = function () {
        alert("我是a链接，我被点击了！！！");
        //打印input和div的tagName;
        console.log(input.tagName);//标签名全部大写;
        console.log(div.tagName);//标签名全部大写;
       // div.tagName = "LI";//只读，不可写;

        //不想跳转就return false;
        return false;
    }
```

## 案例1-京东狗切换
```css
   img {
            cursor: pointer;
            border: 1px solid #ccc;
        }
        
        div {
            background: url("image/jd1.png") no-repeat center;
            text-align: center;
            line-height: 100px;
        }
```
```html
    <img src="image/jd1.png" alt=""/>
    <a href=""></a>
```
```javascript
    在下面写就不用写入口函数了

        需求1：鼠标进入img改变成另外一个图片;
        需求2：鼠标移开img改变成原来的图片;


        需求1：鼠标进入img改变成另外一个图片;
                思路：就是改变img的src属性;
                    技术点1：鼠标进入事件：onmouseover;
                    技术点2：鼠标移出事件：onmouseout;

        步骤：
        1.获取事件源;
        2.绑定事件
        3.书写事件驱动程序;

        1.获取事件源;
        var img = document.getElementsByTagName("img")[0];
        2.绑定事件
        img.onmouseover = function () {
            //3.书写事件驱动程序;
            img.src = "image/jd2.png";
        }

        需求2：鼠标移开img改变成原来的图片;
        img.onmouseout = function () {
            //3.书写事件驱动程序;
                //this：代指函数调用者;(不是在构造函数中)
            this.src = "image/jd1.png";
        }

```

## 显示和隐藏盒子
```javascript
   
```

## 
```javascript
   
```

## 
```javascript
   
```

## 
```javascript
   
```


## 
```javascript
   
```

## 
```javascript
   
```

## 
```javascript
   
```

## 
```javascript
   
```

## 
```javascript
   
```

## 
```javascript
   
```