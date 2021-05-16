**学习目标**：<br />能够说出什么是 jQuery <br />能够说出 jQuery 的优点<br />能够简单使用 jQuery<br />能够说出 DOM 对象和 jQuery 对象的区别<br />能够写出常用的 jQuery 选择器 <br />能够操作 jQuery 样式<br />能够写出常用的 jQuery 动画 <br />能够操作 jQuery 属性<br />能够操作 jQuery 元素<br />能够操作 jQuery 元素尺寸、位置<br />能够说出4种常见的注册事件 <br />能够说出 on 绑定事件的优势<br />能够说出 jQuery 事件委派的优点以及方式<br />能够说出绑定事件与解绑事件<br />能够说出 jQuery 对象的拷贝方法<br />能够说出 jQuery 多库共存的2种方法<br />能够使用 jQuery 插件
<a name="puaTB"></a>
## 概念

- jQuery 是一个快速、简洁的 JavaScript 库，其设计的宗旨是“write Less，Do More”，即倡导写更少的代码，做更多的事情。<br />
- j 就是 JavaScript；   Query 查询； 意思就是查询js，把js中的DOM操作做了封装，我们可以快速的查询使用里面的功能。<br />
- jQuery 封装了 JavaScript 常用的功能代码，优化了 DOM 操作、事件处理、动画设计和 Ajax 交互。<br />
- 学习jQuery本质： 就是学习调用这些函数（方法）。<br />
<a name="OpScR"></a>
## 一、jQuery中常见的两种入口函数
// 第一种: 简单易用。（推荐）<br />$(function () {    <br />    ...  // 此处是页面 DOM 加载完成的入口<br />}) ;  <br />// 第二种: 繁琐，但是也可以实现<br />$(document).ready(function(){<br />   ...  //  此处是页面DOM加载完成的入口<br />});

- 等着 DOM 结构渲染完毕即可执行内部代码，不必等到所有外部资源加载完成，jQuery 帮我们完成了封装。<br />
- 相当于原生 js 中的 DOMContentLoaded。<br />
- 不同于原生 js 中的 load 事件是等页面文档、外部的 js 文件、css文件、图片加载完毕才执行内部代码。



$是jQuery的顶级对象，相当于原生JavaScript中的 window。把元素利用$包装成jQuery对象，就可以调用jQuery 的方法。
<a name="gj9DD"></a>
###  jQuery 对象和 DOM 对象
使用 jQuery 方法和原生JS获取的元素是不一样的，总结如下 : 

1. 用原生 JS 获取来的对象就是 DOM 对象<br />
1. jQuery 方法获取的元素就是 jQuery 对象。<br />
1. jQuery 对象本质是： 利用$对DOM 对象包装后产生的对象（伪数组形式存储）。
> 注意：**只有 jQuery 对象才能使用 jQuery 方法，DOM 对象则使用原生的 JavaScirpt 方法**。
> getElementsByTagName("div")    //这个方法返回值为DOM对象的集合
> $("div")    //这个方法返回的是jQuery对象，它封装了DOM对象。

<a name="51v0b"></a>
###  jQuery 对象和 DOM 对象转换
DOM 对象与 jQuery 对象之间是可以相互转换的。因为原生js 比 jQuery 更大，原生的一些属性和方法 jQuery没有给我们封装. 要想使用这些属性和方法需要把jQuery对象转换为DOM对象才能使用。
<a name="ZgWJL"></a>
####  1.DOM对象转换成jQuery对象，方法只有一种
var box = document.getElementById('box');  // 获取DOM对象<br />var jQueryObject = $(box);  // 把DOM对象转换为 jQuery 对象
<a name="3VWEQ"></a>
#### 2.jQuery 对象转换为 DOM 对象有两种方法：
//   2.1 jQuery对象[索引值]<br />var domObject1 = $('div')[0]<br />//   2.2 jQuery对象.get(索引值)<br />var domObject2 = $('div').get(0)
<a name="vabY7"></a>
### jQuery 选择器
基础选择器<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612010624856-6bd3c167-a70f-4d44-b03d-12c41d03acde.png#align=left&display=inline&height=210&margin=%5Bobject%20Object%5D&name=image.png&originHeight=327&originWidth=968&size=36527&status=done&style=none&width=623)<br />层级选择器<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612010681885-3552e756-cf2a-4d16-9b67-17cd1f88e820.png#align=left&display=inline&height=90&margin=%5Bobject%20Object%5D&name=image.png&originHeight=140&originWidth=998&size=21731&status=done&style=none&width=645)<br />筛选选择器<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612010720257-9de9f24d-91c4-4744-87a1-f14662bb73dd.png#align=left&display=inline&height=182&margin=%5Bobject%20Object%5D&name=image.png&originHeight=277&originWidth=966&size=36496&status=done&style=none&width=633)<br />
<a name="pRY08"></a>
## 二、使用方法
<a name="Vdt46"></a>
### 一、jQuery 设置样式
<a name="Lf5hU"></a>
#### 1.（ 操作 css 方法）
// 1.参数只写属性名，则是返回属性值<br />var strColor = $(this).css('color');<br />// 2.  参数是属性名，属性值，逗号分隔，是设置一组样式，属性必须加引号，值如果是数字可以不用跟单位和引号<br />$(this).css(''color'', ''red'');<br />// 3.  参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开， 属性可以不用加引号<br />$(this).css({ "color":"white","font-size":"20px"});
<a name="c7f62296"></a>
#### 2.设置类样式方法  不会影响原先类名
作用等同于以前的 classList，可以操作类样式， 注意操作类里面的参数不要加点。<br />// 1.添加类<br />$("div").addClass("current");<br />// 2.删除类<br />$("div").removeClass("current");<br />// 3.切换类<br />$("div").toggleClass("current");<br />$('div').hasClass('current');   //返回布尔值，是否含有名称为current的类
<a name="1fILf"></a>
### 二、jQuery 里面的排他思想
// 想要多选一的效果，排他思想：当前元素设置样式，其余的兄弟元素清除样式。<br />$(this).css(“color”,”red”);<br />$(this).siblings( ). css(“color”,””);
<a name="tMWS8"></a>
### 三、隐式迭代
// 遍历内部 DOM 元素（伪数组形式存储）的过程就叫做隐式迭代。<br />// 简单理解：给匹配到的所有元素进行循环遍历，执行相应的方法，而不用我们再进行循环，简化我们的操作，方便我们调用。<br />$('div').hide( );  // 页面中所有的div全部隐藏，不用循环操作
<a name="Ge5W0"></a>
### 四、链式编程
// 链式编程是为了节省代码量，看起来更优雅。<br />$(this).css('color', 'red').sibling().css('color', ''); 
<a name="Lhz8Z"></a>
### 五、jQuery 效果
	jQuery 给我们封装了很多动画效果，最为常见的如下：

- 显示隐藏：show() / hide() / toggle() ;<br />
- 划入画出：slideDown() / slideUp() / slideToggle() ; <br />
- 淡入淡出：fadeIn() / fadeOut() / fadeToggle() / fadeTo() ; <br />
- 自定义动画：animate( ) ;

**注意：**<br />**动画或者效果一旦触发就会执行，如果多次触发，就造成多个动画或者效果排队执行。**<br />**jQuery为我们提供另一个方法，可以停止动画排队：stop() ;**
<a name="XFfGJ"></a>
#### 显示隐藏 
show/hide/toggle方法一样，toggle一般不带参数，直接显示/隐藏即可<br />语法： show([ speed, [easing], [fn]])<br />1、参数都可以省略，无动画效果直接显示。<br />2、speed：三种预定速度之一的字符串（"slow","normal","fast"）或者表示动画时长的毫秒数，如1000<br />3、easing:用来指定切换效果，默认是"swing",可用参数linear<br />4、fn回调函数，在动画完成时执行的函数，每个元素执行一次
<a name="IJTIT"></a>
#### 滑入滑出
slideDown() / slideUp() / slideToggle() ; <br />1、参数都可以省略，无动画效果直接显示。<br />2、speed：三种预定速度之一的字符串（"slow","normal","fast"）或者表示动画时长的毫秒数，如1000<br />3、easing:用来指定切换效果，默认是"swing",可用参数linear<br />4、fn回调函数，在动画完成时执行的函数，每个元素执行一次
<a name="rFBRK"></a>
#### 淡入淡出
淡入淡出动画，常见有四个方法：fadeIn() / fadeOut() / fadeToggle() / fadeTo() ; <br />1、参数都可以省略，无动画效果直接显示。<br />2、speed：三种预定速度之一的字符串（"slow","normal","fast"）或者表示动画时长的毫秒数，如1000<br />3、easing:用来指定切换效果，默认是"swing",可用参数linear<br />4、fn回调函数，在动画完成时执行的函数，每个元素执行一次<br />**fadeTo( ) **：渐进方式调整到指定的不透明度<br />fadeTo([[speed],opacity,[easing],[fn]])<br />1、opacity 透明度必须写，取值0-1之间<br />2、其他三个参数参考楼上。
<a name="f07iL"></a>
#### 自定义动画
animate(params,[speed],[easing],[fn])<br />1、params,想要更改的样式属性，以对象的形式传递，必须写！，属性名可以不带引号，如果是复合属性则需要采取驼峰命名法，其余参数都可以省略。<br />2、其他三个参数参考楼上。
<a name="slRi4"></a>
#### hover事件切换
jQuery中为我们添加了一个新事件 hover() ; 功能类似 css 中的伪类 :hover <br />hover([over,]out)     // 其中over和out为两个函数

- over:鼠标移到元素上要触发的函数（相当于mouseenter）<br />
- out:鼠标移出元素要触发的函数（相当于mouseleave）<br />
- 如果只写一个函数，则鼠标经过和离开都会触发它
<a name="kTRNG"></a>
### 六、jQuery的属性操作
<a name="WaUHk"></a>
#### 一、得到当前元素的索引号 index( )
$(this).index( )
<a name="czitJ"></a>
#### 二、元素固有属性值 prop( )
所谓元素固有属性就是元素本身自带的属性，比如 <a> 元素里面的 href ，比如 <input> 元素里面的 type。 <br />**获取**属性语法<br />prop（"属性名"）<br />**设置**属性语法<br />prop（"属性"，"属性值"）<br />注意：prop() 除了普通属性操作，更适合操作表单属性：disabled / checked / selected 等。
<a name="b7168ad9"></a>
#### 三、元素自定义属性值 attr( )
用户自己给元素添加的属性，我们称为自定义属性。 比如给 div 添加 index =“1”。 <br />**获取**属性语法<br />attr ( " 属性 " )       //类似原生的getAttribute( )<br />**设置**属性语法<br />attr（"属性"，"属性值"）  //类似原生的setAttribute( )<br />注意：attr() 除了普通属性操作，更适合操作自定义属性。（该方法也可以获取 H5 自定义属性）
<a name="nVC7e"></a>
#### 四、数据缓存 data( )
data() 方法可以在指定的元素上存取数据，并不会修改 DOM 元素结构。一旦页面刷新，之前存放的数据都将被移除。<br />**用data方法附加的数据不会在页面上显示，单纯的是存储在元素上的一个数据，刷新了就没了 ，用data可以获取，用attr获取显示未定义**<br />**获取**数据语法<br />data("name")         //向被选元素获取数据，或者以data-开头的属性名的属性值<br />**附加**数据语法<br />data("name","value")  //向被选元素附加数据<br />**在获取以data-开头的属性名的属性值的情况下，若属性值为数字类型，如索引，则**<br />el.data("index") = el.attr("data-index")<br />        数字型                字符串型
```javascript
<span data-index = "1">123</span>  
<script>
		$(function () {
			// 3. 数据缓存 data() 这个里面的数据是存放在元素的内存里面
			// $("span").data("uname", "andy");
			console.log(typeof $("span").data("index"));     //number
			console.log(typeof $("span").attr("data-index"));   //string
		})
	</script>
```
<br />
<a name="kD43X"></a>
#### 五、jQuery 文本属性值
jQuery的文本属性值常见操作有三种：html() / text() / val() ; 分别对应JS中的 innerHTML 、innerText 和 value 属性。主要针对元素的内容还有表单的值操作。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612183907647-f8fc0acf-cda5-4ee8-83e1-6c6a1c3d138b.png#align=left&display=inline&height=441&margin=%5Bobject%20Object%5D&name=image.png&originHeight=470&originWidth=767&size=72409&status=done&style=none&width=719)<br />注意：html() 可识别标签，text() 不识别标签。
<a name="UT6lJ"></a>
#### 六、jQuery 元素操作 each（）
<a name="F6F94"></a>
##### 一、遍历元素  each（）
	jQuery 隐式迭代是对同一类元素做了同样的操作。 如果想要给同一类元素做不同操作，就需要用到遍历。**既可以遍历对象中的每一项，也可以遍历数组中的每一个元素。**<br />**方法一：**<br />$("div").each(function ( index,domEle ) { xxx: } )<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612184947248-f95bce2a-cd4d-44fe-8dbb-05455c227863.png#align=left&display=inline&height=105&margin=%5Bobject%20Object%5D&name=image.png&originHeight=105&originWidth=620&size=11570&status=done&style=none&width=620)<br />注意：此方法用于遍历 jQuery 对象中的每一项，回调函数中元素为 DOM 对象，想要使用 jQuery 方法需要转换。<br />**方法二：**<br />$.each(object , function ( index , element) { xxx; } )<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612185174797-e9a2bee2-3461-47c9-8bfc-159ffa0aa5e3.png#align=left&display=inline&height=67&margin=%5Bobject%20Object%5D&name=image.png&originHeight=67&originWidth=639&size=6884&status=done&style=none&width=639)<br />注意：此方法用于遍历 jQuery 对象中的每一项，回调函数中元素为 DOM 对象，想要使用 jQuery 方法需要转换。
```javascript
<body>
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <script>
        $(function() {
            // 如果针对于同一类元素做不同操作，需要用到遍历元素（类似for，但是比for强大）
            var sum = 0;
            var arr = ["red", "green", "blue"];
            // 1. each() 方法遍历元素 
            $("div").each(function(i, domEle) {
                // 回调函数第一个参数一定是索引号  可以自己指定索引号号名称
                // console.log(i);
                // 回调函数第二个参数一定是 dom 元素对象，也是自己命名
                // console.log(domEle);  // 使用jQuery方法需要转换 $(domEle)
                $(domEle).css("color", arr[i]);
                sum += parseInt($(domEle).text());
            })
            console.log(sum);
            // 2. $.each() 方法遍历元素 主要用于遍历数据，处理数据
            // $.each($("div"), function(i, ele) {
            //     console.log(i);
            //     console.log(ele);
            // });
            // $.each(arr, function(i, ele) {
            //     console.log(i);
            //     console.log(ele);
            // })
            $.each({
                name: "andy",
                age: 18
            }, function(i, ele) {
                console.log(i); // 输出的是 name age 属性名
                console.log(ele); // 输出的是 andy  18 属性值
            })
        })
    </script>
</body>
```
<a name="MIigY"></a>
##### 二、创建、添加、删除
jQuery方法操作元素的创建、添加、删除方法很多，则重点使用部分，可以用模板字符串添加。<br />如下：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612185618767-64a82ac1-a004-4dd1-92e7-f3888b469a58.png#align=left&display=inline&height=877&margin=%5Bobject%20Object%5D&name=image.png&originHeight=877&originWidth=747&size=58327&status=done&style=none&width=747)
<a name="fPuzz"></a>
#### 七、jQuery 尺寸操作
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612271244546-e17b975d-0a1c-421c-8c2c-cc6992407e6c.png#align=left&display=inline&height=262&margin=%5Bobject%20Object%5D&name=image.png&originHeight=262&originWidth=656&size=64125&status=done&style=none&width=656)
<a name="jJpCE"></a>
#### 八、jQuery 位置操作
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612271287619-a577ab75-c24c-497a-a3cb-ec725551b5cf.png#align=left&display=inline&height=419&margin=%5Bobject%20Object%5D&name=image.png&originHeight=419&originWidth=700&size=42286&status=done&style=none&width=700)
<a name="pY07A"></a>
### 七、jQuery事件注册
jQuery 为我们提供了方便的事件注册机制，操作优缺点如下：

- 优点: 操作简单，且不用担心事件覆盖等问题。<br />
- 缺点: 普通的事件注册不能做事件委托，且无法实现事件解绑，需要借助其他方法。

**语法**：<br />element.事件（function（）{ }）<br />$("div").click (function ( ) { 事件处理程序 } )<br />其他和原生基本一致：mouseover、mouseout、blur、focus、change、keyup、keydown、resize、scroll
<a name="zoBCR"></a>
#### 事件处理 on() 绑定事件
因为普通注册事件方法的不足，jQuery又创建了多个新的事件绑定方法bind() / live() / delegate() / on()等，其中最好用的是: on()
<a name="TlD80"></a>
##### 可以绑定多个事件，多个处理事件处理程序
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612316716440-959b41d2-78e0-4a24-a10e-ab1ca250c7ac.png#align=left&display=inline&height=106&margin=%5Bobject%20Object%5D&name=image.png&originHeight=106&originWidth=629&size=5136&status=done&style=none&width=629)<br />如果处理事件相同<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612316749344-65e8775c-0c15-40e7-a07b-7fb75fbc5503.png#align=left&display=inline&height=93&margin=%5Bobject%20Object%5D&name=image.png&originHeight=93&originWidth=628&size=4769&status=done&style=none&width=628)
<a name="5uVOk"></a>
##### 事件委托
有一种情况，新动态添加的元素，在页面一开始绑定事件的时候还不存在，会造成事件绑定失败的情况，这里就需要用冒泡的办法绑定事件委托<br />例：ul动态添加了小li,后来生成的小li 未绑定点击事件<br />    $( " ul " ). on( " click ", " li ", function( ) { } )   <br />
<br />这里面的this指向e.target（触发元素）
<a name="VS23D"></a>
#### 事件处理 off() 解绑事件
当某个事件上面的逻辑，在特定需求下不需要的时候，可以把该事件上的逻辑移除，这个过程我们称为事件解绑。jQuery 为我们提供 了多种事件解绑方法：die() / undelegate() / off() 等，甚至还有只触发一次的事件绑定方法 one()，在这里我们重点讲解一下 off() ;<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612317145665-1f25b13a-593e-493f-8b77-cb79aacce1b9.png#align=left&display=inline&height=185&margin=%5Bobject%20Object%5D&name=image.png&originHeight=185&originWidth=634&size=13382&status=done&style=none&width=634)
<a name="SRDlf"></a>
#### 事件处理 one() 只触发一次
 $("p").one ("click", function() {<br />                alert(11);<br />            })
<a name="lKTuA"></a>
#### 事件处理 trigger() 自动触发事件
有些时候，在某些特定的条件下，我们希望某些事件能够自动触发, 比如轮播图自动播放功能跟点击右侧按钮一致。可以利用定时器自动触发右侧按钮点击事件，不必鼠标点击触发。由此 jQuery 为我们提供了两个自动触发事件 trigger() 和 triggerHandler() ;<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612317487120-067f55be-a111-4182-a679-b9ac48fd44f8.png#align=left&display=inline&height=298&margin=%5Bobject%20Object%5D&name=image.png&originHeight=298&originWidth=655&size=16985&status=done&style=none&width=655)
<a name="xsFZc"></a>
### 八、jQuery事件对象
	jQuery 对DOM中的事件对象 event 进行了封装，兼容性更好，获取更方便，使用变化不大。事件被触发，就会有事件对象的产生。<br />el.on( type , function ( e ) {<br />e.preventDefault ( ); <br />})<br />
<br />**阻止默认行为**：e.preventDefault ( );  或者  return false;<br />**阻止冒泡**：e.stopPropagation ( )<br />

<a name="n1Cq4"></a>
### 九、jQuery拷贝对象
	jQuery中分别为我们提供了将一个或多个对象的内容合并到目标对象。内容如下。$.extend( )<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612318232622-1195ca58-9b78-46f6-ae8d-32b836a94fc7.png#align=left&display=inline&height=263&margin=%5Bobject%20Object%5D&name=image.png&originHeight=263&originWidth=640&size=19098&status=done&style=none&width=640)
<a name="hDGTx"></a>
### 十、 jQuery 多库共存
实际开发中，很多项目连续开发十多年，jQuery版本不断更新，最初的 jQuery 版本无法满足需求，这时就需要保证在旧有版本正常运行的情况下，新的功能使用新的jQuery版本实现，这种情况被称为，jQuery 多库共存。<br />**语法**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612319655042-830ddcb4-5e33-46d9-b4ec-378f2991b8bc.png#align=left&display=inline&height=118&margin=%5Bobject%20Object%5D&name=image.png&originHeight=118&originWidth=425&size=6799&status=done&style=none&width=425)**<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />

