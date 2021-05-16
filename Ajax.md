<a name="SRFRo"></a>
# 目标
- 能够知道和服务器相关的基本概念<br />
- 能够知道客户端和服务器通信的过程<br />
- 能够知道数据也是一种资源<br />
- 能够说出什么是Ajax以及应用场景<br />
- 能够使用jQuery中的Ajax函数请求数据<br />
- 能够知道接口和接口文档的概念
- 能够说出form表单的常用属性<br />
- 能够知道如何阻止表单的默认提交行为<br />
- 能够知道如何使用jQuery快速获取表单数据<br />
- 能够知道如何安装和使用模板引擎<br />
- 能够知道模板引擎的实现原理
- 能够知道如何使用XMLHttpRequest发起Ajax请求<br />
- 能够知道如何封装自己的Ajax函数<br />
- 能够使用XMLHttpRequest Level2中提供的新特性<br />
- 能够知道jQuery中如何实现文件上传与loading效果<br />
- 能够知道如何使用axios发起Ajax请求
- 能够知道什么是同源策略和跨域<br />
- 能够知道什么是JSONP<br />
- 能够说出JSONP的实现原理<br />
- 能够知道防抖和节流的概念
- 能够说出什么是HTTP协议<br />
- 能够知道HTTP请求消息的组成部分<br />
- 能够知道HTTP响应消息的组成部分<br />
- 能够说出常见的请求方法<br />
- 能够说出常见的响应状态码<br />
<a name="iYP7N"></a>
## 服务器<br />
上网过程中，负责 **存放和对外提供资源** 的电脑，叫做服务器
<a name="yt7My"></a>
## 客户端
在上网过程中，负责 **获取和消费资源** 的电脑，叫做客户端
<a name="jlKWX"></a>
## URL
URL（全称是UniformResourceLocator） 中文叫 统一资源定位符，用于标识互联网上每个资源的唯一存放位置。浏览器只有通过URL地址，才能正确定位资源的存放位置，从而成功访问到对应的资源<br />URL地址一般由三部分组成:

-  客户端与服务器之间的通信协议
-  存有该资源的服务器名称
-  资源在服务器上具体的存放位置

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612156976806-91f90fdb-4cbf-41f9-8b3c-34a04e723009.png#align=left&display=inline&height=110&margin=%5Bobject%20Object%5D&name=image.png&originHeight=118&originWidth=692&size=60063&status=done&style=none&width=645)
<a name="XrsRN"></a>
# 客户端与服务器通讯过程
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612157007016-54e6368b-5f35-4a3b-8517-a8fa72f4f9c9.png#align=left&display=inline&height=230&margin=%5Bobject%20Object%5D&name=image.png&originHeight=230&originWidth=750&size=64668&status=done&style=none&width=750)<br />注意:

-  客户端与服务器之间的通讯过程，分为： 请求-处理-响应三个步骤
- 网页中每一个资源，都是通过 **请求-处理-响应 **的方式从服务器获取回来的
<a name="I18G1"></a>
### 基于浏览器工具分析通讯过程
- 打开Chorme浏览器打开 ,Chrome 的开发者工具<br />- 切换到 Network 面板<br />- 选中Doc页签<br />- 刷新页面，分析客户端与服务器的通讯过程
<a name="thJpH"></a>
## 网页中如何请求数据(XMLHttpRequest   简称：xhr)
数据，也是服务器对外提供的一种 资源，只要是资源，必然要通过 请求 - 处理 - 响应 的方式进行获取<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612157119172-4dc601af-96f1-49ba-9376-f0aefbaa3072.png#align=left&display=inline&height=120&margin=%5Bobject%20Object%5D&name=image.png&originHeight=145&originWidth=723&size=42437&status=done&style=none&width=596)<br />如果要在网页中请求服务器上的数据资源，需要用到 `XMLHttpRequest` 对象<br />XMLHttpRequest（简称 xhr）是浏览器提供的JS成员，通过它，可以请求服务器上的数据资源<br />最简单的用法 var xhrObj = new XMLHttpRequest()
<a name="YG9pG"></a>
## 资源的请求方式
客户端请求服务器时，请求的方式有很多种，最常见的两种请求方式分别是 get和 post请求

- get 请求，通常用于获取服务器资源（要资源）
- 例如：根据 URL 地址，从服务器获取 HTML文件、css文件、js文件、图片文件、数据资源等
-  post 请求，通常用于向服务器提交数据（送资源）

例如：登录时，向服务器提交登录信息、注册时向服务器提交注册信息、添加用户时向服务器提交用户信息等各种 数据提交操作
<a name="Ugq7w"></a>
## Ajax
Ajax的全称是 Asynchronous JavaScript And XML（异步JavaScript 和 xml）<br />通俗理解：在网页中利用 `XMLHttpRequest` 对象和服务器进行数据交互的方式，就是Ajax
<a name="3p6fw"></a>
# jQuery中的Ajax
<a name="cpLQi"></a>
### $.get() 函数
$.get( url, [data], [callback] )，data可为空，获取全部数据<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612157369437-0f953994-93a9-4c0d-a64d-e0fced2240dc.png#align=left&display=inline&height=148&margin=%5Bobject%20Object%5D&name=image.png&originHeight=181&originWidth=747&size=64361&status=done&style=none&width=610)
<a name="PIdIe"></a>
### $.post() 函数
$.post( url, [data], [callback] )<br />内容参考get（），data不可为空，要提交数据。
<a name="6BjVf"></a>
### $.ajax() 函数
相比于 `$.get()` 和 `$.post()` 函数，`jQuery` 中提供的 `$.ajax()` 函数，是一个功能比较综合的函数，它允许我们对 `Ajax` 请求进行更详细的配置。get的data可以为空不写，获取全部数据，post必须带数据<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612157728463-1d112549-f9d1-4697-bb73-42ce670a3162.png#align=left&display=inline&height=166&margin=%5Bobject%20Object%5D&name=image.png&originHeight=199&originWidth=744&size=51484&status=done&style=none&width=622)
<a name="54ea89b4"></a>
### 接口
使用 `Ajax` 请求数据时，被请求的 `URL` 地址，就叫做 数据接口（简称**接口**）。同时，每个接口必须有请求方式。<br />例：<br />[http://www.liulongbin.top:3006/api/getbooks](http://www.liulongbin.top:3006/api/getbooks) 获取图书列表的接口（get请求）<br />[http://www.liulongbin.top:3006/api/addbook](http://www.liulongbin.top:3006/api/addbook)  添加图书的接口（post请求）<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612177822596-37f300b2-6639-4466-884d-65ff9ae0eb3d.png#align=left&display=inline&height=445&margin=%5Bobject%20Object%5D&name=image.png&originHeight=539&originWidth=813&size=119661&status=done&style=none&width=671)
<a name="BHLcP"></a>
## 接口测试工具  PostMan
为了验证接口是否被正常被访问，我们常常需要使用接口测试工具，来对数据接口进行检测<br />好处：接口测试工具能让我们在 **不写任何代码** 的情况下，对接口进行 调用 和 测试
<a name="DE9eF"></a>
#### 使用`PostMan`测试GET接口
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612177960636-5e21a1d8-a494-4abf-8400-9f710b7ea5cb.png#align=left&display=inline&height=447&margin=%5Bobject%20Object%5D&name=image.png&originHeight=482&originWidth=781&size=73787&status=done&style=none&width=724)
<a name="J8gFN"></a>
#### 使用`PostMan`测试POST接口
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612177980855-3ccb4138-f394-4e6a-847e-3e7623ec7847.png#align=left&display=inline&height=442&margin=%5Bobject%20Object%5D&name=image.png&originHeight=478&originWidth=789&size=84467&status=done&style=none&width=729)
<a name="UUfwJ"></a>
### 接口文档
接口文档，顾名思义就是 **接口的说明文档**，**它是我们调用接口的依据**。好的接口文档包含了对 **接口URL**，**参数** 以及 **输出内容** 的说明，我们参照接口文档就能方便的知道接口的作用，以及接口如何进行调用
<a name="SbNlG"></a>
### 接口文档的组成部分
接口文档可以包含很多信息，也可以按需进行精简，不过，一个合格的接口文档，应该包含以下6项内容，从而为接口的调用提供依据：

- **接口名称：**用来标识各个接口的简单说明，如 **登录接口**，**获取图书列表接口**等<br />
- **接口URL：**接口的调用地址<br />
- **调用方式：**接口的调用方式，如 **GET** 或者 **POST**<br />
- **参数格式：**接口需要传递的参数，每个参数必须包含 **参数名称**、**参数类型**、**是否必选**、**参数说明** 这4项内容<br />
- **响应格式：**接口的返回值的详细描述，一般包含**数据名称**、**数据类型**、**说明**3项内容<br />
- **返回示例（可选）：**通过对象的形式，列举服务器返回数据的结构
<a name="moPOv"></a>
# Form表单的基本使用
表单在网页中主要负责 **数据采集功能**。HTML中<form>标签，就是用于采集用户输入的信息，并通过 <form>标签的提交操作，把采集的信息提交到服务器端进行处理.
<a name="ZDv4A"></a>
## 表单的组成部分 三部分
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612266264436-60fe240d-6705-4970-a204-ad7c80e82ad7.png#align=left&display=inline&height=187&margin=%5Bobject%20Object%5D&name=image.png&originHeight=241&originWidth=745&size=81109&status=done&style=none&width=578)

- 表单标签<br />
- 表单域：包含了文本框，密码框，隐藏域，都行文本框，复选框，单选框，下拉选择框和文件上传框等等<br />
- 表单按钮：通过设置`type`属性为`submit`来触发`form`表单的提交
<a name="3ad3f4ea"></a>
## <form> 标签的属性
<a name="action"></a>
### action
action 属性用来规定当提交表单时，后端提供的一个URL地址，这个URL地址专门负责接收表单提交过来的数据。当 <form>表单在未制定 action 属性值的清空下，action的默认值为当前页面的 URL 地址<br />**注意:** 当提交表单后，会立即跳转到 `action` 属性指定的 `URL` 地址
<a name="p2R0B"></a>
### target
target 属性用来规定 在何处打开 action URL<br />它的可选值有5个，默认情况下，target的值是 _self，表示在相同的框架中打开 action URL<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612267083057-a89ce43a-1969-49ae-8097-8163385aca96.png#align=left&display=inline&height=190&margin=%5Bobject%20Object%5D&name=image.png&originHeight=253&originWidth=805&size=83532&status=done&style=none&width=603)
<a name="yTYft"></a>
### method
method 属性用来规定 **以何种方式** 把表单数据提交到 action URL<br />它的可选值有两个，分别是 get 和 post<br />默认情况下，method的值为 get， 表示通过URL地址的形式，把表单数据提交到 action URL<br />**注意：**

- get 方式适合用来提交**少量的**，**简单的**数据<br />
- post 方式适合用来提交**大量的**，**复杂的**，或包含**文件上传**的数据<br />
<a name="4qe85"></a>
### enctype
`enctype`属性用来规定在 **发送表单数据之前如何对数据进行编码**<br />它的可选值有三个，默认情况下，enctype的值为 application/x-www-form-urlencoded，表示在发送前编码的所有字符<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612267148436-36da335e-5721-437a-86c0-b21c0fdcace1.png#align=left&display=inline&height=136&margin=%5Bobject%20Object%5D&name=image.png&originHeight=178&originWidth=800&size=84346&status=done&style=none&width=609)
<a name="C0cWu"></a>
## 表单的同步提交及缺点
<a name="Vs9hM"></a>
### 什么是表单的同步提交
通过点击 submit 按钮，触发表单提交的操作，从而使页面跳转到 `action URL` 的行为，叫做表单的同步提交
<a name="pYqO1"></a>
### 表单同步提交的缺点

- <form> 表单同步提交后，整个页面会发生跳转，**跳转到 action URL 所指向的地址**，用户体验很差<br />
- <form> 表单同步提交后，页面之前的状态和数据会丢失<br />

**如何解决呢？**<br />**表单只复杂采集数据，Ajax负责将数据提交到服务器**
<a name="xJEDT"></a>
# 通过Ajax提交表单数据
<a name="AFXgo"></a>
## 阻止表单的默认提交行为  preventDefault( )
当监听到表单的提交事件以后，可以调用此函数阻止表单的提交和页面的跳转<br />event.preventDefault() 函数
<a name="LKrvJ"></a>
## jQuery快速获取表单数据  serialize( )
$ ( selector ).serialize( )<br />//例： username = 用户名的值 & password = 密码的值<br />**注意：**在使用 serialize() 函数快速获取表单数据时，**必须为每个表单元素添加 name 属性**<br />name = 'username'   这种
<a name="9YFkI"></a>
### 表单数据提交完成后，需要重置表单内的内容
**$("#form")[0].reset( )**
<a name="FGNVH"></a>
## 模板引擎
之前在渲染UI结构时候，**拼接字符串是比较麻烦的，而且很容易出现问题**<br />**模板引擎**，它可以根据程序员指定的 **模板结构** 和 **数据**，自动生成一个完整的HTML页面<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612267995286-1806a6dd-df3d-4987-8a62-697b9917bd44.png#align=left&display=inline&height=129&margin=%5Bobject%20Object%5D&name=image.png&originHeight=176&originWidth=820&size=23186&status=done&style=none&width=602)

- 减少了字符串的拼接操作<br />
- 使代码结构更清晰<br />
- 使代码更易于阅读与维护
<a name="kqf5d"></a>
## 模板引擎art-template
art-template 是一个简约，超快的模板引擎，中文官首页：[http://aui.github.io/art-template/zh-cn/index.html](http://aui.github.io/art-template/zh-cn/index.html)
<a name="Iybhi"></a>
### 使用步骤
<a name="jGU23"></a>
#### 一、导入`art-template`
<script src="./lib/template-web.js"></script>
<a name="OLdS6"></a>
#### 二、定义数据
例  :    let data = { name: 'zs', age: 20}
<a name="E7J1D"></a>
#### 三、定义模板

- 模板的 HTML 结构，必须定义到 script 标签中，注意：需要把type属性改成  text/html<br />
- 给 模板 添加一个 id<br />
- 模板里面如果需要使用到传入的数据，利用 {{}} 来实现，例如：{{name}}，那么就会去找 我们调用 template( ) 函数 第二个参数里面对应的`name`属性的值
<a name="Go3Xh"></a>
#### 四、调用`template` 函数
函数的返回值就是拼接好的模板字符串   template('模板id'，需要渲染的数据对象)<br />var htmlStr = template('tpl-user', data)
<a name="lvTCO"></a>
#### 五、渲染HTML结构
最后我们需要把template返回的模板字符串设置到页面容器中<br />$ ( '#container' ) . html ( htmlStr )
<a name="9Q9VJ"></a>
### 标准语法：双花括号 {{ }}
art-template 提供了 {{}} 这种语法格式，在 {{ }} 内可以进行 **变量输出** 或 **循环数组** 等操作，这种 {{ }} 语法在 art-template 中被称为标准语法<br />在 {{ }} 语法中，可以进行 **变量** 的输出，**对象属性**的输出，**三元表达式**输出，**逻辑或**输出，**加减乘除等表达式**输出
<a name="77oVd"></a>
#### 原文输出
{{@ value }}<br />如果输出的 value 值中，包含了 HTML 标签结构，则需要使用**原文输出**语法，才能保证HTML标签被正常渲染
<a name="n2pcT"></a>
#### 条件输出
如果要实现条件输出，则可以在 {{}} 中使用 if...else if.../if 的方式，进行按需输出<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612269140444-cb6d3415-b06e-487a-b608-f28009e51801.png#align=left&display=inline&height=120&margin=%5Bobject%20Object%5D&name=image.png&originHeight=120&originWidth=807&size=39366&status=done&style=none&width=807)
```javascript
{{if flag === 0}}
flag的值是0
{{else if flag === 1}}
flag的值是1
{{/if}}
```
<a name="yu8fG"></a>
#### 循环输出
如果要实现循环输出，则可以在{{}} 内，通过 each 语法循环数组，当前循环的索引使用 `$index` 进行访问，当前循环项使用 `$value` 进行访问<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612269170542-9852b080-2763-45dd-93b3-da723495ae61.png#align=left&display=inline&height=83&margin=%5Bobject%20Object%5D&name=image.png&originHeight=116&originWidth=832&size=18486&status=done&style=none&width=598)
```javascript
{{each hobby}}
<li>索引是:{{$index}}，循环项是:{{$value}}</li>
{{/each}}
```
<a name="dqe6B"></a>
#### 过滤器
本质就是一个function 函数<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612269222412-de926422-0f81-41f7-b26d-ded7874a39f3.png#align=left&display=inline&height=200&margin=%5Bobject%20Object%5D&name=image.png&originHeight=200&originWidth=802&size=43993&status=done&style=none&width=802)
<a name="3LuFX"></a>
## 模板引擎的实现原理
**正则与字符串操作**
<a name="aed5480a"></a>
### exec函数
exec() 函数用于 **检索字符串** 中的正则表达式的匹配<br />如果字符串中又匹配的值，**则返回该匹配值**，否则返回 **null**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612418386999-af1cfea5-95be-4c24-9ae3-0478a910040e.png#align=left&display=inline&height=139&margin=%5Bobject%20Object%5D&name=image.png&originHeight=139&originWidth=720&size=38068&status=done&style=none&width=720)**
<a name="a3sJ8"></a>
### 分组（）
正则表达式中 （） 包起来的内容表示一个分组，可以通过分组来 **提取自己想要的内容**，示例代码如下<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612418446860-b96cb23c-efee-4e31-9dee-c20a8bb46279.png#align=left&display=inline&height=182&margin=%5Bobject%20Object%5D&name=image.png&originHeight=182&originWidth=712&size=51695&status=done&style=none&width=712)<br />返回的数组第一项是{{name}}，第二项是name   如果没有（），则只有第一项会返回哦~
<a name="nOXKJ"></a>
### 字符串的 replace 函数
详见JS高级，replace详解<br />只能匹配一次
<a name="em7DP"></a>
### 实现简易的模板引擎
一、定义模板结构<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612418941971-2c58873d-e9a3-4700-a074-e34d436153d0.png#align=left&display=inline&height=174&margin=%5Bobject%20Object%5D&name=image.png&originHeight=174&originWidth=689&size=41571&status=done&style=none&width=689)<br />二、预调用模板引擎<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612418952048-5ed381d8-97e2-4d81-b81e-57a1b8a86d44.png#align=left&display=inline&height=242&margin=%5Bobject%20Object%5D&name=image.png&originHeight=242&originWidth=686&size=51741&status=done&style=none&width=686)<br />三、封装 template 函数<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612418965614-7d63cf61-510b-4cc9-9580-5df9776ab44d.png#align=left&display=inline&height=274&margin=%5Bobject%20Object%5D&name=image.png&originHeight=274&originWidth=684&size=59172&status=done&style=none&width=684)<br />第一步：获取页面模板元素<br />第二步：搭建正则表达式<br />第三步：声明一个变量，用while做正则替换循环<br />第四步：return替换好的超大字符串字符串<br />四、导入并使用自定义的模板引擎<br /><script src = "template.js"></script>
<a name="d1867635"></a>
## XMLHttpRequest的基本使用
概念 （原生js中操作方法）<br />XMLHttpRequest（简称 xhr）是浏览器提供的 Javascript 对象，通过它，可以请求**服务器上的数据资源**。之<br />前所学的 jQuery 中的 Ajax 函数，就是基于 xhr 对象封装出来的
<a name="TqRsz"></a>
### 使用`xhr`发起GET请求
<a name="Dz3W9"></a>
#### 步骤

- 创建 xhr 对象<br />
- 调用 xhr.open() 函数<br />
- 调用 xhr.send() 函数<br />
- 监听 xhr.onreadystatechange 事件
```javascript
// 1. 创建 XHR 对象
var xhr = new XMLHttpRequest()
// 2. 调用 open 函数
xhr.open('GET', 'http://www.liulongbin.top:3006/api/getbooks')
// 3. 调用 send 函数
xhr.send()
// 4. 监听 onreadystatechange 事件,固定写法
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 200) {
     // 获取服务器响应的数据，也可以获取别的数据
     console.log(xhr.responseText)
   }
}
```
<a name="tk7PG"></a>
#### 使用`xhr`发起带参数的GET请求
使用 xhr 对象发起带参数的 GET 请求时，只需在调用 xhr.open 期间，为 URL 地址指定参数即可：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612420305402-b1a93bed-bef0-48f4-921d-34a73eef583b.png#align=left&display=inline&height=39&margin=%5Bobject%20Object%5D&name=image.png&originHeight=39&originWidth=680&size=12589&status=done&style=none&width=680)
<a name="1BhxT"></a>
#### 查询字符串
**定义：**查询字符串（URL 参数）是指在 URL 的末尾加上用于向服务器发送信息的字符串（变量）。<br />格式：将英文的 ? 放在URL 的末尾，然后再加上 参数＝值 ，想加上多个参数的话，使用 & 符号进行分隔。以<br />这个形式，可以将想要发送给服务器的数据添加到 `URL` 中。
<a name="pLHQT"></a>
#### GET请求携带参数的本质
无论使用 $.ajax()，还是使用 $.get()，又或者直接使用 xhr 对象发起 GET 请求，当需要携带参数的时候，本质上，都是直接将参数以查询字符串的形式，追加到 URL 地址的后面，发送到服务器的。
<a name="NF6X1"></a>
#### 了解`xhr`对象的`readyState`属性
XMLHttpRequest 对象的 readyState 属性，用来表示当前 Ajax 请求所处的状态。每个 Ajax 请求必然处于以下状态中的一个：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612420238598-9963a891-ab45-4b74-8f1f-1456a8d65b04.png#align=left&display=inline&height=271&margin=%5Bobject%20Object%5D&name=image.png&originHeight=271&originWidth=792&size=81575&status=done&style=none&width=792)
<a name="cWmQT"></a>
#### URL编码
`URL` 地址中，只允许出现英文相关的字母、标点符号、数字，因此，在 `URL` 地址中不允许出现中文字符。<br />如果 URL 中需要包含中文这样的字符，则必须对中文字符进行**编码**（转义）。<br />**URL编码的原则**：使用安全的字符（没有特殊用途或者特殊意义的可打印字符）去表示那些不安全的字符。<br />URL编码原则的通俗理解：使用英文字符去表示非英文字符
<a name="Gp0q9"></a>
#### 对URL进行编码与解码
浏览器提供了 URL 编码与解码的 API，分别是：

- encodeURI() 编码的函数<br />
- decodeURI() 解码的函数<br />
<a name="YGBKs"></a>
### 使用`xhr`发起`POST`请求
**步骤**

- 创建 xhr 对象<br />
- 调用 xhr.open() 函数<br />
- **设置 Content-Type 属性**（固定写法）<br />
- 调用 xhr.send() 函数，**同时指定要发送的数据**<br />
- 监听 xhr.onreadystatechange 事件<br />
```javascript
// 1. 创建 xhr 对象
var xhr = new XMLHttpRequest()
// 2. 调用 open 函数
xhr.open('POST', 'http://www.liulongbin.top:3006/api/addbook')
// 3. 设置 Content-Type 属性（固定写法）
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded')
// 4. 调用 send 函数
xhr.send('bookname=水浒传&author=施耐庵&publisher=上海图书出版社')
// 5. 监听事件
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 200) {
    console.log(xhr.responseText)
  }
}
```
<a name="p2B0p"></a>
### `XMLHttpRequest Level2`的新功能

- 可以设置 HTTP 请求的时限<br />
- 可以使用 FormData 对象管理表单数据<br />
- 可以上传文件<br />
- 可以获得数据传输的进度信息
<a name="9Aat0"></a>
#### 设置`HTTP`请求时限
有时，Ajax 操作很耗时，而且无法预知要花多少时间。如果网速很慢，用户可能要等很久。新版本的 XMLHttpRequest 对象，增加了 timeout 属性，可以设置 HTTP 请求的时限：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612445026852-1e508be6-460f-4d5a-9029-43705375cb61.png#align=left&display=inline&height=39&margin=%5Bobject%20Object%5D&name=image.png&originHeight=39&originWidth=251&size=3885&status=done&style=none&width=251)<br />上面的语句，将最长等待时间设为 3000 毫秒。过了这个时限，就自动停止HTTP请求。与之配套的还有一个<br />timeout 事件，用来指定回调函数：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612445046034-2f222e3a-549a-4c8d-ad84-97ab4d1a6fad.png#align=left&display=inline&height=85&margin=%5Bobject%20Object%5D&name=image.png&originHeight=85&originWidth=344&size=11599&status=done&style=none&width=344)
<a name="fVgjj"></a>
#### `FormData`对象管理表单数据
Ajax 操作往往用来提交表单数据。为了方便表单处理，HTML5 新增了一个 FormData 对象，可以模拟表单操作：
```javascript
 // 1. 新建 FormData 对象
 var fd = new FormData()
 // 2. 为 FormData 添加表单项
 fd.append('uname', 'zs')
 fd.append('upwd', '123456')
 // 3. 创建 XHR 对象
 var xhr = new XMLHttpRequest()
 // 4. 指定请求类型与URL地址
 xhr.open('POST', 'http://www.liulongbin.top:3006/api/formdata')
 // 5. 直接提交 FormData 对象，这与提交网页表单的效果，完全一样
 xhr.send(fd)
```
FormData对象也可以用来获取网页表单的值，示例代码如下
```javascript
// 获取表单元素
var form = document.querySelector('#form1')
// 监听表单元素的 submit 事件
form.addEventListener('submit', function(e) {
 e.preventDefault()
 // 根据 form 表单创建 FormData 对象，会自动将表单数据填充到 FormData 对象中
 var fd = new FormData(form)
 var xhr = new XMLHttpRequest()
 xhr.open('POST', 'http://www.liulongbin.top:3006/api/formdata')
 xhr.send(fd)
 xhr.onreadystatechange = function() {}
})
```
<a name="DO792"></a>
#### 上传文件
新版 XMLHttpRequest 对象，不仅可以发送文本信息，还可以上传文件。<br />**实现步骤：**<br />① 定义 UI 结构<br />② 验证是否选择了文件<br />③ 向 FormData 中追加文件<br />④ 使用 xhr 发起上传文件的请求<br />⑤ 监听 onreadystatechange 事件
<a name="84QY6"></a>
#### 显示文件上传进度
通过监听 xhr.upload.onprogress 事件，来获取到文件的上传进度
```javascript
// 创建 XHR 对象
var xhr = new XMLHttpRequest()
// 监听 xhr.upload 的 onprogress 事件
xhr.upload.onprogress = function(e) {
     // e.lengthComputable 是一个布尔值，表示当前上传的资源是否具有可计算的长度
     if (e.lengthComputable) {
         // e.loaded 已传输的字节
         // e.total 需传输的总字节
         var percentComplete = Math.ceil((e.loaded / e.total) * 100)
     }
 }
```
<a name="kz27n"></a>
## 数据交换格式
数据交换格式，就是**服务器端**与**客户端**之间进行**数据传输与交换的格式**<br />前端领域，经常提及的两种数据交换格式分别是 `XML` 和 `JSON`。其中 `XML` 用的非常少，所以，我们重点要学<br />习的数据交换格式就是 JSON
<a name="80cwx"></a>
### JSON
**概念：**JSON 的英文全称是 JavaScript Object Notation，即“**JavaScript 对象表示法**”。简单来讲，<br />**JSON **就是 Javascript 对象和数组的字符串表示法，它使用文本表示一个 JS 对象或数组的信息，因此，<br />**JSON 的本质是字符串。**<br />**作用**：JSON 是一种轻量级的文本数据交换格式，在作用上类似于 XML，专门用于存储和传输数据，但<br />是 JSON 比 XML 更小、更快、更易解析。<br />**现状**：JSON 是在 2001 年开始被推广和使用的数据格式，到现今为止，JSON 已经成为了主流的数据交换格式
<a name="e75c3a32"></a>
### `JSON`的两种结构`<br />`
<a name="uXpOt"></a>
#### **对象结构**
对象结构在 JSON 中表示为 { } 括起来的内容。数据结构为 { key: value, key: value, … } 的键值对结构。其中，key 必须是使用英文的双引号包裹的字符串，value 的数据类型可以是数字、字符串(也要双引号)、布尔值、null、数组、对象6种类型。
<a name="6xzJd"></a>
#### **数组结构**
数组结构在 JSON 中表示为 [ ] 括起来的内容。数据结构为 [ "java", "javascript", 30, true … ] 。<br />数组中数据的类型可以是**数字、字符串、布尔值、null、数组、对象**6种类型。
<a name="EEaER"></a>
#### `JSON`语法注意事项
① 属性名必须使用双引号包裹<br />② 字符串类型的值必须使用双引号包裹<br />③ JSON 中不允许使用单引号表示字符串<br />④ JSON 中不能写注释<br />⑤ JSON 的最外层必须是对象或数组格式<br />⑥ 不能使用 undefined 或函数作为 JSON 的值<br />**`JSON` 的作用：**在计算机与网络之间存储和传输数据。<br />**`JSON` 的本质：**用字符串来表示 Javascript 对象数据或数组数据
<a name="wngq3"></a>
#### JSON和JS对象的关系
JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。例如：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612444292072-077b6b62-01da-46af-83fe-12de83fe239b.png#align=left&display=inline&height=158&margin=%5Bobject%20Object%5D&name=image.png&originHeight=158&originWidth=578&size=26940&status=done&style=none&width=578)
<a name="ywH76"></a>
#### JSON和JS对象的互转
要实现从 JSON 字符串转换为 JS 对象，使用** JSON.parse( )** 方法：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612444467505-a360ca33-de6d-46d9-82ec-3e57cddd581b.png#align=left&display=inline&height=58&margin=%5Bobject%20Object%5D&name=image.png&originHeight=58&originWidth=596&size=16547&status=done&style=none&width=596)<br />要实现从 JS 对象转换为 JSON 字符串，使用** JSON.stringify( ) **方法：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612444471896-c625915b-8bf8-43ba-b624-d00177f47023.png#align=left&display=inline&height=54&margin=%5Bobject%20Object%5D&name=image.png&originHeight=54&originWidth=606&size=17377&status=done&style=none&width=606)
<a name="RTZFq"></a>
#### 序列化和反序列化
把**数据对象** **转换为** **字符串**的过程，叫做**序列化**，例如：调用 JSON.stringify() 函数的操作，叫做 JSON 序列化。<br />把**字符串** **转换为** **数据对象**的过程，叫做**反序列化**，例如：调用 JSON.parse() 函数的操作，叫做 JSON 反序列化。
<a name="eX7se"></a>
## jQuery高级用法- jQuery实现文件上传
<a name="FLd0B"></a>
## **axios**
Axios 是专注于**网络数据请求**的库。<br />相比于原生的 XMLHttpRequest 对象，axios **简单易用**。<br />相比于 jQuery，axios 更加**轻量化**，只专注于网络数据请求。<br />只支持get.post请求，无法发起jsonp请求，可以配置cors

- 基于promise用于浏览器和node.js的http客户端<br />
- 支持浏览器和node.js<br />
- 支持promise<br />
- 能拦截请求和响应<br />
- 自动转换JSON数据<br />
- 能转换请求和响应数据<br />
<a name="nFUOf"></a>
### axios发起GET请求
axios.get('url', { params: { /*参数*/ } }).then(callback)
```javascript
// 请求的 URL 地址
var url = 'http://www.liulongbin.top:3006/api/get'
// 请求的参数对象
var paramsObj = { name: 'zs', age: 20 }
// 调用 axios.get() 发起 GET 请求
axios.get(url, { params: paramsObj }).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(res)
})
```
<a name="9zLdz"></a>
### `axios`发起`POST`请求
axios.post('url', { /*参数*/ }).then(callback)
```javascript
// 请求的 URL 地址
var url = 'http://www.liulongbin.top:3006/api/post'
// 要提交到服务器的数据
var dataObj = { location: '北京', address: '顺义' }
// 调用 axios.post() 发起 POST 请求
axios.post(url, dataObj).then(function(res) {
     // res.data 是服务器返回的数据
     var result = res.data
     console.log(result)
})
```
<a name="BjTC1"></a>
### 直接使用`axios`发起请求
axios 也提供了类似于 jQuery 中 $.ajax() 的函数，语法如下： 
```javascript
axios({
 method: '请求类型',
 url: '请求的URL地址',
 data: { /* POST数据 */ },
 params: { /* GET参数 */ }
}).then(callback)
```
将来在项目中为了组件化，在script标签下定义全局<br />Vue.prototype.$http = axios<br />在methods中定义<br />this.$http.get( url,...)<br />
<br />**axios.defaults.baseURL = "http://....."**<br />this.$http.get( "/api/get",.........)

axios请求返回的是一个封装好六个固定属性的promise对象<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615289738126-59062de9-9bf2-4ae9-a7c5-b9415b040430.png#align=left&display=inline&height=161&margin=%5Bobject%20Object%5D&name=image.png&originHeight=161&originWidth=323&size=12255&status=done&style=none&width=323)
<a name="r12Oo"></a>
#### axios 全局配置
```javascript
#  配置公共的请求头 
axios.defaults.baseURL = 'https://api.example.com';
#  配置 超时时间
axios.defaults.timeout = 2500;
#  配置公共的请求头
axios.defaults.headers.common['Authorization'] = AUTH_TOKEN;
# 配置公共的 post 的 Content-Type
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
```
<a name="KkJqQ"></a>
#### axios 拦截器

- 请求拦截器
   - 请求拦截器的作用是在请求发送前进行一些操作
      - 例如在每个请求体里加上token，统一做了处理如果以后要改也非常容易<br />
- 响应拦截器
   - 响应拦截器的作用是在接收到响应后进行一些操作
      - 例如在服务器返回登录状态失效，需要重新登录的时候，跳转到登录页<br />
```javascript
# 1. 请求拦截器 
	axios.interceptors.request.use(function(config) {
      console.log(config.url)
      # 1.1  任何请求都会经过这一步   在发送请求之前做些什么   
      config.headers.mytoken = 'nihao';
      # 1.2  这里一定要return   否则配置不成功  
      return config;
    }, function(err){
       #1.3 对请求错误做点什么    
      console.log(err)
    })
	#2. 响应拦截器 
    axios.interceptors.response.use(function(res) {
      #2.1  在接收响应做些什么  
      var data = res.data;
      return data;
    }, function(err){
      #2.2 对响应错误做点什么  
      console.log(err)
    })
```
<a name="cT7Ju"></a>
## 同源策略
<a name="7OMwr"></a>
### 什么是同源
如果两个页面的协议，域名和端口都相同，则两个页面具有**相同的源**。
<a name="VmMbs"></a>
### 什么是同源策略
**同源策略**（英文全称 Same origin policy）是**浏览器**提供的一个**安全功能**<br />**`MDN` 官方给定的概念**：同源策略限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这<br />是一个用于隔离潜在恶意文件的重要安全机制<br />通俗的理解：浏览器规定，A 网站的 JavaScript，不允许和非同源的网站 C 之间，进行资源的交互，例如：<br />① 无法读取非同源网页的 Cookie、LocalStorage 和 IndexedDB<br />② 无法接触非同源网页的 DOM<br />③ 无法向非同源地址发送 Ajax 请求
<a name="TDdBP"></a>
### 跨域
**同源**指的是两个 URL 的协议、域名、端口一致，反之，则是**跨域**<br />出现跨域的根本原因：**浏览器的同源策略**不允许非同源的 URL 之间进行资源的交互<br />网页：`[http://www.test.com/index.html](http://www.test.com/index.html)`<br />接口：`[http://www.api.com/userlist](http://www.api.com/userlist)`<br />**注意：**浏览器允许发起跨域请求，但是，跨域请求回来的数据，会被浏览器拦截，无法被页面获取到！
<a name="UbsoT"></a>
### 如何实现跨域数据请求
现如今，实现跨域数据请求，最主要的两种解决方案，分别是 JSONP 和 CORS。<br />**`JSONP`：**出现的早，兼容性好（兼容低版本IE）。是前端程序员为了解决跨域问题，被迫想出来的一种临时解决方案。**缺点**是只支持 GET 请求，不支持 POST 请求。<br />**`CORS`：**出现的较晚，它是 W3C 标准，属于跨域 Ajax 请求的根本解决方案。支持 GET 和 POST 请求。**缺点**是不兼容某些低版本的浏览器
<a name="TCZ4i"></a>
### `JSONP`
JSONP (JSON with Padding) 是 JSON 的一种“使用模式”，可用于解决主流浏览器的跨域数据访问的问题。<br />由于浏览器同源策略的限制，网页中无法通过 Ajax 请求非同源的接口数据。但是 <script> 标签不受浏览器同<br />源策略的影响，可以通过 src 属性，请求非同源的 js 脚本。<br />因此，JSONP 的实现原理，就是通过 <script> 标签的 src 属性，请求跨域的数据接口，并通过**函数调用**的形式，接收跨域接口响应回来的数据
```javascript
 <script>  //定义一个`success`回调函数
     function success(data) {
     console.log('获取到了data数据：')
     console.log(data)
     }
 </script>

//通过 `<script>` 标签，请求接口数据：
<script src="http://ajax.frontend.itheima.net:3006/api/jsonp?callback=success&name=zs&a

```
**缺点**<br />由于 JSONP 是通过 <script> 标签的 src 属性，来实现跨域数据获取的，所以，JSONP 只支持 GET 数据请求，不支持 POST 请求。<br />**注意：** **`JSONP` 和 Ajax 之间没有任何关系**，不能把 JSONP 请求数据的方式叫做 Ajax，因为 JSONP 没有用到XMLHttpRequest 这个对象
<a name="BEopA"></a>
## `jQuery`中的`JSONP`
jQuery 提供的 $.ajax() 函数，除了可以发起真正的 Ajax 数据请求之外，还能够发起 JSONP 数据请求，例如：
```javascript
$.ajax({
     url: 'http://ajax.frontend.itheima.net:3006/api/jsonp?name=zs&age=20',
     // 如果要使用 $.ajax() 发起 JSONP 请求，必须指定 datatype 为 jsonp
     dataType: 'jsonp',
     success: function(res) {
     console.log(res)
     }
})
```
默认情况下，使用 jQuery 发起 JSONP 请求，会自动携带一个 callback=jQueryxxx 的参数，jQueryxxx 是随机生成的一个回调函数名称
<a name="923589fe"></a>
### 自定义参数及回调函数名称
在使用 jQuery 发起 JSONP 请求时，如果想要自定义 JSONP 的**参数**以及**回调函数名称**，可以通过如下两个参数来指定：
```javascript
$.ajax({
     url: 'http://ajax.frontend.itheima.net:3006/api/jsonp?name=zs&age=20',
     dataType: 'jsonp',
     // 发送到服务端的参数名称，默认值为 callback
     jsonp: 'callback',
     // 自定义的回调函数名称，默认值为 jQueryxxx 格式
     jsonpCallback: 'abc',
     success: function(res) {
     console.log(res)
     }
})
```
<a name="y9Y5x"></a>
### 实现原理
jQuery 中的 JSONP，也是通过 <script> 标签的 src 属性实现跨域数据访问的，只不过，jQuery 采用的是**动态创建和移除标签**的方式，来发起 JSONP 数据请求。

- 在发起 JSONP 请求的时候，动态向 <header> 中 append 一个 <script> 标签；<br />
- 在 JSONP 请求成功以后，动态从 <header> 中移除刚才 append 进去的 <script> 标签；<br />
<a name="YjDaU"></a>
## 防抖
**防抖策略**（debounce）是当事件被触发后，延迟 `n` 秒后再执行回调，如果在这 n 秒内事件又被触发，则重新计时。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612625022119-ff16f15a-0d7d-4e47-9e9b-bc0818c11d3f.png#align=left&display=inline&height=246&margin=%5Bobject%20Object%5D&name=image.png&originHeight=246&originWidth=314&size=25495&status=done&style=none&width=314)<br />**好处：**能够保证用户在频繁触发某些事件的时候，不会频繁的执行回调，只会被执行一次<br />用户在输入框中连续输入一串字符时，可以通过防抖策略，只在输入完后，才执行查询的请求，这样可以有效减<br />少请求次数，节约请求资源；
<a name="tyZy7"></a>
## 节流
**节流策略**（`throttle`），顾名思义，可以减少一段时间内事件的触发频率。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612625077796-379d6672-7084-4380-969d-56fee2841ff5.png#align=left&display=inline&height=195&margin=%5Bobject%20Object%5D&name=image.png&originHeight=195&originWidth=236&size=25795&status=done&style=none&width=236)
<a name="NEKoJ"></a>
### 节流的应用场景
① 鼠标连续不断地触发某事件（如点击），只在单位时间内只触发一次；<br />② 懒加载时要监听计算滚动条的位置，但不必每次滑动都触发，可以降低计算的频率，而不必去浪费 CPU 资源；
<a name="xCmRv"></a>
#### 节流阀的概念
高铁卫生间是否被占用，由红绿灯控制，红灯表示被占用，绿灯表示可使用。<br />假设每个人上卫生间都需要花费5分钟，则五分钟之内，被占用的卫生间无法被其他人使用。<br />上一个人使用完毕后，需要将红灯**重置**为绿灯，表示下一个人可以使用卫生间。<br />下一个人在上卫生间之前，需要**先判断控制灯**是否为绿色，来知晓能否上卫生间。<br />节流阀为空，表示可以执行下次操作；不为空，表示不能执行下次操作。<br />当前操作执行完，必须将节流阀**重置**为空，表示可以执行下次操作了。<br />每次执行操作前，必须**先判断节流阀是否为空**。
<a name="845c05c6"></a>
## 总结防抖和节流的区别

- **防抖**：如果事件被频繁触发，防抖能保证只有最有一次触发生效！前面 N 多次的触发都会被忽略！<br />
- **节流**：如果事件被频繁触发，节流能够减少事件触发的频率，因此，节流是有选择性地执行一部分事件！<br />
<a name="aDgpu"></a>
## HTTP协议简介
通信，就是**信息的传递和交换**。<br />通信三要素：

- 通信的主体<br />
- 通信的内容<br />
- 通信的方式<br />
<a name="SEUTx"></a>
### **互联网中的通信**
**案例：**服务器把传智专修学院的简介通过响应的方式发送给客户端浏览器。<br />其中，<br />通信的**主体**是服务器和客户端浏览器；<br />通信的**内容**是传智专修学院的简介；<br />通信的**方式**是响应；
<a name="cfI4c"></a>
## 什么是通信协议
**通信协议**（Communication Protocol）是指通信的双方完成通信所必须遵守的规则和约定。<br />**通俗的理解：**通信双方采用约定好的格式来发送和接收消息，这种**事先约定好的通信格式，就叫做通信协议**。
<a name="xg4Io"></a>
### 互联网中的通信协议
客户端与服务器之间要实现网页内容的传输，则通信的双方必须遵守网页内容的传输协议。<br />网页内容又叫做**超文本**，因此网页内容的传输协议又叫做**超文本传输协议**（HyperText Transfer Protocol） ，<br />简称 **HTTP 协议**。<br />HTTP 协议采用了 **请求/响应** 的交互模型。
<a name="Wiczw"></a>
# HTTP请求消息
<a name="OAPyU"></a>
## 什么是HTTP请求消息
由于 HTTP 协议属于客户端浏览器和服务器之间的通信协议。因此，客户端发起的请求叫做 **HTTP 请求**，客户<br />端发送到服务器的消息，叫做 **HTTP 请求消息**。<br />**注意：**HTTP 请求消息又叫做 HTTP 请求报文
<a name="gsIJx"></a>
## HTTP请求消息的组成部分
HTTP 请求消息由请求行（request line）、请求头部（ header ） 、空行 和 请求体 4 个部分组成。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666378061-cb4eb080-c1c8-49d9-87d0-4530c0e50206.png#align=left&display=inline&height=279&margin=%5Bobject%20Object%5D&name=image.png&originHeight=279&originWidth=708&size=165082&status=done&style=none&width=708)
<a name="97mcq"></a>
#### 请求头部 – 常见的请求头字段
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666501588-3837907a-c2e8-48e8-9fbb-6d9c1312b146.png#align=left&display=inline&height=306&margin=%5Bobject%20Object%5D&name=image.png&originHeight=306&originWidth=699&size=101817&status=done&style=none&width=699)
<a name="97a2816c"></a>
#### 请求体
请求体中存放的，是要通过 POST 方式提交到服务器的数据。<br />**注意**：只有 POST 请求才**有请求体**，GET 请求**没有请求体**！
<a name="KQ9YF"></a>
## HTTP响应消息的组成部分
HTTP响应消息由**状态行**、**响应头部**、**空行** 和 **响应体** 4 个部分组成，如下图所示：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666603766-fcb359e1-040f-4230-acb2-68b40d6fe67e.png#align=left&display=inline&height=274&margin=%5Bobject%20Object%5D&name=image.png&originHeight=274&originWidth=689&size=147800&status=done&style=none&width=689)
<a name="bA8yC"></a>
### 响应体
响应体中存放的，是服务器响应给客户端的资源内容。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666642491-4056468a-bb40-42e3-bb0a-6a78ec4f3c63.png#align=left&display=inline&height=330&margin=%5Bobject%20Object%5D&name=image.png&originHeight=330&originWidth=698&size=100794&status=done&style=none&width=698)
<a name="43YQ4"></a>
## HTTP请求方法
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666669586-7f657b49-a319-451c-a180-49f4e77d9a91.png#align=left&display=inline&height=308&margin=%5Bobject%20Object%5D&name=image.png&originHeight=308&originWidth=696&size=156840&status=done&style=none&width=696)
<a name="323qZ"></a>
## HTTP响应状态码
HTTP 状态码由**三个十进制数字组成**，**第一个十进制数字定义了状态码的类型**，后两个数字**用来对状态码进行细分**。<br />HTTP 状态码共分为 5 种类型：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666739438-4775afac-48ab-4428-86ca-731caba10218.png#align=left&display=inline&height=205&margin=%5Bobject%20Object%5D&name=image.png&originHeight=205&originWidth=692&size=74237&status=done&style=none&width=692)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666773302-f2b3b342-d5a1-4080-bc10-6fcb96265497.png#align=left&display=inline&height=108&margin=%5Bobject%20Object%5D&name=image.png&originHeight=108&originWidth=696&size=40904&status=done&style=none&width=696)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666784968-3fa9aac1-6ecf-458b-bc0f-bbfcec741569.png#align=left&display=inline&height=182&margin=%5Bobject%20Object%5D&name=image.png&originHeight=182&originWidth=690&size=108799&status=done&style=none&width=690)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666796993-4acc0303-4a2e-4bd7-bff3-83b1563e311b.png#align=left&display=inline&height=235&margin=%5Bobject%20Object%5D&name=image.png&originHeight=235&originWidth=691&size=102121&status=done&style=none&width=691)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612666806406-9341d48b-7c9e-4812-8eb9-477991912d1c.png#align=left&display=inline&height=169&margin=%5Bobject%20Object%5D&name=image.png&originHeight=169&originWidth=693&size=80872&status=done&style=none&width=693)
<a name="GlTzi"></a>
## 1、前端向服务器发送请求有多少种方案
1.方案一：ajax 2.方案二：jsonp 3.方案三：fetch 4.方案四：axios
<a name="Q0lz8"></a>
## 2、**ajax是如何发送请求的**
基于 XMLHttpRequest 实例对象 调用 open send 等api 监听事件行为 处理交互过程
