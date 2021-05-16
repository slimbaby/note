<a name="fk7xw"></a>
### 1.  学习目标
◆  能够知道什么是 Node.js<br />◆  能够知道 Node.js 可以做什么<br />◆  能够说出 Node.js 中的 JavaScript 的组成部分<br />◆  能够使用 fs 模块读写操作文件<br />◆  能够使用 path 模块处理路径<br />◆  能够使用 http 模块写一个基本的 web 服务器<br />◆  能够说出模块化的好处<br />◆  能够知道 CommonJS 规定了哪些内容<br />◆  能够说出 Node.js 中模块的三大分类各自是什么<br />◆  能够使用 npm 管理包<br />◆ http 模块<br />◆ 服务器相关的概念<br />◆ 创建最基本的服务器<br />◆ Node 中的模块化<br />◆ export 和 module.exports<br />◆ 包<br />◆ npm 初体验<br />◆ 能够说出 pageage.json 文件中属性的含义<br />◆  知道怎么解决包下载慢的问题<br />◆  了解如何开发包<br />◆  了解如何发布包<br />◆  熟练模块的加载机制<br />◆  熟练 express基本操作<br />◆  能够熟练 express 路由的使用<br />◆  掌握中间件的使用方式<br />◆  能够说出中间件分为哪几类<br />◆  了解如何自定义中间件<br />◆  能够基于 exprss 写接口<br />◆  能够说出解决跨域问题的方法 cors <br />◆  掌握如何实现 JSONP 接口<br />◆ 能够知道如何配置 MySQL 数据库环境<br />◆ 能够认识并使用常见的 SQL 语句操作数据库<br />◆ 能够在项目中操作 MySQL 数据库<br />◆ 前后端的身份认证<br />◆ 能够了解 Session 的实现原理<br />◆ 能够了解 JWT 的实现原理<br />◆ 大事件项目初始化<br />◆ 大事件注册新用户功能
<a name="ZHOBi"></a>
## 什么是 Node.js
Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境<br />
<a name="Eakld"></a>
### 浏览器中的 JavaScript 的组成部分
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614407535758-2b15d33a-92fb-40f5-9ebe-8e2ba75d6ed7.png#align=left&display=inline&height=195&margin=%5Bobject%20Object%5D&name=image.png&originHeight=392&originWidth=682&size=50596&status=done&style=none&width=339)
<a name="GxWmh"></a>
### 为什么  JavaScript 可以在浏览器中被执行 
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614407615834-d26ad230-79f5-47ba-939a-80d26cb28e1e.png#align=left&display=inline&height=147&margin=%5Bobject%20Object%5D&name=image.png&originHeight=279&originWidth=809&size=47838&status=done&style=none&width=426)<br />   总结： <br />1. V8引擎负责解析和执行 JavaScript代码<br />2.内置 API 是由运行环境提供的特殊接口，只能在所属的运行环境中被调用
<a name="3PROK"></a>
### Node 中的 JavaScript 环境<br />
Node 运行环境包含两个部分，分别是：<br />**V8 引擎**，主要负责解析 JavaScript 代码

**内置 API**，我们学习 Node.js 重点就是学习这些内置的 API，从而能够完成后台的开发<br />

1. Node 运行环境和 浏览器运行环境的区别
   - 浏览器是 JavaScript 的前端运行环境<br />
   - Node.js 是 JavaScript 的后端运行环境<br />
   - Node 环境中 没有 DOM 和 BOM 的 API，即在 Node 中无法调用 DOM 和 BOM 等浏览器内置 API<br />同理，在浏览器中也不能够调用 Node 内置 API
<a name="TFmfq"></a>
### Node 可以做什么
Node 作为一个 JavaScript 的运行环境，仅仅提供了基础的功能和 API。然而，基于 Node 提供的这些基础能，很多强大的工具和框架如雨后春笋<br />基于 Express 框架，可以快速构建 Web 应用<br />基于 Electron 框架，可以构建跨平台的桌面应用<br />基于 restify 框架，可以快速构建 API 接口项目<br />读写和操作数据库、创建实用的命令行工具辅助前端开发、etc…
<a name="cqqoP"></a>
### 什么是终端

1. 终端（英文：Terminal）是专门为开发人员设计的，用于实现人机交互的一种方式 <br />
<a name="rjYjU"></a>
#### 终端中的快捷键
在 Windows 的 powershell 或 cmd 终端中，我们可以通过如下快捷键，来提高终端的操作效率：

1. 使用 `↑` 键，可以快速定位到上一次执行的命令<br />
1. 使用 `tab` 键，能够快速补全路径<br />
1. 使用 `esc` 键，能够快速清空当前已输入的命令<br />
1. 输入 `cls` 命令，可以清空终端
<a name="CY4e3"></a>
### `fs` 文件系统
fs模块是Node.js官方提供的、用来**操作文件**的模块。它提供了一系列的方法和属性，用来满足用户对文件的操作需求

   - fs.readFile() 方法，用来读取指定文件中的内容
   - fs.writeFile() 方法，用来向指定的文件中写入内容

如果要在 JavaScript 代码中，使用 fs 模块来操作文件，则需要使用如下的方式先导入它
```javascript
const fs = require('fs')
```
<a name="BcwRL"></a>
#### fs.readFile()
fs.readFile(path[, options], callback)<br />例：fs.readFile('./Tom.txt', 'utf8', function (err, data) {...}<br />参数解读：

1. 参数1：必选参数，字符串，表示文件的路径<br />
1. 参数2：可选参数，表示以什么编码格式来读取文件<br />
1. 参数3：必选参数，文件读取完成后，通过回调函数拿到读取的结果

可以判断 err 对象是否为 null，从而知晓文件读取的结果<br />  // 如果读取成功，则 err 的值为 null<br />  // 如果读取失败，则 err 的值为错误对象， data 的值为 undefined
<a name="zL0tX"></a>
#### fs.writeFile()
fs.writeFile(file, data[, options], callback)<br />参数解读：

1. 参数1：必选参数，需要指定一个文件路径的字符串，表示文件的存放路径<br />
1. 参数2：必选参数，表示要写入的内容<br />
1. 参数3：可选参数，表示以什么格式写入文件内容，默认值是 `utf8`<br />
1. 参数4：必选参数，文件写入完成后的回调函数

fs.writeFile('./Tom.txt', ' Jerry', function (err) {<br />  // 如果文件写入成功，则 err 的值等于 null<br />  // 如果文件写入失败，则 err 的值等于一个错误对象 <br />  // 创建不了文件夹
<a name="IXtym"></a>
### fs 路径问题
<a name="UPwzM"></a>
#### fs 模块路径动态拼接的问题
  在使用 fs 模块操作文件时，如果提供的操作路径是以 ./ 或 ../开头的相对路径时，很容易出现路径动态拼接错误的问题<br />  原因：代码在运行的时候，会以执行 node 命令时所处的目录，动态拼接出被操作文件的完整路径<br />  解决方案：在使用 fs 模块操作文件时，直接提供完整的路径，不要提供 ./ 或 ../ 开头的相对路径，从而防止路径动态拼接的问题<br />__dirname 属性 Node 给提供的一个全局的属性，表示当前文件所处的目录<br />fs.readFile(** __dirname + '/Tom.txt'** , 'utf8', function (err, data) {...}
<a name="v1yet"></a>
### `path` 路径模块
<a name="ed304b8b"></a>
#### 什么是 path 路径模块
path 模块是 Node.js 官方提供的、用来处理路径的模块。它提供了一系列的方法和属性，用来满足用户对路径的处理需求，例如：

   - path.join() 方法，用来将多个路径片段拼接成一个完整的路径字符串
   - path.basename() 方法，用来从路径字符串中，将文件名解析出来
   - path.extname() 方法，可以获取路径中的扩展名部分
2. 如果要在 JavaScript 代码中，使用 path 模块来处理路径，则需要使用如下的方式先导入它
2. const path = rquire('path')
<a name="EwKsi"></a>
####  path 路径拼接
<a name="uAP7F"></a>
####  path.join() 
使用 path.join() 方法，可以把多个路径片段拼接为完整的路径字符串，语法格式如下<br />path.join([...paths])<br />参数解读：

1. ...paths  <string> 路径片段的序列<br />
1. 返回值:  <string>

**可以拼接多个路径片段，可以识别"../"返回上一级，每个片段之间用 ，隔开，把每一个路径片段都以路径的形式识别并拼接**

注意：今后凡是涉及到路径拼接的操作，**都要使用 **path.join() **方法进行处理**。不要直接使用 + 进行字符串的拼接
<a name="fg5W8"></a>
#### path.basename()
path.basename(path[, ext])<br />使用 path.basename() 方法，可以获取路径中的最后一部分，经常通过这个方法获取路径中的文件名，语法格式如下<br />参数解读：

1. path <string> 必选参数，表示一个路径的字符串<br />
1. ext <string> 可选参数，表示文件扩展名<br />
1. 返回: <string> 表示路径中的最后一部分

var fullName = path.basename('/a/b/c/d/index.html')<br />console.log(fullName)  // index.html 打印出文件的名称
<a name="VFGUg"></a>
#### path.extname() 
使用 path.extname() 方法，可以获取路径中的扩展名部分，语法格式如下<br />path.extname(path)<br />参数解读：

1. `path` <string >必选参数，表示一个路径的字符串<br />
1. 返回: <string> 返回得到的扩展名字符串<br />

const fpath = '/a/b/c/d/index.html' // 文件的存放路径<br />var fullName = path.extname(fpath)<br />console.log(fullName)  // .html 返回文件的拓展名
<a name="RA6CK"></a>
### http 模块
**http 模块是 Node.js 官方提供的、用来创建 web 服务器的模块。通过 http 模块提供的 http.createServer() 方法，就能方便的把一台普通的电脑，变成一台 Web 服务器，从而对外提供 Web 资源服务**<br />

1. 如果要希望使用 http 模块创建 Web 服务器，则需要先导入它

const http = require('http')<br />在 Node.js 中，我们不需要使用 IIS、Apache 等这些第三方 web 服务器软件。因为我们可以基于 Node.js 提供的 http 模块，通过几行简单的代码，就能轻松的手写一个服务器软件，从而对外提供 web 服务
<a name="KueJa"></a>
#### ip 地址

1. IP 地址就是互联网上每台计算机的唯一地址，因此 IP 地址 具有唯一性<br />
1. IP 地址 的格式：通常用“点分十进制”表示成(a.b.c.d)的形式，其中，a,b,c,d 都是 0~255 之间的十进制整数
   - 例如：用点分十进表示的 IP地址（192.168.1.1）<br />

**注意事项**： 

1. **互联网中每台 `Web` 服务器，都有自己的 `IP` 地址**
   - 例如：大家可以在 Windows 的终端中运行 ping www.baidu.com 命令，即可查看到百度服务器的 IP 地址
      1. 在开发期间，自己的电脑既是一台服务器，也是一个客户端，为了方便测试，可以在自己的浏览器中输入 127.0.0.1 这个 IP 地址，就能把自己的电脑当做一台服务器进行访问了<br />
<a name="bSSlr"></a>
#### 域名和域名服务器

1. 尽管 IP 地址 能够唯一地标记网络上的计算机，但 IP地址 是一长串数字，不直观，而且不便于记忆，于是人们又发明了另一套字符型的地址方案，即所谓的域名地址(Domain Name)<br />
1. IP地址和 域名 是一一对应的关系，这份对应关系存放在一种叫做域名服务器 (DNS，Domain name server) 的电脑中。使用者只需通过好记的域名访问对应的服务器即可，对应的转换工作由域名服务器实现。因此，域名服务器就是提供 IP 地址 和域名之间的转换服务的服务器<br />

**注意事项：**<br />1.单纯使用 `IP 地址`，互联网中的电脑也能够正常工作。但是有了域名的加持，能让互联网的世界变得更加方便<br />2.在开发测试期间， 127.0.0.1 对应的域名是 localhost，它们都代表我们自己的这台电脑，在使用效果上没有任何区别
<a name="Wem38"></a>
#### 端口号
1.在一台电脑中，可以运行成百上千个 web 服务

2.每个web 服务 都对应一个唯一的端口号

3.客户端发送过来的网络请求，通过端口号，可以被准确地交给对应的 web 服务 进行处理

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614481387871-7129dfe1-9493-4a30-a55a-0624ad9b817d.png#align=left&display=inline&height=167&margin=%5Bobject%20Object%5D&name=image.png&originHeight=207&originWidth=765&size=35125&status=done&style=none&width=617)
<a name="7E1ZK"></a>
### 创建web服务器
```javascript
// 1. 导入 http 模块
const http = require('http')

// 2. 调用 http.createServer() 方法，即可快速创建一个 web 服务器实例
const server = http.createServer()

// 3. 为服务器实例绑定 request 事件，监听客户端的请求,使用服务器实例的 .on() 方法，为服务器绑定一个 request 事件
server.on('request', function (req, res) {
  // 只要有客户端来请求我们自己的服务器，就会被触发 request 事件
  console.log('访问服务器成功')
})

// 调用服务器实例的 .listen() 方法，即可启动当前的 web 服务器实例
server.listen(8080, function () {  
  console.log('running……')
})
```
<a name="MuY9z"></a>
#### `req` 请求对象  ctrl+c 终端停止请求
服务器接收到客户端的请求，就会调用通过 server.on() 为服务器绑定的 request 事件处理程序，如果想在事件处理程序中，访问与客户端相关的数据和属性，可以使用如下方式：
```javascript
server.on('request', function (req, res) {
  // req 是请求对象，它包含了与客户端相关的数据和属性
  // req.url 获取客户端请求的 url 地址
  // req.method 获取客户端请求的类型
  const str = `${req.url} -- ${req.method}`
  console.log(str)
})
```
<a name="uUKg9"></a>
#### `res` 响应对象
```javascript
server.on('request', function (req, res) {
  // res 是响应对象，它包含了与服务器相关的数据和属性
  // 例如：将字符串发送到客户端
  const str = `${req.url} -- ${req.method}`
  // res.end() 方法的作用
  // 向客户端发送指定的内容，并结束这次请求的处理过程
  res.end(str)
})
```
<a name="ZmNLg"></a>
#### 解决中文乱码问题
  // 为了防止中文乱码问题，需要设置响应头，<br />  res.setHeader('Content-Type', 'text/html; charset=utf-8')<br />  // 再把包含中文的内容返回给客户端<br />  res.end(str)
<a name="62MOo"></a>
#### 案例：根据不同的 url 响应不同的内容
<a name="PBbKW"></a>
#### 核心实现步骤

1. 获取请求的 url 地址<br />
1. 设置默认的响应内容为 404 Not found<br />
1. 判断用户请求的是否为 / 或 /index.html 首页<br />
1. 判断用户请求的是否为 /about.html 关于页面<br />
1. 设置 Content-Type 响应头，防止中文乱码<br />
1. 使用 res.end() 把内容响应给客户端<br />
<a name="YkkxH"></a>
### 模块化
<a name="rbaZR"></a>
#### 什么是模块化

1. 模块化是指解决一个复杂问题时，自顶向下逐层**把系统划分成若干模块的过程**。对于整个系统来说，**模块是可组合、分解和更换的单元**<br />
1. 编程领域中的模块化，就是**遵守固定的规则**，把一个**大文件**拆成**独立并互相依赖的多个小模块**<br />
1. 把代码进行模块化拆分的好处
   - 提高了代码的复用性<br />
   - 提高了代码的可维护性<br />
   - 可以实现按需加载<br />
<a name="66FXg"></a>
#### 模块化相关的概念

1. 模块化规范就是对代码进行模块化的拆分与组合时，需要遵守的那些规则，例如：
   - 使用什么样的语法格式来引用模块<br />
   - 在模块中使用什么样的语法格式向外暴露成员<br />
2. 模块化规范的好处：大家都遵守同样的模块化规范写代码，降低了沟通的成本，极大方便了各个模块之间的相互调用，利人利己<br />
<a name="QAEGv"></a>
### Node 中的模块化
<a name="AkAEB"></a>
#### 了解 Node 中模块的 3 个大类
Node.js 中根据模块来源的不同，将模块分为了 3 大类，分别是：

1. 内置模块（内置模块是由 Node.js 官方提供的，例如 fs、path、http 等）<br />
1. 自定义模块（用户创建的每个 .js 文件，都是自定 义模块）<br />
1. 第三方模块（由第三方开发出来的模块，并非官方提供的内置模块，也不是用户创建的自定义模块，**使用前需要先下载**）



<a name="KnE3E"></a>
#### 使用 require 方法加载模块
使用强大的 require() 方法，可以加载需要的内置模块、用户自定义模块、第三方模块进行使用。
```javascript
// 1. 加载内置的 fs 模块
const fs = require('fs')

// 2. 加载用户的自定义模块
const custom = require('./custom.js')

// 3. 加载第三方模块，(使用第三方模块，下面会进行讲解)
const moment = require('moment')
```
**注意事项 1： 使用 require() 方法加载其他模块时，会执行被加载模块中的代码**
<a name="KsDQR"></a>
##### 注意事项2： 在使用 require 加载用户自定义模块期间，可以省略 .js 后缀名
<a name="t4Inf"></a>
#### 了解模块作用域的概念以及好处
<a name="GjW0D"></a>
##### 什么是模块作用域
和函数作用域类似，在自定义模块中定义的变量、方法等成员，只能在当前模块内被访问，外部文件是访问不到的，这种模块级别的访问限制，叫做模块作用域
<a name="KKY8j"></a>
##### 模块作用域的好处
防止了全局变量污染、文件依赖等问题的产生
<a name="hrSES"></a>
##### module 对象
<a name="vUKKm"></a>
##### 在每个 .js 自定义模块中都有一个 module 对象，它里面存储了和当前模块有关的信息，打印如下
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614530088342-eda3247c-dc2f-4a5e-a96e-6aaefe9c82de.png#align=left&display=inline&height=501&margin=%5Bobject%20Object%5D&name=image.png&originHeight=501&originWidth=787&size=196205&status=done&style=none&width=787)
<a name="inlLl"></a>
##### 了解 module.exports 对象的作用
在自定义模块中，可以使用 module.exports 对象，将模块内的成员共享出去，供外界使用

1. 外界用 require() 方法导入自定义模块时，得到的就是 module.exports 所指向的对象
```javascript
// 记载模块.js
const mo = require('./被加载的模块')
console.log(mo)        // {}
```
<a name="IDthI"></a>
##### 使用 module.exports 向外共享成员
```javascript
// 加载模块.js
const mo = require('./被加载的模块.js')

console.log(mo)  //  {}

// 被加载的模块.js
// 向 module.exports 对象上挂载 username 属性
module.exports.username = 'zs'

// 向 module.exports 对象上挂载 sayHello 方法
module.exports.sayHello = function () {
  console.log('Hellp')
}
```
<a name="fKFvF"></a>
#### `exports` 对象
由于 module.exports 单词写起来比较复杂，为了简化向外共享成员的代码，Node 提供了 exports 对象。默认情况下，exports 和 module.exports 指向同一个对象。最终共享的结果，还是以 module.exports 指向的对象为准
<a name="iKgSq"></a>
##### 共享成员时的注意点
使用 require() 方法导入模块时，导入的结果，永远以 module.exports 指向的对象为准
<a name="2AAQ4"></a>
#### `exports` 和 `module.exports` 的使用误区

1. 时刻谨记，require() 模块时，得到的永远是 module.exports 指向的对象<br />
1. 注意：为了防止混乱，建议大家不要在同一个模块中同时使用 exports 和 module.exports<br />
<a name="T9qfA"></a>
#### <br />`CommonJS` 模块化规范

1. Node.js 遵循了 CommonJS 模块化规范，CommonJS规定了模块的特性和各模块之间如何相互依赖<br />
1. CommonJS 规定：
   - 每个模块内部，module 变量代表当前模块<br />
   - module 变量是一个对象，它的 exports 属性（即 module.exports）是对外的接口<br />
   - 加载某个模块，其实是加载该模块的 module.exports 属性。require() 方法用于加载模块<br />
<a name="YhZ7v"></a>
### 包

1. Node.js 中的第三方模块又叫做包
<a name="A1qu9"></a>
####  为什么需要包

1. 由于 Node.js 的内置模块仅提供了一些底层的 API，导致在基于内置模块进行项目开发的时，效率很低<br />
1. 包是基于内置模块封装出来的，提供了更高级、更方便的 API，极大的提高了开发效率<br />
1. 包和内置模块之间的关系，类似于 jQuery 和 浏览器内置 API 之间的关系<br />
<a name="Tu9He"></a>
#### 从哪里下载包
[https://www.npmjs.com/](https://www.npmjs.com/)
<a name="bSt01"></a>
#### 如何下载包

1. 下载包使用 npm ，全名叫做 Node Package Manager（简称 npm 包管理工具），这个包管理工具随着 Node.js 的安装包一起被安装到了用户的电脑上。<br />
1. 可以在终端中执行 npm -v 命令，来查看自己电脑上所安装的 npm 包管理工具的版本号
<a name="nYvTD"></a>
#### `npm install` 命令安装包

1. 如果想在项目中安装指定名称的包，需要运行如下的命令

npm install 包的完整名称  简写：npm i 包的完整名称    例如：npm i moment<br />

<a name="A5u4R"></a>
#### 包管理配置的概念
npm 规定，在项目根目录中，必须提供一个叫做 package.json 的包管理配置文件，用来记录与项目有关的一些配置信息，例如：

- 项目的名称、版本号、描述等
- 项目中都用到了哪些包
- 哪些包只会在开发期间会用到
- 哪些包在开发和部署时都需要用到
<a name="e23c2d28"></a>
#### 快速创建 package.json
npm 包管理工具提供了一个快捷命令，可以在执行命令时所处的目录中，快速创建 package.json 这个包管理配置文件
```javascript
npm init -y
```

- 在项目根目录中，创建一个叫做 package.json的配置文件，即可用来记录项目中安装了哪些包。从而方便剔除 node_modules 目录之后，在团队成员之间共享项目的源代码<br />
- 今后在项目开发中，一定要把 node_modules 文件夹，添加到 .gitignore 忽略文件中
- 注意：上述命令只能在英文的目录下成功运行！所以，项目文件夹的名称一定要使用英文命名，不要使用中文，不能出现空格
- 运行 npm install 命令安装包的时候，npm 包管理工具会自动把包的名称和版本号，记录到 package.json 中
<a name="VQrJv"></a>
#### dependencies 节点的作用
package.json文件中，有一个 dependencies 节点，专门用来记录您使用 npm install命令安装了哪些包
<a name="Ze4ym"></a>
#### 一次性安装所有的包
可以运行 npm install 命令（或 npm i）一次性安装所有的依赖包
<a name="229ae655"></a>
#### `devDependencies` 节点的作用

1. 如果某些包只在项目开发阶段会用到，在项目上线之后不会用到，则建议把这些包记录到 `devDependencies` 节点中<br />
1. 与之对应的，如果某些包在开发和项目上线之后都需要用到，则建议把这些包记录到 `dependencies` 节点中

npm install 包名 --save-dev<br />npm i 包名 -D
<a name="UuWXA"></a>
### 包的分类
<a name="3hUza"></a>
#### 项目包

1. 那些被安装到项目的 `node_modules` 目录中的包，都是项目包
1. 项目包又分为两类，分别是：
   - 开发依赖包，被记录到 `devDependencies` 节点中的包，只在开发期间会用到
   - 核心依赖包，被记录到 `dependencies` 节点中的包，在开发期间和项目上线之后都会用到

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614687777584-65329fd3-654b-4279-b9ee-899aba7e5b6c.png#align=left&display=inline&height=137&margin=%5Bobject%20Object%5D&name=image.png&originHeight=137&originWidth=687&size=34522&status=done&style=none&width=687)
<a name="Iiyc8"></a>
#### 全局包

1. 在执行 `npm install` 命令时，如果提供了 `-g` 参数，则会把包安装为全局包
1. 全局包会被安装到 `C:\Users\用户目录\AppData\Roaming\npm\node_modules` 目录下
1. 注意：
   - 只有工具性质的包，才有全局安装的必要性。因为它们提供了好用的终端命令
   - 判断某个包是否需要全局安装后才能使用，可以参考官方提供的使用说明即可

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614687789003-b4b0e4cc-d060-4af9-bba1-9c120ff614a2.png#align=left&display=inline&height=121&margin=%5Bobject%20Object%5D&name=image.png&originHeight=121&originWidth=653&size=23226&status=done&style=none&width=653)<br />
<a name="sVyhZ"></a>
#### 卸载包

1. 可以运行 ，来卸载指定的包：

注意：npm uninstall 命令执行成功后，会把卸载的包，自动从 package.json 的 dependencies 中移除掉
<a name="gVVYu"></a>
### 包下载慢的问题
因为包数据存储在国外的npm服务器上，网络数据的传输需要经过漫长的海底光缆，我们可以通过淘宝npm镜像服务器进行下载<br />**切换 `npm` 的下包镜像源**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614687600539-c98afd2f-f6e3-46bc-a3e9-53b76f832812.png#align=left&display=inline&height=254&margin=%5Bobject%20Object%5D&name=image.png&originHeight=254&originWidth=707&size=60293&status=done&style=none&width=707)**
<a name="oB3DA"></a>
### 开发属于自己的包--见模板
<a name="lpiva"></a>
### 模块的加载机制
<a name="QtNBU"></a>
#### 优先从缓存中加载
模块在第一次加载后会被缓存，这意味着多次调用 `require()` 方法不会导致模块的代码被多次执行<br />注意：不论内置模块、用户自定义模块、还是第三方模块，他们都会优先从缓存中加载，从而提高模块的加载效率
<a name="mHQR9"></a>
#### 内置模块的加载优先级
内置模块是由 `Node.js` 官方提供的模块，**内置模块的加载优先级最高**<br />例如： `require('fs')` 始终返回内置的 `fs` 模块，即使在 `node_modules` 目录下有名字相同的包也叫做 `fs`
<a name="vCfjq"></a>
#### 自定义模块的加载机制

1. 使用 require() 加载自定义模块时，必须指定以 `./` 或者 `../` 开头的路径标识符。在加载自定义模块时，如果没有指定 `./` 或 `../` 这样的路径标识符，则 `node` 会把它当作 `内置模块` 或 `第三方模块` 进行加载<br />
1. 在使用 `require()` 导入自定义模块时，如果省略了文件的拓展名，则 `Node` 会按照顺序分别尝试加载以下文件
   - 按照 **确切的文件名** 进行加载<br />
   - 补全 **`.js`  **扩展名进行加载<br />
   - 补全 **`.json` ** 扩展名进行加载<br />
   - 补全 **`.node`** 扩展名进行加载<br />
   - 加载失败，终端报错<br />
<a name="1BLpD"></a>
#### 第三方模块的加载机制

1. 如果传递给 `require()` 的模块标识符不是一个内置模块，也没有以 `'./'` 或  `'../'` 开头，则 `Node.js` 会从当前模块的父目录开始，尝试从 `/node_modules` 文件夹中加载第三方模块<br />
1. **如果没有找到对应的第三方模块，则移动到再上一层父目录中，进行加载，直到文件系统的根目录**<br />



3. 假设在 `C:\Users\itheima\project\foo.js` 文件里调用了 `require('tools')`，则 `Node.js` 会按以下顺序查找
   - `C:\Users\itheima\project\node_modules\tools`<br />
   - `C:\Users\itheima\node_modules\tools`<br />
   - `C:\Users\node_modules\tools`<br />
   - `C:\node_modules\tools`<br />
<a name="f78yp"></a>
#### 目录作为模块
当把目录作为模块标识符，传递给 `require()` 进行加载的时候，有三种加载方式：

1. 在被加载的目录下查找一个叫做 `package.json` 的文件，并寻找 `main` 属性，作为 `require()` 加载的入口<br />
1. 如果目录里没有 `package.json` 文件，或者 `main` 入口不存在或无法解析，则 `Node.js` 将会试图加载目录下的 `index.js` 文件<br />
1. 如果以上两步都失败了，则 `Node.js` 会在终端打印错误消息，报告模块的缺失：`Error: Cannot find module xxx`<br />
<a name="LLN6o"></a>
### express
<a name="JR6o0"></a>
#### 什么是 express

1. 通俗理解：`Express` 是基于 `Node.js` 平台的内置模块 http 进一步封装出来，快速、开放、极简的 `Web` 开发框架<br />
1. `Express` 的本质：就是一个 `npm` 上的第三方包，提供了快速创建 Web 服务器的便捷方法

对于前端程序员来说，最常见的两种服务器，分别是：

- **`Web` 网站服务器**：专门对外提供 `Web` 网页资源的服务器。<br />
- **`API` 接口服务器**：专门对外提供 `API` 接口的服务器。<br />
<a name="ZnXzM"></a>
#### 基本使用：
npm i express
```javascript
// 1.导入 express
const express = require('express')
// 2. 创建 web 服务器
const app = express()

// 4. 监听客户端的 GET 和 Post 请求，并向客户端响应具体的内容
app.get('/user', (req, res) => {
  // 调用 express 提供的 res.send() 方法，向客户端响应一个 JSON 对象
  res.send({ name: 'zs', age: 20, gender: '男' })
})

app.post('/user', (req, res) => {
  // 调用 express 提供的 res.send() 方法，向客户端响应一个文本字符串
  res.send('请求成功')
})
//5.// 通过 req.query 可以获取到客户端发送过来的，查询参数
app.get('/', (req, res) => {
  // 注意：默认情况下， req.query 是一个空对象
  console.log(req.query)
  res.send(req.query)
})

// 3. 调用 app.listen(端口号, 启动后的回调函数), 启动服务器
app.listen(80, () => {
  console.log('running……')
})
```
<a name="C2R3p"></a>
#### 获取url中携带的查询参数
通过 `req.query` 对象，可以访问到客户端通过查询字符串的形式，发送到服务器的参数，见上代码5.
<a name="6VCsF"></a>
#### 获取 URL 中的动态参数
通过 `req.params` 对象，可以访问到 `URL` 中，通过 : 匹配到的动态参数<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614689066814-41d2529f-2a6d-4e83-a93d-d70ea5abac00.png#align=left&display=inline&height=257&margin=%5Bobject%20Object%5D&name=image.png&originHeight=257&originWidth=735&size=61737&status=done&style=none&width=735)<br />补充知识点

- `/:id` -- id 值不是固定的，可以自己定义，例如： `/:ids`<br />
- 展示到页面中的 `id` 键，是自定义的变量值<br />
- 参数可以有多个，例如： `/:ids/:name`
- `res.send({msg:"id为"+req.params.id+"的用户数据"})`
<a name="FJtsv"></a>
#### 托管静态资源
<a name="g88KD"></a>
##### `express.static()`

1. `express` 提供了一个非常好用的函数，叫做 `express.static()`，通过它，我们可以非常方便地创建一个静态资源服务器，例如，通过如下代码就可以将 `public` 目录下的图片、`CSS` 文件、`JavaScript` 文件对外开放访问了<br />
1. ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614689104255-4aa0ff04-9bd4-45b9-be12-1ccf1fc0b4ae.png#align=left&display=inline&height=54&margin=%5Bobject%20Object%5D&name=image.png&originHeight=54&originWidth=433&size=9924&status=done&style=none&width=433)
1. 注意：`Express` 在指定的静态目录中查找文件，并对外提供资源的访问路径。因此，存放静态文件的目录名不会出现在 `URL` 中
<a name="TSiTz"></a>
##### 托管多个静态资源目录

1. 如果要托管多个静态资源目录，请多次调用 `express.static()` 函数，访问静态资源文件时，`express.static()` 函数会根据目录的添加顺序查找所需的文件<br />
1. ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614689144789-eac0eb30-2a6a-4e32-83f0-80a62173cb2e.png#align=left&display=inline&height=66&margin=%5Bobject%20Object%5D&name=image.png&originHeight=66&originWidth=398&size=18887&status=done&style=none&width=398)
<a name="XcnDQ"></a>
#####   挂载路径前缀
如果希望在托管的静态资源访问路径之前，挂载路径前缀，则可以使用如下的方式<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614689196261-0536e61f-e0e8-47b0-98b2-6bd7c201ff27.png#align=left&display=inline&height=42&margin=%5Bobject%20Object%5D&name=image.png&originHeight=42&originWidth=487&size=11710&status=done&style=none&width=487)
<a name="eCcox"></a>
#### 使用 `nodemon` 实现后台项目的重启
nodemon index.js
<a name="ydoJ5"></a>
### Express 路由
<a name="NLOrw"></a>
#### 路由的概念

1. 路由就是**映射关系**<br />
1. 根据不同的用户 URL 请求，返回不同的内容<br />
1. 本质：URL 请求地址与服务器资源之间的对应关系<br />
<a name="a2NF9"></a>
#### Express 中的路由

1. 在 `Express` 中，路由指的是**客户端的请求**与**服务器处理函数**之间的**映射关系**
1. Express 中的路由分 3 部分组成，分别是**请求的类型**、**请求的 URL 地址**、**处理函数**

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614752458015-3025cc44-eaf2-48f7-8089-395359cffb09.png#align=left&display=inline&height=296&margin=%5Bobject%20Object%5D&name=image.png&originHeight=296&originWidth=490&size=54242&status=done&style=none&width=490)
<a name="zHqcw"></a>
#### 路由的匹配过程

1. 每当一个请求到达服务器之后，**需要先经过路由的匹配**，只有匹配成功之后，才会调用对应的处理函数<br />
1. 在匹配时，会按照路由的顺序进行匹配，如果**请求类型**和**请求的 URL **同时匹配成功，则 `Express` 会将这次请求，转交给对应的 function 函数进行处理

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614752765003-53ed213d-9cb4-40ae-b45a-86364d1fc840.png#align=left&display=inline&height=322&margin=%5Bobject%20Object%5D&name=image.png&originHeight=322&originWidth=745&size=61920&status=done&style=none&width=745)<br />路由匹配的注意点

- 按照定义的**先后顺序**进行匹配<br />
- **请求类型**和**请求的URL**同时匹配成功，才会调用对应的处理函数<br />
<a name="cHfT7"></a>
#### 模块化路由

1. 为了方便对路由进行模块化的管理，`Express` 不建议将路由直接挂载到 `app` 上，而是推荐将路由抽离为单独的模块，将路由抽离为单独模块的步骤如下
   - 创建路由模块对应的 `.js` 文件<br />
   - 调用 `express.Router()`函数创建路由对象<br />
   - 向路由对象上挂载具体的路由<br />
   - 使用 `module.exports` 向外共享路由对象<br />
   - 使用 `app.use()` 函数注册路由模块
```javascript
// 1. 导入 express
const express = require('express')
// 2. 创建路由对象
const router = express.Router()
// 3. 挂载获取用户列表的路由
router.get('/user/list', (req, res) => {
  res.send('用户列表')
})
// 4. 挂载添加用户列表的路由
router.post('/user/add', (req, res) => {
  res.send('添加用户')
})
// 5. 向外导出路由对象
module.exports = router
```
<a name="oOA5O"></a>
#### 注册路由模块

1. 导入路由模块<br />
1. 使用 `app.use()` 注册路由模块
```javascript
const express = require('express')
const app = express()
// 导入路由模块
const userRouter = require('./002-router')
// 使用 app.use() 注册路由模块
app.use(userRouter)
app.listen(3000, () => {
  console.log('running……')
})
```
<a name="tRe4I"></a>
#### 为路由模块添加前缀

1. 类似于托管静态资源写法，为静态资源统一挂载访问前缀一样<br />
1. 注意，添加了路由前缀后，访问的路由的时候，也应该加上前缀
```javascript
const express = require('express')
const app = express()
// 导入路由模块
const userRouter = require('./002-router')
// 使用 app.use() 注册路由模块
// 给路由模块添加统一得到访问前缀 /api
app.use('/api', userRouter)
app.listen(3000, () => {
  console.log('running……')
})
```
<a name="UjjpM"></a>
### 中间件
<a name="df073fc3"></a>
#### 中间件的概念

1. 什么是中间件<br />所谓的中间件（`Middleware` ），特指业务流程的中间处理环节
<a name="20674fac"></a>
#### express 中间件的调用流程
当一个请求到达 Express 的服务器之后，可以连续调用多个中间件，从而对这次请求进行预处理<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614757442807-f1d58312-c81a-45ad-a0e5-8b41a5039c46.png#align=left&display=inline&height=315&margin=%5Bobject%20Object%5D&name=image.png&originHeight=315&originWidth=595&size=44874&status=done&style=none&width=595)
<a name="BiA16"></a>
#### Express 中间件的格式

1. Express 的中间件，**本质上就是一个 `function` 处理函数**，`Express` 中间件的格式如<br />

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614754980881-78ec857a-1646-4a94-a083-d6f5e41301f9.png#align=left&display=inline&height=327&margin=%5Bobject%20Object%5D&name=image.png&originHeight=327&originWidth=783&size=191218&status=done&style=none&width=783)
<a name="ZNaI7"></a>
#### 全局生效的中间件
通过调用 `app.use(中间件函数)`，即可顶一个全局生效的中间件<br />const kw = (req, res, next) => {<br />  console.log('这是最简单的中间件函数')<br />  next()<br />}
<a name="6b607d93"></a>
#### 中间件的作用
多个中间件之间，共享同一份 `req` 和 `res`，基于这样的特性，我们可以在**上游** 的中间件中，统一为 `req` 或 `res` 对象添加自定义的属性和方法，供下游的中间件或路由进行使用
<a name="eLXSy"></a>
#### 局部生效的中间件
不使用 `app.use()` 定义的中间件，叫做局部生效的中间件<br />const mv1 = (req, res, next) => {<br />  console.log('这是中间件函数')<br />  next()<br />}<br />// mv1、mv2 这个中间件只在 "当前路由中生效"，这种用法属于 "局部生效的中间件"<br />app.get('/', mv1, mv2, (req, res) => {<br />  res.send('Home Page')<br />})
<a name="qNEkm"></a>
#### 中间件的5个使用注意事项

1. 一定要在路由之前注册中间件<br />
1. 客户端发送过来的请求，可以连续调用多个中间件进行处理<br />
1. 执行完中间件的业务代码之后，不要忘记调用 `next()` 函数<br />
1. 为了防止代码逻辑混乱，调用 `next()` 函数后不要再写额外的代码<br />
1. 连续调用多个中间件时，多个中间件之间，共享 `req` 和 `res` 对象
<a name="31mAQ"></a>
### 中间件的分类

1. 为了方便大家理解和记忆中间件的使用，Express 官方把常见的中间件用法，分成了 5 大类，分别是
   - 应用级别的中间件<br />
   - 路由级别的中间件<br />
   - 错误级别的中间件<br />
   - Express 内置的中间件<br />
   - 第三方的中间件
<a name="ByqUM"></a>
#### 应用级别的中间件

- 通过 app.use() 或 app.get() 或 app.post() ，绑定到 app 实例上的中间件，叫做应用级别的中间件
<a name="E9g4h"></a>
#### 路由级别的中间件

1. 绑定到 `express.Router()` 实例上的中间件，叫做路由级别的中间件
1. 用法上和应用级别中间件没有任何区别，只不过，应用级别中间件是绑定到 `app` 实例上，路由级别中间件绑定到 `router` 实例上

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614772612851-90ccbc9c-41fb-4e3a-a862-ba1d003cbc6c.png#align=left&display=inline&height=329&margin=%5Bobject%20Object%5D&name=image.png&originHeight=329&originWidth=492&size=100682&status=done&style=none&width=492)
<a name="LWu7o"></a>
#### 错误级别中间件

1. 错误级别中间件的作用： 专门用来捕获整个项目中发生的异常错误，从而防止项目异常崩溃的问题<br />
1. 格式：错误级别中间件的 function 处理函数中，必须有 4 个形参，形参顺序从前到后，分别是`(err, req, res, next)`<br />
1. **注意： 错误级别的中间件，必须注册在所有路由之后**<br />
```javascript
const express = require('express')
const app = express()
// 1. 路由
app.get('/', (req, res) => {
  // 1.1 抛出一个自定义的错误
  throw new Error('服务器内部发生了错误')
  res.send('Home Page.')
})
// 2. 错误级别的中间件
// 注意：错误级别的中间件，必须注册在所有路由之后
app.use((err, req, res, next) => {
  // 2.1 在服务器打印错误消息
 console.log('发生了错误：' + err.message)
  // 2.2 向客户端响应错误相关的内容 
  res.send(err.message)
})
app.listen(3000, () => {
  console.log('running……')
})
```
<a name="7006dd3a"></a>
####  Express内置的中间件
自 `Express 4.16.0` 版本开始，`Express` 内置了 3 个常用的中间件，极大的提高了 `Express` 项目的开发效率和体验

1. `express.static` 快速托管静态资源的内置中间件，例如： HTML 文件、图片、`CSS` 样式等（无兼容性）<br />
1. `express.json` 解析 `JSON` 格式的请求体数据（**有兼容性**，仅在 `4.16.0+` 版本中可用）<br />
1. `express.urlencoded` 解析 `URL-encoded` 格式的请求体数据（**有兼容性**，仅在 `4.16.0+` 版本中可用）<br />
1. ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614772707672-a18490fa-f59f-4b6c-852d-382017772b87.png#align=left&display=inline&height=161&margin=%5Bobject%20Object%5D&name=image.png&originHeight=161&originWidth=608&size=49441&status=done&style=none&width=608)
<a name="nPpxm"></a>
##### `express.json` 中间件的使用
注意：除了错误级别的中间件，其他的中间件，必须在路由之前进行配置<br />`express.json()`  中间件，解析表单中的 `JSON` 格式的数据<br />app.use(express.json())<br /> // 在服务器，可以使用 req.body 这个属性，来接收客户端发送过来的请求体数据,是一个**对象**<br />  // 默认情况下，如果不配置解析表单数据中间件，则 req.body 默认等于 undefined
<a name="4KKrL"></a>
##### `express.urlencoded` 中间件的使用
`express.urlencoded` 解析 `URL-encoded` 格式的请求体数据<br />// 通过 express.urlencoded() 这个中间件，来解析表单中的 url-encoded 格式的数据<br />app.use(express.urlencoded({ extended: false }))  //固定写法
<a name="idKo7"></a>
#### 第三方的中间件

1. 非 `Express` 官方内置，而是由第三方开发出来的中间件，叫做第三方中间件。在项目中，大家可以按需下载并配置第三方中间件，从而提高项目的开发效率<br />
1. 例如：在 `express@4.16.0` 之前的版本中，经常使用 `body-parser` 这个第三方中间件，来解析请求体数据。使用步骤如下
   - 运行 `npm install body-parser` 安装中间件<br />
   - 使用 `require` 导入中间件<br />
   - 调用 `app.use()` 注册并使用中间件<br />
3. **注意：`Express` 内置的 `express.urlencoded` 中间件，就是基于 `body-parser` 这个第三方中间件进一步封装出来的**

//  使用 app.use() 注册中间件<br />app.use(bodyParser.urlencoded({ extended: false }))
<a name="R70Gm"></a>
### 接口的跨域问题

1. 到目前为止，我们编写的 `GET` 和 `POST` 接口，存在一个很严重的问题：**不支持跨域请求**<br />
1. 解决接口跨域问题的方案主要有两种
   - **CORS**  (主流的解决方案，推荐使用)<br />
   - **JSONP**  (有缺陷的解决方案：只支持 GET 请求)<br />
<a name="IWeS9"></a>
#### cors
<a name="lmiqW"></a>
#####  什么是 CORS

1. `CORS` (跨域资源共享) 由一系列 `HTTP` 响应头组成，这些 `HTTP` 响应头决定浏览器 **是否阻止前端 JS 代码跨域获取资源**<br />
1. 浏览器的**同源安全策略**默认会阻止网页“跨域”获取资源。但如果接口服务器**配置了 CORS 相关的 HTTP 响应头**，就可以**解除浏览器端的跨域访问限制**
1. `CORS` 主要在服务器端进行配置。客户端浏览器无须做任何额外的配置，即可请求开启了 `CORS` 的接口<br />
1. `CORS` 在浏览器中有兼容性。只有支持 `XMLHttpRequest Level2` 的浏览器，才能正常访问开启了 `CORS` 的服务端接口（例如：`IE10+`、`Chrome4+`、`FireFox3.5+`）
<a name="2Jbcz"></a>
##### Access-Control-Allow-Origin
响应头部中可以携带一个 `Access-Control-Allow-Origin` 字段<br />`origin` 参数的值指定了允许访问该资源的外域 `URL`<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614840646903-fe0257b3-73de-4ccb-a1a5-507b5667d71f.png#align=left&display=inline&height=55&margin=%5Bobject%20Object%5D&name=image.png&originHeight=55&originWidth=632&size=15483&status=done&style=none&width=632)<br />如果指定了 `Access-Control-Allow-Origin` 字段的值为通配符 *，表示允许来自任何域的请求<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614840667388-5b89e507-a008-4a44-a3b0-69752ed25a1c.png#align=left&display=inline&height=40&margin=%5Bobject%20Object%5D&name=image.png&originHeight=40&originWidth=608&size=12339&status=done&style=none&width=608)
<a name="PgF9g"></a>
#####  Access-Control-Allow-Headers
默认情况下，CORS 仅支持客户端向服务器发送如下的 9 个请求头

- `Accept`<br />
- `Accept-Language`<br />
- `Content-Language`<br />
- `DPR`<br />
- `Downlink`<br />
- `Save-Data`<br />
- `Viewport-Width`<br />
- `Width`<br />
- `Content-Type` （值仅限于 `text/plain`、`multipart/form-data`、`application/x-www-form-urlencoded` 三者之一）<br />

如果客户端向服务器发送了额外的请求头信息，则需要在服务器端，通过 `Access-Control-Allow-Headers` 对额外的请求头进行声明，否则这次请求会失败！<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614840728355-72260732-531d-417a-8fdf-da6ca0583640.png#align=left&display=inline&height=117&margin=%5Bobject%20Object%5D&name=image.png&originHeight=117&originWidth=707&size=46634&status=done&style=none&width=707)
<a name="ixqxL"></a>
##### Access-Control-Allow-Methods

1. 默认情况下，`CORS` 仅支持客户端发起 `GET`、`POST`、`HEAD` 请求<br />
1. 如果客户端希望通过 `PUT`、`DELETE` 等方式请求服务器的资源，则需要在服务器端，通过 `Access-Control-Alow-Methods` 来指明实际请求所允许使用的 `HTTP` 方法<br />

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614840971898-3828ad72-f95e-41e5-8de1-d81a81a0baa0.png#align=left&display=inline&height=155&margin=%5Bobject%20Object%5D&name=image.png&originHeight=155&originWidth=708&size=47972&status=done&style=none&width=708)
<a name="3d283c33"></a>
#### CORS 请求的分类
客户端在请求 CORS 接口时，根据请求方式和请求头的不同，可以将 CORS 的请求分为两大类，分别是：

- 简单请求<br />
- 预检请求<br />

**简单请求**：<br />同时满足以下两大条件的请求，就属于简单请求

- **请求方式**：`GET`、`POST`、`HEAD` 三者之一<br />
- HTTP 头部信息不超过以下几种字段：
   - 无自定义头部字段<br />
   - `Accept`<br />
   - `Accept-Language`<br />
   - `Content-Language`<br />
   - `DPR`<br />
   - `Downlink`<br />
   - `Save-Data`<br />
   - `Viewport-Width`<br />
   - `Width`<br />
   - `Content-Type`（只有三个值 `application/x-www-form-urlencoded`、`multipart/form-data`、`text/plain`）

**预检请求**

1. 只要符合以下任何一个条件的请求，都需要进行预检请求
   - 请求方式为 `GET`、`POST`、`HEAD` 之外的请求 `Method` 类型<br />
   - 请求头中包含自定义头部字段<br />
   - 向服务器发送了 `application/json` 格式的数据<br />
2. 在浏览器与服务器正式通信之前，浏览器会**先发送 OPTION 请求进行预检，以获知服务器是否允许该实际请求**，所以这一次的 OPTION 请求称为“预检请求”。**服务器成功响应预检请求后，才会发送真正的请求，并且携带真实数据**<br />
<a name="KLr1W"></a>
####  简单请求和预检请求的区别

1. 简单请求的特点：客户端与服务器之间**只会发生一次请求**<br />
1. 预检请求的特点：客户端与服务器之间**会发生两次请求，OPTION 预检请求成功之后，才会发起真正的请求**
<a name="V7ZVj"></a>
## 数据库

1. 数据库（database）是用来组织、存储和管理数据的仓库<br />
1. 为了方便管理互联网世界中的数据，就有了数据库管理系统的概念（简称：数据库）。用户可以对数据库中的数据进行新增、查询、更新、删除等操作

常见的数据库分类下面几种

- MySQL 数据库（目前使用最广泛、流行度最高的开源免费数据库；Community(社区版本免费) + Enterprise(收费)）<br />
- Oracle 数据库（收费）<br />
- SQL Server 数据库（收费）<br />
- Mongodb 数据库 (Community + Enterprise)

传统数据库(关系型数据库或SQL数据库)<br />MySQL、Oracle、SQL Server，这三者的设计理念相同，用法比较类似<br />新型数据库(非关系数据库或NoSQL数据库)<br />Mongodb，它在一定程度上弥补了传统型数据库的缺陷<br />
<br />在传统的类型的数据库中，数据的组织结构分为数据库(`database`)、数据表(`table`)、数据行(`row`)、字段(`field`) 这 4 大部分组成

- **数据库**类似于 Excel 的**工作簿**<br />
- **数据表**类似于 Excel 的**工作表**<br />
- **数据行**类似于 Excel 的**每一行数据**<br />
- **字段类**似于 Excel 的**列**<br />
- 每个字段都有对应的数据类型<br />
<a name="my1t9"></a>
#### 设计表的字段名称和数据类型

1. 根据图示设计字段名称<br />
1. `DataType` 常见的数据类型：
   - `int` 整数<br />
   - `varchar(len)` 字符串<br />
   - `tinyint(1)`布尔值<br />
<a name="O54td"></a>
#### 设置字段的特殊标识

1. 设置字段的特殊标识
   - `PK`（`Primary Key`）        --- 主键、唯一标识<br />
   - `NN`（`Not Null`）              --- 值不允许为空<br />
   - `UQ`（`Unique`）                  --- 值唯一<br />
   - `AI`（`Auto Increment`）  --- 值自动增长

<br />
<a name="fb2sK"></a>
### SQL的增删改查<br />
增：<br />`INSERT INTO` 语句用于向数据表中插入新的数据行，语法格式如下<br />insert into 数据表名 (username, password) values ('mz', '123456')<br />
<br />改：<br />`Update` 语句用于修改表中的数据<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614856767070-37a00100-8f97-4c14-ad36-8382a59586da.png#align=left&display=inline&height=36&margin=%5Bobject%20Object%5D&name=image.png&originHeight=36&originWidth=493&size=14215&status=done&style=none&width=493)

- **多个被更新的列之间， 使用英文的逗号进行分隔**<br />
- **where 后面跟着的是更新的条件**<br />
- **注意： 初学者经常忘记提供更新的 where 条件，这样会导致整张表的数据都被更新，一定要慎重**<br />
```sql
update users set password=654321 where id=4
update users set password=888888, status=1 where id=4
```
删：<br />DELETE 语句用于删除表中的行<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614856947800-1786c6dc-2dcc-4177-8819-4927733d1626.png#align=left&display=inline&height=41&margin=%5Bobject%20Object%5D&name=image.png&originHeight=41&originWidth=378&size=10169&status=done&style=none&width=378)<br />**注意： 初学者经常忘记提供更新的 where 条件，这样会导致整张表的数据都被更新，一定要慎重**
```sql
delete from users where id=4
```
查：<br />select * from 表名称    //从指定的表中，查询所有的数据<br />select 列名称 [,列名称2] from 表名称   //从指定的表中，查询出指定列名称（字段）的数据<br />**SQL 语句中的关键字对大小写不敏感**。SELECT 等效于 select，FROM 等效于 from
<a name="z3K24"></a>
#### WHERE 子句
WHERE 子句用于限定选择的标准。在 SELECT、UPDATE、DELETE 语句中，皆可使用 WHERE 子句来限定选择的标.<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614860837267-6787de75-c62a-4efb-a56e-73bdb6c5d965.png#align=left&display=inline&height=176&margin=%5Bobject%20Object%5D&name=image.png&originHeight=176&originWidth=456&size=51558&status=done&style=none&width=456)<br />可在 `WHERE` 子句中使用的运算符

- 注意：在某些版本的 `SQL` 中，操作符 `<>` 可以写为 `!=`<br />

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614860891185-a90bad98-7274-4205-a734-d18783e4d64a.png#align=left&display=inline&height=327&margin=%5Bobject%20Object%5D&name=image.png&originHeight=327&originWidth=680&size=26985&status=done&style=none&width=680)
<a name="ksW0q"></a>
##### SQL 的 AND 和 OR 运算符
`AND` 和 `OR` 可在 `WHERE` 子语句中把两个或多个条件结合起来<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614861022931-d2f39e92-d083-435f-b971-ca2660453150.png#align=left&display=inline&height=237&margin=%5Bobject%20Object%5D&name=image.png&originHeight=237&originWidth=718&size=14032&status=done&style=none&width=718)
<a name="bQycC"></a>
#####  SQL 的 ORDER BY 子句

1. 语法
   - `ORDER BY` 语句用于根据指定的列对结果集进行排序,默认按照升序对记录进行排序，`ASC` 关键字代表升序排序
   - 如果您希望按照降序对记录进行排序，可以使用 `DESC` 关键字<br />
2. `ORDER BY` 子句 - 升序排序<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614861248769-2929e1c1-77f0-49c8-bb1a-b5b8a8d22cd1.png#align=left&display=inline&height=46&margin=%5Bobject%20Object%5D&name=image.png&originHeight=46&originWidth=362&size=3549&status=done&style=none&width=362)
2. ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614861333550-b21447ea-0e3e-4bd1-ad0f-c9dd2c1fbf5b.png#align=left&display=inline&height=87&margin=%5Bobject%20Object%5D&name=image.png&originHeight=87&originWidth=448&size=3897&status=done&style=none&width=448)
<a name="uc050"></a>
##### SQL 的 COUNT(*) 函数
`COUNT(*)` 函数用于返回查询结果的总数据条数

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614861676575-2cf8834c-3445-4d0c-b840-19b89a1f5bbc.png#align=left&display=inline&height=31&margin=%5Bobject%20Object%5D&name=image.png&originHeight=31&originWidth=438&size=2363&status=done&style=none&width=438)
<a name="nnOdZ"></a>
#### 使用 AS 为列设置别名
-- 将列名 username 改为 uname， password 改为 upwd<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615034885780-4c53de02-a0ce-4efd-8a8d-2b4ff1b0bdb5.png#align=left&display=inline&height=30&margin=%5Bobject%20Object%5D&name=image.png&originHeight=30&originWidth=484&size=2647&status=done&style=none&width=484)<br />
<a name="HgPOb"></a>
#### SQL在node里的配置
```javascript
//导入mysql模块
const mysql = require("mysql");
// 2. 建立与 mysql 数据库的连接
var db = mysql.createPool({
  host: '127.0.0.1',  // 数据库的 ip 地址
  user: 'root', // 登录数据库的账号
  password: 'toor', // 登录数据库的密码
  database: 'my_db_01' // 指定要操作哪个数据库
})
module.exports = db;  //对外暴露
```
** id 的唯一性**

1. 插入数据后，发现数据的 `id` 存在间隔<br />
1. 之前存在，后来被删除了，那么在新增数据以后，即使这个 `id` 被删了，这个  `id` 也不会被占用

查
```javascript
// 3. 查询 users 表中所有的用户数据
db.query('select * from users', (err, results) => {
  // 查询失败
  if (err) return console.log(err.message)
  // 查询成功
  console.log(results)
})
```
增
```javascript
// 3. 声明要插入到 users 表中的数据对象
const user = { username: 'tom', password: '123456' }
// 4. 待执行的 sql 语句，其中英文的 ? 表示占位符
const sqlstr = 'insert into users set ?'
// 5. 使用数组的形式，依次为 ？ 占位符指定具体的值
db.query(sqlstr, user ,(err, results) => {
  // 插入失败
  if (err) return console.log(err.message)
  // 插入成功
  if (results.affectedRows === 1) { console.log('插入数据成功') }
})
```
改
```javascript
// 3. 声明要插入到 users 表中的数据对象
const user = { id: 7, username: 'spike', password: '123000' }
// 4. 待执行的 sql 语句
const sqlstr = 'update users set ? where id=?'
// 5. 调用 db.query() 执行 SQL 语句的同时，使用数组依次为占位符指定具体的值
db.query(sqlstr, [user, user.id] ,(err, results) => {
  // 更新失败
  if (err) return console.log(err.message)
  // 更新成功
  if (results.affectedRows === 1) { console.log('更新数据成功') }
})
```
删
```javascript
const sqlstr = 'delete from users where id=?'
// 2. 调用 db.query() 执行 SQL 语句的同时，为占位符指定具体的值
// 注意：如果 sql 语句中有多个占位符，则必须使用数据为每个占位符指定具体的值
// 如果 sql 语句中只有一个占位符，则可以省略
db.query(sqlstr, 7 ,(err, results) => {
  // 删除失败
  if (err) return console.log(err.message)
  // 删除成功
  if (results.affectedRows === 1) { console.log('删除数据成功') }
})
```
使用 DELETE 语句，会把真正的把数据从表中删除掉

为了保险起见，推荐使用**标记删除**的形式，来**模拟删除的动作**

- 标记删除，就是在表中设置类似于 **status** 这样的**状态字段**，来**标记**当前这条数据是否被删除<br />

当用户执行了删除的动作时，我们并没有执行 DELETE 语句把数据删除掉，而是执行了 UPDATE 语句，将这条数据对应的 status 字段标记为删除即可
```javascript
const sqlstr = 'update users set status=1 where id=?'
```
<a name="mzr7e"></a>
### web开发模式，前后端分离

1. 基于**服务端渲染**的传统 Web 开发模式<br />
1. 基于**前后端分离**的新型 Web 开发模式

**前后端不分离**：服务器发送给客户端的 `HTML` 页面，是在**服务器通过字符串的拼接动态生成的**。<br />**前后端分离**：前后端分离的开发模式，**依赖于 Ajax 技术的广泛应用**。简而言之，前后端分离的 Web 开发模式，就是**后端只负责提供 API 接口，前端使用 Ajax 调用接口**的开发模式<br />**前后端不分离**的优点

   - **前端耗时少**。因为服务器端负责动态生成 HTML 内容，浏览器只需要直接渲染页面即可。尤其是移动端，更省电<br />
   - **有利于SEO**。因为服务器端响应的是完整的 HTML 页面内容，所以爬虫更容易爬取获得信息，更有利于SEO<br />

**前后端不分离**的缺点

   - **占用服务器端资源**。即服务器端完成 HTML 页面内容的拼接，如果请求较多，会对服务器造成一定的访问压力<br />
   - **不利于前后端分离，开发效率低**。使用服务器端渲染，则无法进行分工合作，尤其对于前端复杂度高的项目，不利于项目高效开发<br />

**前后端分离**的优点

   - **开发体验好**。前端专注于 UI 页面的开发，后端专注于api 的开发，且前端有更多的选择性<br />
   - **用户体验好**。Ajax 技术的广泛应用，极大的提高了用户的体验，可以轻松实现页面的局部刷新<br />
   - **减轻了服务器端的渲染压力**。因为页面最终是在每个用户的浏览器中生成的<br />

**前后端分离**的缺点

   - **不利于 SEO**。因为完整的 HTML 页面需要在客户端动态拼接完成，所以爬虫对无法爬取页面的有效信息。（解决方案：利用 Vue、React 等前端框架的 **SSR** 技术能够很好的解决 SEO 问题！）<br />

**不谈业务场景而盲目选择使用何种开发模式都是耍流氓**

- 比如企业级网站，主要功能是展示而没有复杂的交互，并且需要良好的 `SEO`，则这时我们就需要使用服务器端渲染<br />
- 而类似后台管理项目，交互性比较强，不需要考虑 `SEO`，那么就可以使用前后端分离的开发模式
- 为了同时兼顾了首页的渲染速度和前后端分离的开发效率，一些网站采用了首屏服务器端渲染 + 其他页面前后端分离的开发模式
<a name="fXWR4"></a>
### 身份认证
身份认证，又称 ”身份验证“，”鉴权“，是指通过一定的手段，完成对用户身份的确认，例如：<br />各大网站的手机验证码登录/邮箱密码登录/二维码登录

- 对于**服务端渲染**和**前后端分离**这两种开发模式来说，分别有着不同的身份认证方案
      - **服务端渲染** 推荐使用 **Session 认证机制**<br />
      - **前后端分离**推荐使用 **JWT 认证机制**

**<br />**HTTP 协议的无状态性**，指的是客户端的每次 HTTP 请求都是独立的，连续多个请求之间没有直接的关系，服务器不会主动保留每次 HTTP 请求的状态
<a name="xYrGU"></a>
#### Cookie

1. `Cookie` 是**存储在用户浏览器中的一段不超过 4 KB 的字符串**。它由一个**名称**（Name）、一个**值**（Value）和其它几个用于控制 Cookie **有效期**、**安全性**、**使用范围**的**可选属性**组成<br />
1. 不同域名下的 Cookie 各自独立，每当客户端发起请求时，会**自动**把**当前域名下**所有**未过期的 Cookie** 一同发送到服务器<br />
1. `Cookie` 的几大特性
   - 自动发送<br />
   - 域名独立<br />
   - 过期时限<br />
   - 4KB 限制

** Cookie 在身份认证中的作用**

1. 客户端第一次请求服务器的时候，服务器通过响应头的形式，向客户端发送一个身份认证的 `Cookie`，客户端会自动将 `Cookie` 保存在浏览器中。<br />
1. 随后，当客户端浏览器每次请求服务器的时候，浏览器会自动将身份认证相关的 `Cookie`，通过请求头的形式发送给服务器，服务器即可验明客户端的身份<br />

**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615036607881-e7a3d2db-15fc-4646-a659-23834fce359b.png#align=left&display=inline&height=192&margin=%5Bobject%20Object%5D&name=image.png&originHeight=395&originWidth=1409&size=77700&status=done&style=none&width=686)**<br />**Cookie 不具有安全性**<br />由于 Cookie 是存储在浏览器中的，而且浏览器也提供了读写 Cookie 的 API，因此 Cookie 很容易被伪造，不具有安全性。因此不建议服务器将重要的隐私数据通过 Cookie 的形式发送给浏览器

**注意：千万不要使用 Cookie 存储重要且隐私的数据！** 比如用户的身份信息、密码等

<a name="OoqIr"></a>
#### session
**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615037079865-962d4931-38c6-40ef-afca-2ecbca05951e.png#align=left&display=inline&height=583&margin=%5Bobject%20Object%5D&name=image.png&originHeight=583&originWidth=1162&size=139367&status=done&style=none&width=1162)**<br />**向 session 中存数据**

1. 当 `express-session` 中间件配置成功后，即可通过 `req.session` 来访问和使用 `session` 对象，从而存储用户的关键信息

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615037341786-b1af2d52-493c-4b23-860d-8985158f7d39.png#align=left&display=inline&height=322&margin=%5Bobject%20Object%5D&name=image.png&originHeight=419&originWidth=821&size=90532&status=done&style=none&width=630)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615037374120-18159f3d-5d7a-4eef-85da-a5b8785ec552.png#align=left&display=inline&height=341&margin=%5Bobject%20Object%5D&name=image.png&originHeight=438&originWidth=809&size=104254&status=done&style=none&width=630)<br />** 从 session 中取数据**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615037471040-843ae7fe-fe29-4cc5-807a-efa472781ee0.png#align=left&display=inline&height=360&margin=%5Bobject%20Object%5D&name=image.png&originHeight=360&originWidth=1065&size=97456&status=done&style=none&width=1065)**<br />**清空 session**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615037509745-d4df1a25-6a8a-4df4-9d42-b3d24fb1ff55.png#align=left&display=inline&height=388&margin=%5Bobject%20Object%5D&name=image.png&originHeight=388&originWidth=550&size=66775&status=done&style=none&width=550)**
<a name="HZKSz"></a>
#### 了解 Session 认证的局限性

1. `Session` 认证机制需要配合 `Cookie` 才能实现。由于 `Cookie` 默认不支持跨域访问，所以，当涉及到前端跨域请求后端接口的时候，需要做很多额外的配置，才能实现跨域 `Session` 认证<br />
1. 注意：
   - 当前端请求后端接口**不存在跨域问题**的时候，**推荐使用 Session** 身份认证机制<br />
   - 前端**需要跨域请求后端接口**的时候，不推荐使用 Session 身份认证机制，**推荐使用 JWT 认证机制**<br />
3. 什么是 JWT
   - `JWT`（英文全称：`JSON Web Token`）是目前最流行的跨域认证解决方案
<a name="IdPGO"></a>
####   JWT 的工作原理
用户的信息通过 Token 字符串的形式，保存在客户端浏览器中

服务器通过还原 Token 字符串的形式来认证用户的身份<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615080186625-4527e58c-ae0d-4f2e-9cd5-aa9d08315ea1.png#align=left&display=inline&height=511&margin=%5Bobject%20Object%5D&name=image.png&originHeight=511&originWidth=990&size=100763&status=done&style=none&width=990)
<a name="tQkAo"></a>
#### JWT 的组成部分

1. `JWT` 通常由三部分组成，分别是 `Header`（头部）、`Payload`（有效荷载）、`Signature`（签名）<br />
1. 三者之间使用英文的“.”分隔，格式如下

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615080239519-fafbf669-306b-478a-9be8-3d9fc8c1c3c1.png#align=left&display=inline&height=56&margin=%5Bobject%20Object%5D&name=image.png&originHeight=56&originWidth=426&size=12569&status=done&style=none&width=426)

- `Payload` 部分才是真正的用户信息，它是用户信息经过加密之后生成的字符串<br />
- `Header` 和 `Signature` 是安全性相关的部分，只是为了保证 `Token` 的安全性
<a name="8d01ace5"></a>
####  JWT 的使用方式

1. 客户端收到服务器返回的 `JWT` 之后，通常会将它储存在 `localStorage` 或 `sessionStorage` 中<br />
1. 此后，客户端每次与服务器通信，都要带上这个 `JWT` 的字符串，从而进行身份认证。推荐的做法是把`JWT` 放在 `HTTP` 请求头的 `Authorization` 字段中<br />

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615081968892-d60a227d-61e3-4e1b-a6f4-0d72a715ad26.png#align=left&display=inline&height=68&margin=%5Bobject%20Object%5D&name=image.png&originHeight=68&originWidth=559&size=13478&status=done&style=none&width=559)
<a name="D2WJB"></a>
#### 安装并导入 JWT 相关的包
cnpm i jsonwebtoken express-jwt -S

1. 其中
   - `jsonwebtoken` 用于生成 `JWT` 字符串<br />
   - `express-jwt` 用于将 `JWT` 字符串解析还原成 `JSON` 对象
<a name="I88ru"></a>
#### 定义 secret 密钥

1. 为了保证 `JWT`字符串的安全性，防止 JWT 字符串在网络传输过程中被别人破解，我们需要专门定义一个用于加密和解密的 `secret` 密钥
   - 当生成 `JWT` 字符串的时候，需要使用 `secret` 密钥对用户信息进行加密，最终得到加密好的 JWT 字符串<br />
   - 当把 `JWT` 字符串解析还原成 `JSON` 对象的时候，需要使用 `secret` 密钥进行解密
   - 调用 `jsonwebtoken` 包提供的 `sign()` 方法，将用户的信息加密成 `JWT` 字符串，响应给客户端
```javascript
// 登录成功
  // TODO_03：在登录成功之后，调用 jwt.sign() 方法生成 JWT 字符串。并通过 token 属性发送给客户端
  // 参数1：用户的信息对象
  // 参数2：加密的秘钥
  // 参数3：配置对象，可以配置当前 token 的有效期
  // 记住：千万不要把密码加密到 token 字符中
  const tokenStr = jwt.sign({ username: userinfo.username }, secretKey, { expiresIn: '30s' })
  res.send({
    status: 200,
    message: '登录成功！',
    token: tokenStr, // 要发送给客户端的 token 字符串
  })
})
```
<a name="qXgwG"></a>
#### 将 JWT 字符串还原为 JSON 对象

1. 客户端每次在访问那些有权限接口的时候，都需要主动通过请求头中的 `Authorization` 字段，将 `Token` 字符串发送到服务器进行身份认证<br />
1. 此时，服务器可以通过 `express-jwt` 这个中间件，自动将客户端发送过来的  `Token` 解析还原成 `JSON` 对象

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615082492626-da3e69ff-5180-4992-a064-d5b7e1b12c94.png#align=left&display=inline&height=72&margin=%5Bobject%20Object%5D&name=image.png&originHeight=72&originWidth=765&size=11027&status=done&style=none&width=765)
<a name="WX7Ux"></a>
#### 使用 req.user 获取用户信息

1. 当 `express-jwt` 这个中间件配置成功之后，即可在那些有权限的接口中，使用 `req.user` 对象，来访问从 `JWT` 字符串中解析出来的用户信息了
1. ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615082593558-37c9ea57-95a4-46d2-ac60-93cbb554e3e9.png#align=left&display=inline&height=265&margin=%5Bobject%20Object%5D&name=image.png&originHeight=265&originWidth=661&size=17764&status=done&style=none&width=661)
<a name="AoxqZ"></a>
#### 捕获解析 JWT 失败后产生的错误

1. 当使用 `express-jwt` 解析 `Token` 字符串时，如果客户端发送过来的 `Token` 字符串过期或不合法，会产生一个解析失败的错误，影响项目的正常运行<br />
1. 可以通过 `Express` 的错误中间件，捕获这个错误并进行相关的处理
1. ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615082643022-87034427-c3fd-491b-923f-ef217acd4ce6.png#align=left&display=inline&height=329&margin=%5Bobject%20Object%5D&name=image.png&originHeight=329&originWidth=616&size=19136&status=done&style=none&width=616)
