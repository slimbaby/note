学习目标：<br />能够通过ID来获取元素<br />能够通过标签名来获取元素<br />能够通过class来获取元素<br />能够通过选择器来获取元素<br />能够获取body和html元素<br />能够给元素注册事件<br />能够修改元素的内容<br />能够区分innerText和innerHTML的区别<br />能够修改像div这类普通元素的属性<br />能够修改表单元素的属性<br />能够修改元素的样式属性<br />能够说出排他操作的一般实现步骤<br />能够使用html5中的dataset方式操作自定义属性<br />能够根据提示完成百度换肤的案例<br />能够根据提示完成全选案例<br />能够根据提示完成tab栏切换案例<br />能够区分元素节点、文本节点、属性节点<br />能够获取指定元素的父元素<br />能够获取指定元素的所有子元素<br />能够说出childNodes和children的区别<br />能够使用createElement创建页面元素<br />能够使用removeChild()方法删除节点<br />能够完成动态生成表格案例<br />能够使用传统方式和监听方式给元素注册事件<br />能够说出事件流执行的三个阶段<br />能够在事件处理函数中获取事件对象<br />能够使用事件对象取消默认行为<br />能够使用事件对象阻止事件冒泡<br />能够使用事件对象获取鼠标的位置<br />能够完成跟随鼠标的天使案例<br />能够说出常用的3-5个键盘事件<br />能够知道如何获取当前键盘按下的是哪个键<br />能够知道浏览器的顶级对象window<br />能够使用window.onload事件<br />能够使用window.onresize事件<br />能够说出两种定时器的区别<br />能够使用location对象的href属性完成页面之间的跳转<br />能够使用location对象获取url中的参数部分<br />能够使用history提供的方法实现页面刷新<br />能够说出常见 offset 系列属性的作用<br />能够说出常见 client 系列属性的作用<br />能够说出常见 scroll 系列属性的作用<br />能够封装简单动画函数<br />能够写出移动端触屏事件<br />能够写出常见的移动端特效<br />能够使用移动端开发插件开发移动端特效<br />能够使用移动端开发框架开发移动端特效<br />能够写出 sessionStorage 数据的存储以及获取<br />能够写出 localStorage 数据的存储以及获取<br />能够说出它们两者的区别
<a name="rm1Ec"></a>
## 概念
<a name="WpRVc"></a>
## API的概念
API（Application Programming Interface，应用程序编程接口）是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件得以访问一组例程的能力，而又无需访问源码，无需理解其内部工作机制细节，只需直接调用使用即可。<br />Web API 是浏览器提供的一套操作浏览器功能和页面元素的 API ( BOM 和 DOM )。
<a name="VcbVN"></a>
## DOM介绍
文档对象模型（Document Object Model，简称DOM）<br />W3C 已经定义了一系列的 DOM 接口，通过这些 DOM 接口可以改变网页的内容、结构和样式。<br />**DOM树**<br />DOM树 又称为文档树模型，把文档映射成树形结构，通过节点对象对其处理，处理的结果可以加入到当前的页面。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612400710413-f9cd2501-7570-482e-a680-4463fc28e581.png#align=left&display=inline&height=256&margin=%5Bobject%20Object%5D&name=image.png&originHeight=309&originWidth=589&size=31113&status=done&style=none&width=488)<br />DOM树 又称为文档树模型，把文档映射成树形结构，通过节点对象对其处理，处理的结果可以加入到当前的页面。

- 文档：一个页面就是一个文档，DOM中使用document表示<br />
- 节点：网页中的所有内容，在文档树中都是节点（标签、属性、文本、注释等），使用node表示<br />
- 标签节点：网页中的所有标签，通常称为元素节点，又简称为“元素”，使用element表示
<a name="d7ab3378"></a>
## 获取元素
<a name="8cVGy"></a>
### 根据ID获取
语法：document.getElementById('id')  直接是ID名称，不用#<br />作用：根据ID获取元素对象<br />参数：id值，区分大小写的字符串<br />返回值：元素对象 或 null
<a name="F7keq"></a>
### 根据标签名获取元素
语法：document.getElementsByTagName('标签名') 或者 element.getElementsByTagName('标签名')   直接是标签名称，不用 . <br />作用：根据标签名获取元素对象<br />参数：标签名<br />返回值：元素对象集合（伪数组，数组元素是元素对象）<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612400965292-ddbb300a-c411-4315-be14-f20ff467300e.png#align=left&display=inline&height=121&margin=%5Bobject%20Object%5D&name=image.png&originHeight=121&originWidth=555&size=7234&status=done&style=none&width=555)
<a name="Sqnd2"></a>
### H5新增获取元素方式
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612415578545-9be5134d-780c-4451-9b77-bbcd8db762ac.png#align=left&display=inline&height=204&margin=%5Bobject%20Object%5D&name=image.png&originHeight=204&originWidth=712&size=40544&status=done&style=none&width=712)
<a name="Go644"></a>
### 获取特殊元素（body，html）
document.body   //返回body元素对象<br />document.documentElement    //返回html元素对象
<a name="v4juz"></a>
## 事件
<a name="xm5qB"></a>
### 事件三要素

- 事件源（谁）：触发事件的元素<br />
- 事件类型（什么事件）： 例如 click 点击事件<br />
- 事件处理程序（做啥）：事件触发后要执行的代码(函数形式)，事件处理函数
<a name="pQXrG"></a>
###  常见的鼠标事件
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612803422308-02d740fd-2de9-4e6e-96b4-d78e5848cfd8.png#align=left&display=inline&height=308&margin=%5Bobject%20Object%5D&name=image.png&originHeight=308&originWidth=706&size=68581&status=done&style=none&width=706)
<a name="ypGvF"></a>
### 一、改变元素内容（获取或设置）
el.innerText<br />从起始位置到终止位置的内容，但它无法识别HTML标签，同时空格和换行也会去掉<br />el.innerHTML<br />从起始位置到终止位置的内容，它可以识别HTML标签，同时保留空格和换行
<a name="2Pg2X"></a>
### 二、常用元素的属性操作
**获取属性的值**
> 元素对象.属性名

**设置属性的值**
> 元素对象.属性名 = 值
> ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804169587-c0c7d2af-4c19-4b78-8877-822042b66176.png#align=left&display=inline&height=99&margin=%5Bobject%20Object%5D&name=image.png&originHeight=99&originWidth=306&size=3773&status=done&style=none&width=306)

<a name="yAg8z"></a>
### 三、样式属性操作
我们可以通过 JS 修改元素的大小、颜色、位置等样式。<br />**常用方式**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612803784295-d183336d-ede2-4b36-87a9-718a3ba59a22.png#align=left&display=inline&height=91&margin=%5Bobject%20Object%5D&name=image.png&originHeight=91&originWidth=656&size=5259&status=done&style=none&width=656)**
<a name="0ucuG"></a>
#### 方式1：通过操作style属性
元素对象style.backgroundColor = "black"<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612803809778-bd581e9b-0aec-424c-ac11-6e96ad8dec4f.png#align=left&display=inline&height=192&margin=%5Bobject%20Object%5D&name=image.png&originHeight=192&originWidth=504&size=13384&status=done&style=none&width=504)
<a name="e1cf21dc"></a>
#### 方式2：通过操作className属性
**元素对象。className = "类名"**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612803900778-a61adeae-f23d-411c-bc68-47f7ade17e25.png#align=left&display=inline&height=206&margin=%5Bobject%20Object%5D&name=image.png&originHeight=206&originWidth=418&size=15233&status=done&style=none&width=418)
<a name="QFNFj"></a>
### 四、表单元素的属性操作
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804086104-2655941a-85b9-4aa0-86cb-4165525c01ec.png#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&name=image.png&originHeight=303&originWidth=709&size=20040&status=done&style=none&width=709)
<a name="9XALw"></a>
### 自定义属性操作 data-
<a name="UlfW5"></a>
#### 一、获取属性值
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804349287-4e06fd86-d6a5-4dcb-b71f-3a6874b41460.png#align=left&display=inline&height=225&margin=%5Bobject%20Object%5D&name=image.png&originHeight=225&originWidth=673&size=36610&status=done&style=none&width=673)
<a name="WYODl"></a>
#### 二、设置属性值
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804398108-692dc1a1-5649-4d96-8701-771448d1841e.png#align=left&display=inline&height=225&margin=%5Bobject%20Object%5D&name=image.png&originHeight=225&originWidth=543&size=11751&status=done&style=none&width=543)
<a name="6IeMR"></a>
#### 三、移除属性
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804433568-4d1fb64d-21a7-4c09-9397-9b68c87406af.png#align=left&display=inline&height=39&margin=%5Bobject%20Object%5D&name=image.png&originHeight=39&originWidth=379&size=1914&status=done&style=none&width=379)<br /> 	// class 不是className<br />        // 移除属性 div.removeAttribute('index');
<a name="6Elsw"></a>
#### H5自定义属性
自定义属性目的：是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。<br />自定义属性获取是通过getAttribute(‘属性’) 获取。但是有些自定义属性很容易引起歧义，不容易判断是元素的内置属性还是自定义属性。<br />H5给我们新增了自定义属性：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804541679-3775089f-7667-4e7b-bb3e-edbe16eeab03.png#align=left&display=inline&height=180&margin=%5Bobject%20Object%5D&name=image.png&originHeight=180&originWidth=366&size=10277&status=done&style=none&width=366)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804567472-302cd76a-d553-4fff-b211-8eeebc734d18.png#align=left&display=inline&height=110&margin=%5Bobject%20Object%5D&name=image.png&originHeight=110&originWidth=635&size=9775&status=done&style=none&width=635)<br />
<br />element.['属性名']<br /> var pwd = $('.reg-box [name=password]').val()  [ ]获取属性元素<br />

<a name="YmFyT"></a>
### 节点
网页中的所有内容都是节点（标签、属性、文本、注释等），在DOM 中，节点使用 node 来表示。HTML DOM 树中的所有节点均可通过 JavaScript 进行访问，所有 HTML 元素（节点）均可被修改，也可以创建或删除。<br />DOM树![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804699870-cc68ff5f-1409-4558-8e85-1b0fd9cdd328.png#align=left&display=inline&height=235&margin=%5Bobject%20Object%5D&name=image.png&originHeight=235&originWidth=488&size=19149&status=done&style=none&width=488)<br />
<br />一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804726310-58ecd106-d279-478e-afb1-ca16bd22a2aa.png#align=left&display=inline&height=157&margin=%5Bobject%20Object%5D&name=image.png&originHeight=157&originWidth=493&size=9751&status=done&style=none&width=493)
<a name="8c50c192"></a>
#### 节点层级
<a name="380a823d"></a>
#### 父级节点
node.parentNode<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612804782722-ed0f8e82-91b5-4915-983e-283d25d0ceef.png#align=left&display=inline&height=64&margin=%5Bobject%20Object%5D&name=image.png&originHeight=64&originWidth=547&size=6244&status=done&style=none&width=547)
<a name="fZeiF"></a>
#### 子节点
**所有子节点**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612805501047-d4cdd7f1-ffd6-4335-871c-96b7b5598cf3.png#align=left&display=inline&height=174&margin=%5Bobject%20Object%5D&name=image.png&originHeight=174&originWidth=642&size=15771&status=done&style=none&width=642)<br />**子元素节点**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612805525646-81b959b6-a315-430e-b961-d03a23f52d5d.png#align=left&display=inline&height=170&margin=%5Bobject%20Object%5D&name=image.png&originHeight=170&originWidth=721&size=27611&status=done&style=none&width=721)<br />**其他**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612805559504-e19766aa-1dc7-49f3-ae9a-b9c9ff19583d.png#align=left&display=inline&height=579&margin=%5Bobject%20Object%5D&name=image.png&originHeight=579&originWidth=724&size=35012&status=done&style=none&width=724)实际开发中，firstChild 和 lastChild 包含其他节点，操作不方便，而 firstElementChild 和 lastElementChild 又有兼容性问题，那么我们如何获取第一个子元素节点或最后一个子元素节点呢？<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612805646958-f6a9fb17-edef-43a2-975b-f14e6bb7a4c0.png#align=left&display=inline&height=105&margin=%5Bobject%20Object%5D&name=image.png&originHeight=105&originWidth=725&size=23459&status=done&style=none&width=725)
<a name="V74lW"></a>
#### 兄弟节点
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612805927787-b49d42d8-4359-45ca-97c8-9acd33b551ca.png#align=left&display=inline&height=193&margin=%5Bobject%20Object%5D&name=image.png&originHeight=193&originWidth=652&size=13000&status=done&style=none&width=652)
<a name="sl1lA"></a>
####  创建节点
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806007253-d9630082-4aaf-4979-9a40-fcf4552f2cbc.png#align=left&display=inline&height=136&margin=%5Bobject%20Object%5D&name=image.png&originHeight=136&originWidth=704&size=11735&status=done&style=none&width=704)
<a name="IgJVB"></a>
#### 添加节点
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806038648-a68f2be6-0366-47c4-bcd5-6b235502d97d.png#align=left&display=inline&height=263&margin=%5Bobject%20Object%5D&name=image.png&originHeight=263&originWidth=714&size=48885&status=done&style=none&width=714)
<a name="3B3t9"></a>
#### 删除节点![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806526224-70c9fffd-fdc3-457d-a3d0-4f4f667a5db8.png#align=left&display=inline&height=56&margin=%5Bobject%20Object%5D&name=image.png&originHeight=56&originWidth=631&size=4327&status=done&style=none&width=631)
node.removeChild() 方法从 node节点中删除一个子节点，返回删除的节点。
<a name="r0QJT"></a>
#### 复制（克隆）节点
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806569180-97caaa2a-666c-4d7e-9a1d-82cdb367d99a.png#align=left&display=inline&height=212&margin=%5Bobject%20Object%5D&name=image.png&originHeight=212&originWidth=604&size=39013&status=done&style=none&width=604)
<a name="d7Dyx"></a>
### 创建元素的三种方式
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806660464-aaa3f26a-4f37-4de9-a65f-09fcb3edbb11.png#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&name=image.png&originHeight=303&originWidth=599&size=57621&status=done&style=none&width=599)
<a name="RBsxJ"></a>
### DOM元素的增删改查
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806935887-daff6e10-d769-45da-b340-60fe0b3ad0ec.png#align=left&display=inline&height=892&margin=%5Bobject%20Object%5D&name=image.png&originHeight=892&originWidth=612&size=101515&status=done&style=none&width=612)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612806955689-a0041915-8683-4aa7-88b7-80e30583eb59.png#align=left&display=inline&height=180&margin=%5Bobject%20Object%5D&name=image.png&originHeight=180&originWidth=329&size=20137&status=done&style=none&width=329)
<a name="fUSVu"></a>
### 事件高级
<a name="mEkV6"></a>
#### 注册事件（3种方式）
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612807022415-389778d2-8164-4c09-b740-d17f8c15174f.png#align=left&display=inline&height=255&margin=%5Bobject%20Object%5D&name=image.png&originHeight=255&originWidth=656&size=56096&status=done&style=none&width=656)<br />第三种：attacheEvent( )，详见下文
<a name="iKBM6"></a>
#### 事件监听
**addEventListener()事件监听（IE9以后支持）**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612807764969-b811f8fa-36a6-421d-8ecf-44fe65bf717b.png#align=left&display=inline&height=267&margin=%5Bobject%20Object%5D&name=image.png&originHeight=267&originWidth=641&size=52984&status=done&style=none&width=641)<br />**attacheEvent()事件监听（IE678支持）**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612807838004-cb52ca27-9d9f-4985-8531-a4f208b8dcbe.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=image.png&originHeight=272&originWidth=635&size=48911&status=done&style=none&width=635)<br />例： btns.attachEvent('onclick', function() {<br />        alert(11);<br />    }
<a name="G8Sp7"></a>
#### 删除事件（解绑事件）
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612808192710-fa5b8404-eee2-40f3-81fc-aa32e5c9e8fa.png#align=left&display=inline&height=205&margin=%5Bobject%20Object%5D&name=image.png&originHeight=205&originWidth=537&size=27078&status=done&style=none&width=537)<br />eventTarget.removeEventListener( type, 函数名)
<a name="8lZDm"></a>
### DOM事件流
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612808266568-94b2a915-ef18-4549-b8f0-99bf7c728a8a.png#align=left&display=inline&height=77&margin=%5Bobject%20Object%5D&name=image.png&originHeight=77&originWidth=540&size=18154&status=done&style=none&width=540)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612808281522-c281c3da-1c53-4704-b72b-e0ab61ce3800.png#align=left&display=inline&height=280&margin=%5Bobject%20Object%5D&name=image.png&originHeight=280&originWidth=608&size=48434&status=done&style=none&width=608)<br />DOM 事件流会经历3个阶段：  <br />1. 捕获阶段<br />2. 当前目标阶段<br />3. 冒泡阶段  <br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612808323372-50acbcf7-d485-4615-ac25-36e4bcc39fbd.png#align=left&display=inline&height=280&margin=%5Bobject%20Object%5D&name=image.png&originHeight=280&originWidth=485&size=26646&status=done&style=none&width=485)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612808343708-d7b4b21a-6b40-449c-b007-1d9b6297fcc3.png#align=left&display=inline&height=269&margin=%5Bobject%20Object%5D&name=image.png&originHeight=269&originWidth=623&size=61427&status=done&style=none&width=623)
<a name="ccf3a56e"></a>
### 常用鼠标事件
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612809008268-2a83ac09-acc8-44b4-917d-d4a0d2c66d49.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=image.png&originHeight=272&originWidth=620&size=54596&status=done&style=none&width=620)
<a name="thfvW"></a>
### 事件对象
事件发生后，跟事件相关的一系列信息数据的集合都放到这个对象里面，这个对象就是事件对象。<br />事件对象本身的获取存在兼容问题：<br />1. 标准浏览器中是浏览器给方法传递的参数，只需要定义形参 e 就可以获取到。<br />2. 在 IE6~8 中，浏览器不会给方法传递参数，如果需要的话，需要到 window.event 中获取查找。
<a name="C34Ha"></a>
#### 事件对象的属性和方法
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612808498435-5c222d4a-8fe3-49a2-98e6-fae2a1d432cb.png#align=left&display=inline&height=244&margin=%5Bobject%20Object%5D&name=image.png&originHeight=244&originWidth=628&size=86207&status=done&style=none&width=628)
<a name="StkmG"></a>
#### e.target 和 this 的区别
-  this 是事件绑定的元素（绑定这个事件处理函数的元素） 。<br />-  e.target 是事件触发的元素。<br />常情况下terget 和 this是一致的，<br />但有一种情况不同，那就是在事件冒泡时（父子元素有相同事件，单击子元素，父元素的事件处理函数也会被触发执行），<br />	这时候this指向的是父元素，因为它是绑定事件的元素对象，<br />	而target指向的是子元素，因为他是触发事件的那个具体元素对象。<br />-  e.currentTarget：事件触发的当前事件（当前事件，可能是触发事件的源组件，可能是触发的事件组件（即触发事件源组件的子元素），此时点击子元还是父元素，都是当前事件，应用e.currentTarget）  即与this相同
<a name="9Rvp0"></a>
#### 阻止默认行为  e.preventDefault()
** e.preventDefault()**<br />低版本浏览器 ie678  returnValue  属性<br />            e.returnValue = false;<br /> 我们可以利用return false 也能阻止默认行为 没有兼容性问题<br />            return false;
<a name="MXlHo"></a>
#### 阻止事件冒泡  e.stopPropagation()
**e.stopPropagation()**<br />低版本浏览器 ie678  cancelBubble  属性<br />            e.cancelBubble = true;<br />e.cancelBubble = true; // 非标准 cancel 取消 bubble 泡泡
<a name="9DSwX"></a>
#### 事件委托
给父元素注册事件，利用事件冒泡，当子元素的事件触发，会冒泡到父元素，然后去控制相应的子元素。
<a name="w185R"></a>
#### 事件委托的作用

- 我们只操作了一次 DOM ，提高了程序的性能。<br />
- **动态新创建的子元素，也拥有事件（非常重要）**
<a name="4aOHA"></a>
#### 禁止选中文字和禁止右键菜单 contextmenu   /  selectstart
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612809136741-1050d8d5-20ca-41fc-bb18-7ddf9e6dcae4.png#align=left&display=inline&height=264&margin=%5Bobject%20Object%5D&name=image.png&originHeight=264&originWidth=613&size=39495&status=done&style=none&width=613)
<a name="LPaRh"></a>
#### 鼠标事件对象
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612809172414-63587f0b-6793-4775-a8d1-1acb63e5b596.png#align=left&display=inline&height=272&margin=%5Bobject%20Object%5D&name=image.png&originHeight=272&originWidth=619&size=82589&status=done&style=none&width=619)
<a name="xGuby"></a>
### 键盘事件
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612857960478-0d2e7928-ef92-47f3-8f75-caa015daf914.png#align=left&display=inline&height=282&margin=%5Bobject%20Object%5D&name=image.png&originHeight=282&originWidth=648&size=56563&status=done&style=none&width=648)
<a name="LUgLB"></a>
#### 键盘事件对象 keyCode
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612858124318-ffd6e69e-f43b-43a9-a92d-4065648ee616.png#align=left&display=inline&height=197&margin=%5Bobject%20Object%5D&name=image.png&originHeight=197&originWidth=635&size=37111&status=done&style=none&width=635)
<a name="InnRq"></a>
## BOM
BOM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。<br />BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612858190676-33735ff3-87ca-410a-ba51-b9de4b3ad8cd.png#align=left&display=inline&height=153&margin=%5Bobject%20Object%5D&name=image.png&originHeight=153&originWidth=641&size=37535&status=done&style=none&width=641)
<a name="1V7aF"></a>
### BOM的构成
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612858251462-a228109e-ae2a-4f85-82ea-51a363c45de4.png#align=left&display=inline&height=203&margin=%5Bobject%20Object%5D&name=image.png&originHeight=203&originWidth=625&size=37119&status=done&style=none&width=625)
<a name="KJVwO"></a>
### 顶级对象window 
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612858909660-fe76778d-3d41-4131-b775-ff721d754623.png#align=left&display=inline&height=160&margin=%5Bobject%20Object%5D&name=image.png&originHeight=160&originWidth=624&size=43383&status=done&style=none&width=624)
<a name="koPZP"></a>
### window对象的常见事件
<a name="lHjPd"></a>
#### 页面（窗口）加载事件（2种）load
第一种:onload<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612858953469-4807a85a-e0ce-48dc-92b6-8f0e5b672f5b.png#align=left&display=inline&height=114&margin=%5Bobject%20Object%5D&name=image.png&originHeight=114&originWidth=621&size=12720&status=done&style=none&width=621)window.onload 是窗口 (页面）加载事件，**当文档内容完全加载完成**会触发该事件(包括图像、脚本文件、CSS 文件等), 就调用的处理函数。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612858991577-6b0d70fd-af05-4ec3-b460-06a035ff2ac0.png#align=left&display=inline&height=147&margin=%5Bobject%20Object%5D&name=image.png&originHeight=147&originWidth=629&size=37694&status=done&style=none&width=629)<br />第二种：DOMContentLoaded<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859037777-6863be34-50f3-452c-b2af-c41647f5de1d.png#align=left&display=inline&height=64&margin=%5Bobject%20Object%5D&name=image.png&originHeight=64&originWidth=617&size=8760&status=done&style=none&width=617)<br />DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等。<br />	IE9以上才支持！！！<br />	如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。
<a name="VsPjV"></a>
#### 调整窗口大小事件 onresize
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859075762-260c427a-065e-4b5f-9af9-a90ddbb3a2ef.png#align=left&display=inline&height=83&margin=%5Bobject%20Object%5D&name=image.png&originHeight=83&originWidth=607&size=11406&status=done&style=none&width=607)<br />window.onresize 是调整窗口大小加载事件,  当触发时就调用的处理函数。<br />注意：

1. 只要窗口大小发生像素变化，就会触发这个事件。<br />
1. 我们经常利用这个事件完成响应式布局。 window.innerWidth 当前屏幕的宽度<br />
<a name="ajzmf"></a>
#### 定时器 setTimeout() setInterval()
window 对象给我们提供了 2 个非常好用的方法-定时器。

- setTimeout() <br />
- setInterval()  
<a name="W3JRJ"></a>
#### setTimeout() 闹钟定时器
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859217579-8846211d-30e9-4e77-a7a1-beeb0f3e97cb.png#align=left&display=inline&height=98&margin=%5Bobject%20Object%5D&name=image.png&originHeight=98&originWidth=633&size=16223&status=done&style=none&width=633)
<a name="1d9tA"></a>
#### setInterval() 闹钟定时器
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859429620-94fd8eea-f661-4f33-9f56-4154f0f5784f.png#align=left&display=inline&height=94&margin=%5Bobject%20Object%5D&name=image.png&originHeight=94&originWidth=606&size=18534&status=done&style=none&width=606)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859249041-c0751364-6a70-435d-9dce-4c6e55bbecb4.png#align=left&display=inline&height=178&margin=%5Bobject%20Object%5D&name=image.png&originHeight=178&originWidth=625&size=39647&status=done&style=none&width=625)<br />var timer1 = setTimeout(callback, 3000);
<a name="GsEuR"></a>
#### 停止定时器
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859392322-7b2720b9-cdd4-444e-a0fc-66a8f1c1ad03.png#align=left&display=inline&height=41&margin=%5Bobject%20Object%5D&name=image.png&originHeight=41&originWidth=616&size=4784&status=done&style=none&width=616)![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612859482946-f4352e01-b9a8-4546-9f89-dcf866ed4105.png#align=left&display=inline&height=48&margin=%5Bobject%20Object%5D&name=image.png&originHeight=48&originWidth=625&size=5056&status=done&style=none&width=625)<br />**定时器的this指向window,在定时器内部使用的变量要在定时器内部声明或者挂载到window身上**
<a name="dacYP"></a>
###  location对象
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612860219645-ac07cebf-fa62-4f8a-b154-9f1a0788c6a0.png#align=left&display=inline&height=57&margin=%5Bobject%20Object%5D&name=image.png&originHeight=57&originWidth=620&size=20883&status=done&style=none&width=620)<br />
<a name="cRlaw"></a>
#### URL
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612861300638-92f6277c-f210-49f0-9229-af29a02f1f62.png#align=left&display=inline&height=364&margin=%5Bobject%20Object%5D&name=image.png&originHeight=364&originWidth=712&size=80557&status=done&style=none&width=712)
<a name="jXEp8"></a>
#### location 对象的属性
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612861318699-d6dc4532-008c-4cff-8a9e-3ca417b5daee.png#align=left&display=inline&height=289&margin=%5Bobject%20Object%5D&name=image.png&originHeight=289&originWidth=721&size=65196&status=done&style=none&width=721)
<a name="FjVY0"></a>
#### location对象的常见方法
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612861415033-80f7fad8-ec52-44af-ad8b-8e18bfa5f818.png#align=left&display=inline&height=141&margin=%5Bobject%20Object%5D&name=image.png&originHeight=141&originWidth=722&size=53808&status=done&style=none&width=722)
<a name="nN58i"></a>
#### navigator对象
navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。<br />下面前端代码可以判断用户那个终端打开页面，实现跳转
```javascript
<script>
 if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
            window.location.href = "手机端网址";     //手机
        } else {
            window.location.href = "电脑端网址";     //电脑
        }
</script>
```
<a name="fKzEH"></a>
#### history对象
window对象给我们提供了一个 history对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的URL。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612861495861-56310780-9d4f-4cbc-be86-514d25c5f575.png#align=left&display=inline&height=150&margin=%5Bobject%20Object%5D&name=image.png&originHeight=150&originWidth=735&size=32459&status=done&style=none&width=735)<br />history对象一般在实际开发中比较少用，但是会在一些 OA 办公系统中见到。
<a name="rH0rp"></a>
## JS执行机制
<a name="lhZTf"></a>
###  JS 是单线程
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612861672441-80c520dd-a5a8-4d4b-b4d2-b3c8bc34c8da.png#align=left&display=inline&height=90&margin=%5Bobject%20Object%5D&name=image.png&originHeight=90&originWidth=729&size=15436&status=done&style=none&width=729)
<a name="1O2A7"></a>
#### 同步任务和异步任务
单线程导致的问题就是后面的任务等待前面任务完成，如果前面任务很耗时（比如读取网络数据），后面任务不得不一直等待！！<br />	为了解决这个问题，利用多核 CPU 的计算能力，HTML5 提出 Web Worker 标准，允许 JavaScript 脚本创建多个线程，但是子线程完全受主线程控制。于是，JS 中出现了**同步任务**和**异步任务**。
<a name="IheOw"></a>
#### 同步
	前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。比如做饭的同步做法：我们要烧水煮饭，等水开了（10分钟之后），再去切菜，炒菜。
<a name="d9eUr"></a>
#### 异步
	你在做一件事情时，因为这件事情会花费很长时间，在做这件事的同时，你还可以去处理其他事情。比如做饭的异步做法，我们在烧水的同时，利用这10分钟，去切菜，炒菜。<br />JS中所有任务可以分成两种，一种是同步任务（synchronous），另一种是异步任务（asynchronous）。<br />
<br />同步任务指的是：<br />	在主线程上排队执行的任务，只有前一个任务执行完毕，才能执行后一个任务；<br />异步任务指的是：<br />	不进入主线程、而进入”任务队列”的任务，当主线程中的任务运行完了，才会从”任务队列”取出异步任务放入主线程执行。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612862620520-9481b5de-1b1c-4c4e-9427-6fcfb47bc427.png#align=left&display=inline&height=375&margin=%5Bobject%20Object%5D&name=image.png&originHeight=375&originWidth=499&size=22176&status=done&style=none&width=499)
<a name="myJDr"></a>
### JS执行机制（事件循环）
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612862894498-b08811ac-a3f6-4bd2-a50d-44234eee5b77.png#align=left&display=inline&height=840&margin=%5Bobject%20Object%5D&name=image.png&originHeight=840&originWidth=852&size=88326&status=done&style=none&width=852)
<a name="R99qH"></a>
## 元素偏移量 offset 系列
<a name="gDgyB"></a>
### offset 概述
offset 翻译过来就是偏移量， 我们使用 offset系列相关属性可以动态的得到该元素的位置（偏移）、大小等。

1. 获得元素距离带有定位父元素的位置<br />
1. 获得元素自身的大小（宽度高度）<br />
1. 注意：返回的数值都不带单位

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612932962522-de5f1473-54f2-4e2f-b427-429ffd0a66b2.png#align=left&display=inline&height=202&margin=%5Bobject%20Object%5D&name=image.png&originHeight=202&originWidth=689&size=80834&status=done&style=none&width=689)<br />
<a name="2DYOv"></a>
### offset 与 style 区别
<a name="yONLo"></a>
#### offset

- offset 可以得到任意样式表中的样式值<br />
- offset 系列获得的数值是没有单位的<br />
- offsetWidth 包含padding+border+width<br />
- offsetWidth 等属性是只读属性，只能获取不能赋值<br />
> 所以，我们想要获取元素大小位置，用offset更合适

<a name="41UR0"></a>
#### style

- style 只能得到行内样式表中的样式值<br />
- style.width 获得的是带有单位的字符串<br />
- style.width 获得不包含padding和border 的值<br />
- style.width 是可读写属性，可以获取也可以赋值<br />
> 所以，我们想要给元素更改值，则需要用style改变**

<a name="LUEkw"></a>
## 元素可视区 client 系列
<a name="n2pMa"></a>
### client概述
client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。通过 client系列的相关属性可以动态的得到该元素的边框大小、元素大小等。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612933208722-dc98ae21-ebac-4f30-a6a8-7dcff6b2566b.png#align=left&display=inline&height=165&margin=%5Bobject%20Object%5D&name=image.png&originHeight=165&originWidth=683&size=56379&status=done&style=none&width=683)
<a name="7DgMO"></a>
## 元素滚动 scroll 系列
<a name="V9eq0"></a>
### scroll 概述
scroll 翻译过来就是滚动的，我们使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612933268850-8a563627-c36e-4ba0-9d83-944ef9d5c30b.png#align=left&display=inline&height=167&margin=%5Bobject%20Object%5D&name=image.png&originHeight=167&originWidth=689&size=59322&status=done&style=none&width=689)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612933334751-35c00901-e674-4ce2-9e1d-8acdfd8d54a9.png#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&name=image.png&originHeight=303&originWidth=304&size=45122&status=done&style=none&width=304)
<a name="70chP"></a>
### 页面被卷去的头部
如果浏览器的高（或宽）度不足以显示整个页面时，会自动出现滚动条。当滚动条向下滚动时，页面上面被隐藏掉的高度，我们就称为页面被卷去的头部。滚动条在滚动时会触发 onscroll事件。<br />页面被卷去的头部：可以通过window.pageYOffset 获得  如果是被卷去的左侧window.pageXOffset
<a name="DCRei"></a>
## 三大系列总结
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612933634591-eaed25e2-fee6-422f-85d3-1481a6c6abb3.png#align=left&display=inline&height=145&margin=%5Bobject%20Object%5D&name=image.png&originHeight=145&originWidth=721&size=55930&status=done&style=none&width=721)<br />他们主要用法：<br />1.offset系列 经常用于获得元素位置    offsetLeft  offsetTop<br />2.client经常用于获取元素大小  clientWidth clientHeight<br />3.scroll 经常用于获取滚动距离 scrollTop  scrollLeft  <br />4.注意页面滚动的距离通过 window.pageXOffset  获得
<a name="ts74y"></a>
## mouseenter 和mouseover的区别

- 当鼠标移动到元素上时就会触发mouseenter 事件<br />
- 类似 mouseover，它们两者之间的差别是<br />
- mouseover 鼠标经过自身盒子会触发，经过子盒子还会触发。mouseenter  只会经过自身盒子触发<br />
- 之所以这样，就是因为mouseenter不会冒泡<br />
- 跟mouseenter搭配鼠标离开 mouseleave  同样不会冒泡
<a name="JdilW"></a>
## 触屏事件
<a name="r8wQW"></a>
### 触屏事件概述 
移动端浏览器兼容性较好，我们不需要考虑以前 JS 的兼容性问题，可以放心的使用原生 JS 书写效果，但是移动端也有自己独特的地方。比如触屏事件 touch（也称触摸事件），Android和 IOS 都有。<br />touch 对象代表一个触摸点。触摸点可能是一根手指，也可能是一根触摸笔。触屏事件可响应用户手指（或触控笔）对屏幕或者触控板操作。<br />常见的触屏事件如下：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612933777745-58f2eb2a-16c6-4a41-9e44-4659ec3332c4.png#align=left&display=inline&height=146&margin=%5Bobject%20Object%5D&name=image.png&originHeight=146&originWidth=686&size=32764&status=done&style=none&width=686)
<a name="YXimN"></a>
### 触摸事件对象（TouchEvent）
TouchEvent 是一类描述手指在触摸平面（触摸屏、触摸板等）的状态变化的事件。这类事件用于描述一个或多个触点，使开发者可以检测触点的移动，触点的增加和减少，等等<br />touchstart、touchmove、touchend 三个事件都会各自有事件对象。<br />触摸事件对象重点我们看三个常见对象列表：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612943099599-7f14d024-5aa0-421d-a638-0390a7ea14fe.png#align=left&display=inline&height=144&margin=%5Bobject%20Object%5D&name=image.png&originHeight=144&originWidth=720&size=48275&status=done&style=none&width=720)
> **因为平时我们都是给元素注册触摸事件，所以重点记住 targetTocuhes**

<a name="GLO3O"></a>
### 案例：移动端拖动元素

1. touchstart、touchmove、touchend可以实现拖动元素<br />
1. 但是拖动元素需要当前手指的坐标值 我们可以使用  targetTouches[0] 里面的pageX 和 pageY <br />
1. 移动端拖动的原理：    手指移动中，计算出手指移动的距离。然后用盒子原来的位置 + 手指移动的距离<br />
1. 手指移动的距离：  手指滑动中的位置 减去  手指刚开始触摸的位置<br />拖动元素三步曲：<br />（1） 触摸元素 touchstart： 获取手指初始坐标，同时获得盒子原来的位置<br />（2） 移动手指 touchmove： 计算手指的滑动距离，并且移动盒子<br />（3） 离开手指 touchend:<br />`注意： 手指移动也会触发滚动屏幕所以这里要阻止默认的屏幕滚动 e.preventDefault()`
<a name="yrNHy"></a>
### classList属性
classList属性是HTML5新增的一个属性，返回元素的类名。但是ie10以上版本支持。<br />该属性用于在元素中添加，移除及切换 CSS 类。有以下方法<br />**添加类：**<br />element.classList.add（’类名’）；<br />focus.classList.add('current');<br />**移除类：**<br />element.classList.remove（’类名’）;<br />focus.classList.remove('current');<br />**切换类：**<br />element.classList.toggle（’类名’）;<br />focus.classList.toggle('current');<br />`注意:以上方法里面，所有类名都不带点`
<a name="QlGNd"></a>
### 本地存储
<a name="HhXPv"></a>
#### 本地存储特性
1、数据存储在用户浏览器中<br />2、设置、读取方便、甚至页面刷新不丢失数据<br />3、容量较大，sessionStorage约5M、localStorage约20M<br />4、只能存储字符串，可以将对象JSON.stringify() 编码后存储
<a name="window.sessionStorage"></a>
### window.sessionStorage
1、生命周期为关闭浏览器窗口<br />2、在同一个窗口(页面)下数据可以共享<br />3、以键值对的形式存储使用<br />存储数据：<br />sessionStorage.setItem(key, value)<br />获取数据：<br />sessionStorage.getItem(key)<br />删除数据：<br />sessionStorage.removeItem(key)<br />清空数据：(所有都清除掉)<br />sessionStorage.clear()
<a name="1.7.3.window.localStorage"></a>
### window.localStorage
1、声明周期永久生效，除非手动删除 否则关闭页面也会存在<br />2、可以多窗口（页面）共享（同一浏览器可以共享）

3. 以键值对的形式存储使用<br />

存储数据：<br />localStorage.setItem(key, value)<br />获取数据：<br />localStorage.getItem(key)<br />删除数据：<br />localStorage.removeItem(key)<br />清空数据：(所有都清除掉)<br />localStorage.clear()
<a name="tb0qN"></a>
### onpageshow 事件在用户浏览网页时触发。
onpageshow 事件类似于 [onload](https://www.runoob.com/jsref/event-onload.html) 事件，onload 事件在页面第一次加载时触发， onpageshow 事件在每次加载页面时触发，即 onload 事件在页面从浏览器缓存中读取时不触发。<br />
<br />

