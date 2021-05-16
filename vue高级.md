

<a name="GchCU"></a>
### vue-router的基本使用
一、引入vue文件和vue-router文件<br />二、在vm的html实例中加入<router-view></router-view>标签，占位符<br />三、定义两个或以上组件
```javascript
const User = {
            template: `<h1>user组件</h1>`
        }
        const Register = {
            template: `<h1>register组件</h1>`
        }
```
四、定义vuerouter全局对象的路由规则   含固定属性path, component 
```javascript
const router = new VueRouter({
            routes: [
                { path: "/user", component: User },
                { path: "/register", component: Register },
            ]
        })
```
五、vm实例上挂载router<br />六、在vm的html实例中加入  要加to！！！！！！！<br />        <router-link to="/user">user</router-link><br />        <router-link to="/register">register</router-link>

<a name="Z9UTm"></a>
### 路由重定向
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616033678534-38ad717f-8cf6-4b33-a8d1-3641b9b4cf5e.png#align=left&display=inline&height=279&margin=%5Bobject%20Object%5D&name=image.png&originHeight=279&originWidth=858&size=194594&status=done&style=none&width=858)
<a name="xbbW5"></a>
### 嵌套路由
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616034059986-b842e230-3d06-45f2-a94d-5ae2daf622f4.png#align=left&display=inline&height=66&margin=%5Bobject%20Object%5D&name=image.png&originHeight=66&originWidth=1230&size=160180&status=done&style=none&width=1230)<br />一、定义两个或以上子组件<br />二、父路由的路由规则中添加children属性<br />三、父路由模板中添加<router-view></router-view>标签，占位符
```javascript
 { path: "/register", component: Register, children: [
      { path: "/register/", redirect: "/register/hz" },
      { path: "/register/hz", component: Hz },
      { path: "/register/wz", component: Wz },
    ]
  },
```
<a name="f1256d2a"></a>
### 组件的复用
一、页面添多加几个<router-link to = "/user/n"><br />二、定义统一规则<br />{ path: "/user/:id", component: User }<br />在user组件中，模板渲染id值{{$route.params.id}}<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616037624219-f2b56333-8ebd-463e-b304-04d8c7f2df97.png#align=left&display=inline&height=43&margin=%5Bobject%20Object%5D&name=image.png&originHeight=56&originWidth=795&size=24212&status=done&style=none&width=616)
<a name="mZYUw"></a>
### 解耦
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616038587087-a24364b4-f93d-4000-a5bf-881f52c84fbd.png#align=left&display=inline&height=776&margin=%5Bobject%20Object%5D&name=image.png&originHeight=776&originWidth=776&size=45182&status=done&style=none&width=776)<br />

<a name="JPM5z"></a>
### 命名路由 
便于维护<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616039104017-091b60fc-26f9-44ae-9965-d091c2a1693d.png#align=left&display=inline&height=76&margin=%5Bobject%20Object%5D&name=image.png&originHeight=76&originWidth=1064&size=70489&status=done&style=none&width=1064)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616039122424-82687ea3-8a84-4d76-9096-7b1903acbfdb.png#align=left&display=inline&height=46&margin=%5Bobject%20Object%5D&name=image.png&originHeight=46&originWidth=1165&size=79710&status=done&style=none&width=1165)<br />注意：to之前要加冒号  后面引号一个对象，name："user",<br />parmas:{ 传入的参数 }<br />

<a name="e8Pil"></a>
### router-link
默认渲染成a标签，可以添加tag属性改变其渲染<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617060441204-a4f46340-1900-4122-83b0-e3fa1533030f.png#align=left&display=inline&height=111&margin=%5Bobject%20Object%5D&name=image.png&originHeight=111&originWidth=808&size=122659&status=done&style=none&width=808)
<a name="lKIYW"></a>
### 静态路由和动态路由
静态路由：都允许访问<br />动态路由：有权限访问<br />
<br />

<a name="hSott"></a>
### 声明式导航和编程式导航
声明式导航用在直接渲染到页面<br />编程式导航用于在js中处理逻辑后需要页面进行跳转<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616071730097-d7617758-12a7-4dbb-ab6b-27d1462c5f42.png#align=left&display=inline&height=90&margin=%5Bobject%20Object%5D&name=image.png&originHeight=90&originWidth=420&size=4560&status=done&style=none&width=420)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616049310804-fbce50c2-dac1-4ac8-a4da-0345f9d92b2a.png#align=left&display=inline&height=522&margin=%5Bobject%20Object%5D&name=image.png&originHeight=522&originWidth=1115&size=155385&status=done&style=none&width=1115)
<a name="CZ1ZL"></a>
#### 编程式导航
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616071467789-6afb6b22-d92b-4203-bc52-f8db6c9abae4.png#align=left&display=inline&height=410&margin=%5Bobject%20Object%5D&name=image.png&originHeight=410&originWidth=807&size=167634&status=done&style=none&width=807)<br />
<a name="57M5s"></a>
### 校验邮箱和手机号码的正则
```
const checkEmail = (rule, value, callback) => {
      const regEmail = /^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+(\.[a-zA-Z0-9_-])+/
      if (regEmail.test(value)) {
        return callback()
      }
      callback(new Error('请输入合法的邮箱'))
    }
    const checkMobile = (rule, value, callback) => {
      const regMobile = /^(0|86|17951)?(13[0-9]|15[012356789]|17[678]|18[0-9]|14[57])[0-9]{8}$/
      if (regMobile.test(value)) {
        return callback()
      }
      callback(new Error('请输入合法的手机号码'))
    }
```

<br />
<br />**属性绑定如果是布尔值，需要在前面加冒号**<br />
<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616835113952-8e7b9ec6-375e-4101-b26c-ddb3be6380e8.png#align=left&display=inline&height=313&margin=%5Bobject%20Object%5D&name=image.png&originHeight=313&originWidth=765&size=187221&status=done&style=none&width=765)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616835214877-0949f2ea-2c5a-45df-aa98-2b283c6e99e7.png#align=left&display=inline&height=267&margin=%5Bobject%20Object%5D&name=image.png&originHeight=267&originWidth=1281&size=363969&status=done&style=none&width=1281)<br />     
<a name="S3P1E"></a>
### Scoped CSS
当 `<style>` 标签有 `scoped` 属性时，它的 CSS 只作用于当前组件中的元素。这类似于 Shadow DOM 中的样式封装。它有一些注意事项，但不需要任何 polyfill。使用 `scoped` 后，父组件的样式将不会渗透到子组件中。不过一个子组件的根节点会同时受其父组件的 scoped CSS 和子组件的 scoped CSS 的影响。这样设计是为了让父组件可以从布局的角度出发，调整其子组件根元素的样式<br />如果你希望 `scoped` 样式中的一个选择器能够作用得“更深”，例如影响子组件，你可以使用 `>>>` 操作符：

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617060818395-6ba7e9ef-dcd3-4013-9011-7cf34de317a3.png#align=left&display=inline&height=355&margin=%5Bobject%20Object%5D&name=image.png&originHeight=355&originWidth=749&size=22876&status=done&style=none&width=749)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617060968216-a57c1a27-9109-43cd-84d5-e46ad7d7fe44.png#align=left&display=inline&height=582&margin=%5Bobject%20Object%5D&name=image.png&originHeight=582&originWidth=685&size=269587&status=done&style=none&width=685)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617014766048-29dd8204-77ca-4778-91df-09daf067aa08.png#align=left&display=inline&height=667&margin=%5Bobject%20Object%5D&name=image.png&originHeight=667&originWidth=961&size=158190&status=done&style=none&width=961)
<a name="Vue-nextTick"></a>
### element ui
各种组件进行封装，不能直接在el-标签中直接操作DOM,要加native<br />比如给输入框添加回车搜索的触发事件
```javascript
 <el-input placeholder="请输入内容" v-model="queryInfo.query" @keyup.enter.native= 'getGoodsList'>
```
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617068313857-693b7113-d03c-4dd0-bc0a-0430cb1e1614.png#align=left&display=inline&height=68&margin=%5Bobject%20Object%5D&name=image.png&originHeight=68&originWidth=542&size=8284&status=done&style=none&width=542)<br />element ui中，table要实现树形列表可以添加属性<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617106621407-2995b8b9-3fcf-4523-be3e-b1c77d500b6d.png#align=left&display=inline&height=454&margin=%5Bobject%20Object%5D&name=image.png&originHeight=454&originWidth=1063&size=45827&status=done&style=none&width=1063)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617106790957-f2a93c9c-0639-4162-ae5c-81ed7a424392.png#align=left&display=inline&height=362&margin=%5Bobject%20Object%5D&name=image.png&originHeight=362&originWidth=1056&size=39024&status=done&style=none&width=1056)
<a name="azgHq"></a>
## 优化
nprogress  ->进度条的包<br />用得不多，算用户心理优化。。。<br />打开main.js
```javascript
//导入进度条插件
import NProgress from 'nprogress'
//导入进度条样式
import 'nprogress/nprogress.css'
.....
//请求在到达服务器之前，先会调用use中的这个回调函数来添加请求头信息
axios.interceptors.request.use(config => {
  //当进入request拦截器，表示发送了请求，我们就开启进度条
  NProgress.start()
  //为请求头对象，添加token验证的Authorization字段
  config.headers.Authorization = window.sessionStorage.getItem("token")
  //必须返回config
  return config
})
//在response拦截器中，隐藏进度条
axios.interceptors.response.use(config =>{
  //当进入response拦截器，表示请求已经结束，我们就结束进度条
  NProgress.done()
  return config
})
```
<a name="GYgo4"></a>
### 判断开发环境移除所有的console.log
插件：npm install babel-plugin-transform-remove-console --save-dev<br />在根目录文件的babel.config.js中配置这个属性<br /> "plugins": ["transform-remove-console"]<br />判断生产环境和开发环境来配置不同的plugin属性-->资料查阅vue官方文档文件中的开发环境vs生产环境模式[https://cn.vuejs.org/v2/guide/installation.html#%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83-vs-%E7%94%9F%E4%BA%A7%E7%8E%AF%E5%A2%83%E6%A8%A1%E5%BC%8F](https://cn.vuejs.org/v2/guide/installation.html#%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83-vs-%E7%94%9F%E4%BA%A7%E7%8E%AF%E5%A2%83%E6%A8%A1%E5%BC%8F)
```javascript
//项目发布阶段需要用到的babel插件
const productPlugins = []
//判断是开发还是发布阶段
if(process.env.NODE_ENV === 'production'){
  //发布阶段
  productPlugins.push("transform-remove-console")
}
module.exports = {
  "presets": [
    "@vue/app"
  ],
  "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ],
    ...productPlugins
  ]
}
```
<a name="djXDX"></a>
### 生成打包报告
A.命令行形式生成打包报告vue-cli-service build --report<br />B.在vue控制台生成打包报告点击“任务”=>“build”=>“运行”运行完毕之后点击右侧“分析”，“控制台”面板查看报告
<a name="gditF"></a>
### 部分依赖文件过大,修改webpack的默认配置
修改webpack的默认配置默认情况下，vue-cli 3.0生成的项目，隐藏了webpack配置项，如果我们需要配置webpack需要通过vue.config.js来配置。在项目根目录中创建vue.config.js文件，<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617255102724-2b6103fe-ead6-44dc-ac92-5774a6db7179.png#align=left&display=inline&height=153&margin=%5Bobject%20Object%5D&name=image.png&originHeight=153&originWidth=699&size=54469&status=done&style=none&width=699)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617255149626-92d5d07a-8366-4fa7-9a61-485f6f12c312.png#align=left&display=inline&height=215&margin=%5Bobject%20Object%5D&name=image.png&originHeight=215&originWidth=710&size=50243&status=done&style=none&width=710)<br />process.env.NODE_ENV === 'production'  不是process.env对象上原有的属性，它是我们自己添加上去的一个环境变量，用来确定当前所处的开发阶段
```javascript
module.exports = {
  chainWebpack: config => {
    config.when(process.env.NODE_ENV === 'production', config => {
      config.entry('app').clear().add('./src/main-prod.js')
    })
    config.when(process.env.NODE_ENV === 'development', config => {
      config.entry('app').clear().add('./src/main-dev.js')
    })
  }
}
```
<a name="F9Cht"></a>
### 通过externals加载外部CDN资源
在vue.config.js生产模式下进行externals节点的配置<br />默认情况下，依赖项的所有第三方包都会被打包到js/chunk-vendors.******.js文件中，导致该js文件过大那么我们可以通过externals排除这些包，使它们不被打包到js/chunk-vendors.******.js文件中,项目运行时，会自动去windows全局寻找这些包，所以我们要加载外部CDN的形式解决引入的依赖项<br />vue.config.js
```javascript
 //使用externals设置排除项
            config.set('externals',{
                vue:'Vue',
                'vue-router':'VueRouter',
                axios:'axios',
                lodash:'_',
                echarts:'echarts',
                nprogress:'NProgress',
                'vue-quill-editor':'VueQuillEditor'
            })
```
设置好排除之后，为了使我们可以使用vue，axios等内容，我们需要加载外部CDN的形式解决引入依赖项。打开开发入口文件main-prod.js,删除掉默认的引入的样式代码，然后打开public/index.html添加外部cdn引入代码
```javascript
<!-- nprogress 的样式表文件 -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/nprogress/0.2.0/nprogress.min.css" />
    <!-- 富文本编辑器 的样式表文件 -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/quill/1.3.4/quill.core.min.css" />
    <link rel="stylesheet" href="https://cdn.staticfile.org/quill/1.3.4/quill.snow.min.css" />
    <link rel="stylesheet" href="https://cdn.staticfile.org/quill/1.3.4/quill.bubble.min.css" />
    <!-- element-ui 的样式表文件 -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.8.2/theme-chalk/index.css" />

    <script src="https://cdn.staticfile.org/vue/2.5.22/vue.min.js"></script>
    <script src="https://cdn.staticfile.org/vue-router/3.0.1/vue-router.min.js"></script>
    <script src="https://cdn.staticfile.org/axios/0.18.0/axios.min.js"></script>
    <script src="https://cdn.staticfile.org/lodash.js/4.17.11/lodash.min.js"></script>
    <script src="https://cdn.staticfile.org/echarts/4.1.0/echarts.min.js"></script>
    <script src="https://cdn.staticfile.org/nprogress/0.2.0/nprogress.min.js"></script>
    <!-- 富文本编辑器的 js 文件 -->
    <script src="https://cdn.staticfile.org/quill/1.3.4/quill.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/vue-quill-editor@3.0.4/dist/vue-quill-editor.js"></script>

    <!-- element-ui 的 js 文件 -->
    <script src="https://cdn.staticfile.org/element-ui/2.8.2/index.js"></script>

```
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617259480355-14fe69c5-50f1-4d1f-9206-83b2bfcbc746.png#align=left&display=inline&height=423&margin=%5Bobject%20Object%5D&name=image.png&originHeight=423&originWidth=823&size=178872&status=done&style=none&width=823)
<a name="iCUl4"></a>
### 定制首页内容
开发环境的首页和发布环境的首页展示内容的形式有所不同如开发环境中使用的是import加载第三方包，而发布环境则是使用CDN，那么首页也需根据环境不同来进行不同的实现我们可以通过插件的方式来定制首页内容，打开vue.config.js，编写代码如下
```javascript
module.exports = {
    chainWebpack:config=>{
        config.when(process.env.NODE_ENV === 'production',config=>{
            ......       
            //使用插件
            config.plugin('html').tap(args=>{
                //添加参数isProd
                args[0].isProd = true
                return args
            })
        })
        config.when(process.env.NODE_ENV === 'development',config=>{
            config.entry('app').clear().add('./src/main-dev.js')

            //使用插件
            config.plugin('html').tap(args=>{
                //添加参数isProd
                args[0].isProd = false
                return args
            })
        })
    }
}
```
然后在public/index.html中使用插件判断是否为发布环境并定制首页内容<br />**注意<% %>的用法**
```javascript
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <title><%= htmlWebpackPlugin.options.isProd ? '' : 'dev - ' %>电商后台管理系统</title>

    <% if(htmlWebpackPlugin.options.isProd){ %>
    <!-- nprogress 的样式表文件 -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/nprogress/0.2.0/nprogress.min.css" />
    ........
    <!-- element-ui 的 js 文件 -->
    <script src="https://cdn.staticfile.org/element-ui/2.8.2/index.js"></script>
    <% } %>
  </head>
  .......
```
<a name="DaMEN"></a>
### 路由懒加载
当路由被访问时才加载对应的路由文件，就是路由懒加载。<br />路由懒加载实现步骤：<br />1.安装 @babel/plugin-syntax-dynamic-import打开vue控制台，点击依赖->安装依赖->开发依赖->搜索@babel/plugin-syntax-dynamic-import点击安装。<br />2.打开router.js，更改引入组件代码如下,把原来引入的注释掉，换成第二行，/* webpackChunkName: "welcome" */可以给文件起名方便识别
```javascript
// import Login from './components/Login.vue'
 { path: '/welcome', component: () => import(/* webpackChunkName: "welcome" */'../components/Welcome.vue') },
   //不用插件的方法
   const  home = r => require.ensure( [], () => r (require('../../common/home.vue')))
```
<a name="RFRrG"></a>
### 开启gzip压缩
如果是node后台，就是前端负责<br />打开node后端的vue_shop_server文件夹的终端，输入命令：npm i compression -D打开app.js,编写代码：
```javascript
const express = require('express')
const compression = require('compression')
const app = express()
app.use(compression())//顺序不能反，要在下一行挂载之前
app.use(express.static('./dist'))

app.listen(8998,()=>{
    console.log("server running at http://127.0.0.1:8998")
})
```
使用pm2管理应用打开vue_shop_server文件夹的终端，<br />输入命令：npm i pm2 -g使用pm2启动项目，<br />在终端中输入命令：pm2 start app.js --name 自定义名称<br />查看项目列表命令：pm2 ls<br />重启项目：pm2 restart 自定义名称<br />停止项目：pm2 stop 自定义名称<br />删除项目：pm2 delete 自定义名称
<a name="bExSM"></a>
## scss处理的了解和使用
sass和scss其实是一样的，SASS的3.0版本之前的后缀名为.sass,而版本3.0之后的后缀名是.scss<br />scss编写规范基本和css一致，sass时代有严格的缩进规范并且没有{} 和；<br />
<br />一、sass使用 $ 符号来识别变量,声明了一个高亮的变量,less用的是@
```css
$highlight-color :#f90
#app{
    background-color: $highlight-color;
}
```
二、以空格分割的多条属性也可以标识变量
```css
$basic-border:1px solid #000;
#app{
		border:$basic-border
} 
```
三、变量范围<br />变量可以在css规则块定义之外存在，当变量定义在css规则块之内，那么该变量只能在**此规则块内使用**。<br />四、嵌套语法也是可以用的<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617282860284-2cb30cc0-d4e8-415e-882a-333db2ce257e.png#align=left&display=inline&height=145&margin=%5Bobject%20Object%5D&name=image.png&originHeight=145&originWidth=310&size=37523&status=done&style=none&width=310)<br />五、父选择器<br />css伪类选择器为 a:hover<br />但是scss  将sass文件转换成css文件的时候，会产生一个空格。变成a :hover，会报错，这时候需要加一个&符号
```css
a{
	color:blue;
  &:hover{ color:red }
}
```
假数据<br />webpack有配置在public文件夹下的文件<br />

<a name="cqYvu"></a>
### vue-cli：
基于 webpack 构建，并带有合理的默认配置；
但是用vue-cli建立出来的项目根目录并没有webpack.config.js文件，也找不到相关引用<br />修改：<br />简单的配置方式
调整 webpack 配置最简单的方式就是在 > `vue.config.js` 中的 > `configureWebpack` 选项提供一个对象：// vue.config.js module.exports = {   configureWebpack: {     plugins: [ new MyAwesomeWebpackPlugin() ] } }该对象将会被 > [webpack-merge](https://link.zhihu.com/?target=https%3A//github.com/survivejs/webpack-merge) 合并入最终的 webpack 配置。
<a name="DYLz8"></a>
## svg图片
设置svg图片颜色用fill属性
```javascript
 <svg
      :class="{'is-active':isActive}"
      class="hamburger"
      viewBox="0 0 1024 1024"
      xmlns="http://www.w3.org/2000/svg"
      width="64"
      height="64"
      fill="#fff"
    >
      <path d="M408 442h480c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8H408c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8zm-8 204c0 4.4 3.6 8 8 8h480c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8H408c-4.4 0-8 3.6-8 8v56zm504-486H120c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h784c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8zm0 632H120c-4.4 0-8 3.6-8 8v56c0 4.4 3.6 8 8 8h784c4.4 0 8-3.6 8-8v-56c0-4.4-3.6-8-8-8zM142.4 642.1L298.7 519a8.84 8.84 0 0 0 0-13.9L142.4 381.9c-5.8-4.6-14.4-.5-14.4 6.9v246.3a8.9 8.9 0 0 0 14.4 7z" />
    </svg>
```
<a name="F5Dwq"></a>
## vue->自定义指令
解决用户上传的头像显示不出来的情况下，要用默认图片做头像<br />在根目录src文件里中创建一个指令文件夹directives,并创建文件index.js<br />创建一个自定义指令
```javascript
export const imagerror = {
  // 指令对象 会在当前的dom元素插入到节点之后执行,其他钩子函数见文档
  inserted(dom, options) {
    // options是 指令中的变量的解释  其中有一个属性叫做 value
    // dom 表示当前指令作用的dom对象
    // dom认为此时就是图片
    // 当图片有地址 但是地址没有加载成功的时候 会报错 会触发图片的一个事件 => onerror
    dom.onerror = function() {
      // 当图片出现异常的时候 会将指令配置的默认图片设置为该图片的内容
      // dom可以注册error事件
      dom.src = options.value // 这里不能写死
    }
  }
}
```
第二步：在main.js文件中引入所有的自定义指令，注册自定义指令<br />import * as directives from '@/directives'
```javascript
Vue.directive('指令名称', {
    // 会在当前指令作用的dom元素 插入之后执行
    // options 里面是指令的表达式
    inserted: function (dom,options) {
      XXXXXXXXXX
    }
})
//以上方法每个指令都需要定义一个变量去接收非常麻烦，我们可以通过遍历的方法进行注册
// 注册自定义指令
// 遍历所有的导出的指令对象 完成自定义全局注册
Object.keys(directives).forEach(key => {
  // 注册自定义指令
  Vue.directive(key, directives[key])  //注意没有s
})
```
在需要用到该指令的dom上添加
```javascript
 <img v-imagerror="defaultImg" :src="staffPhoto" class="user-avatar">
   
  默认图片每个人可能都不一样，图片路径不能写死，要用require包裹起来，把它转化成一个变量
 data() {
    return {
      defaultImg: require('@/assets/common/head.jpg')
    }
  }
```
<a name="d21PP"></a>
### 快速新建文件夹
```javascript
$ mkdir departments employees setting salarys social attendances approvals permission(都是文件夹名)
```


<a name="tR9yX"></a>
### 快速创建文件
```javascript
$ touch departments.js employees.js setting.js salarys.js salarys.js social.js attendances.js approvals.js permission.js
```
<a name="RsmVd"></a>
## render函数
functional:true表示这是一个函数式组件<br />函数式组件： 没有data状态，没有响应式数据，只会接收props属性， 没有this， 他就是一个函数

<a name="TU9bm"></a>
### 组件封装复用，但是又有个性定制
组件复用的时候，如果大体相同，可以封装相同组件，但是某些模块稍微有些许区别，比如下拉菜单的数量不同（部门权限），需要新定义<br />

<a name="9rLjG"></a>
### vue.js监听属性watch(handler方法immediate属性deep属性)
[https://www.cnblogs.com/yyh28/p/13222798.html?utm_source=tuicool](https://www.cnblogs.com/yyh28/p/13222798.html?utm_source=tuicool)<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />

