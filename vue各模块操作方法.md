<a name="otDKQ"></a>
### 项目各文件夹
一、所有的路由规则都在router文件夹下的index.js文件中，最终向外暴露router,在main.js中被引入，并挂载到main.js中的vue实例身上<br />二、main.js文件为引入各种js文件css文件的窗口，包括根组件App.vue/router路由/全局样式/字体样式/element ui 插件/axios/配置axios拦截器并将其挂载到vue原型对象身上<br />三、App.vue为页面根组件，啥也没有，只有一个<router-view></router-view>路由占位符<br />四、plugins文件夹为element ui的导入文件夹，内含一个element.js文件，将各种element ui 内置组件供vue使用

<a name="Gk1IT"></a>
### element ui 项目中的表单校验
element ui 的表单检验规则来自第三方的插件async-validator<br />**第一次**：当用户鼠标失去焦点时，对应的输入框自动验证内容和定义的规则能否匹配，<br />方法：在data中定义相关的rules,需要验证的表单，from标签绑定 如下属性<br />        :model="editForm"  绑定数据<br />        :rules="addFormRules"  绑定验证规则<br />表单相应的el-form-item 标签添加 prop="username"绑定不同的验证规则。<br />表单相应的input框，用v-model="editForm.username"绑定不同数据<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617187438191-1b44ca76-7912-4e76-b1fd-fb7c12c8cc95.png#align=left&display=inline&height=190&margin=%5Bobject%20Object%5D&name=image.png&originHeight=190&originWidth=449&size=34850&status=done&style=none&width=449)<br />我们介绍几个基本使用的规则

| 规则 | 说明 |
| --- | --- |
| required | 如果为true，表示该字段为必填 |
| message | 当不满足设置的规则时的提示信息 |
| pattern | 正则表达式，通过正则验证值 |
| min | 当值为字符串时，min表示字符串的最小长度，当值为数字时，min表示数字的最小值 |
| max | 当值为字符串时，max表示字符串的最大长度，当值为数字时，max表示数字的最大值 |
| trigger | 校验的触发方式，change（值改变） / blur （失去焦点）两种， |
| validator | 如果配置型的校验规则不满足你的需求，你可以通过自定义函数来完成校验 |

<a name="daMll"></a>
#### 自定义函数校验规则
validator是一个函数, 其中有三个参数 (rule(当前规则),value(当前值),callback(回调函数))
```javascript
var  func = function (rule, value, callback) {
    // 根据value进行进行校验 
    // 如果一切ok  
    // 直接执行callback
    callback() // 一切ok 请继续
    // 如果不ok 
    callback(new Error("错误信息"))
}
```
<a name="ZzJJ8"></a>
#### 第二次验证（手动校验）！重要
点击提交按钮时，要确认表单上的数据是否都满足验证条件，满足则可以提交，不满足就提示弹框，并阻止提交<br />方法：给from表单绑定ref属性 ref="editFormRef"<br />给提交按钮的点击事件先进行判断<br />this.$refs.editFormRef.validate(async (valid) => { <br />if (!valid) return this.$message.error('校验失败')<br />XXXXXXXXXXXXXXXXX<br />} ）<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617188407728-974838ca-7b21-4bff-9b94-90bb5c180913.png#align=left&display=inline&height=561&margin=%5Bobject%20Object%5D&name=image.png&originHeight=561&originWidth=1068&size=69544&status=done&style=none&width=1068)
<a name="7KZg1"></a>
#### 校验邮箱和手机号码的正则
```javascript
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
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617187399630-6e230a7b-5278-40df-a5ac-5ad35e9d205d.png#align=left&display=inline&height=230&margin=%5Bobject%20Object%5D&name=image.png&originHeight=230&originWidth=644&size=19751&status=done&style=none&width=644)<br />
<a name="E1uzz"></a>
## 鉴权怎么做
  第一步：客户端首先使用用户名跟密码发起请求登录；<br />  第二步：服务端收到请求，去验证用户名与密码是否正确；<br />  第三步：验证成功后，服务端会签发一个 Token，再把这个 Token 发送给客户端；<br />  第四步：客户端收到Token以后可以把它存储起来，比如放在sessionStorage里；<br /> 第五步：根据接口文档  对需要授权的 API 在特定的  字段提供 `token` 令牌 ， axios 添加请求拦截器<br />  第六步：配置路由导航守卫，如果访问的是登录页面直接放行，如果访问的不是登录页面判断一下是否有token，没有的话直接强制跳转会登录页面<br /> 第七步：客户端每次向服务端请求资源的时候需要带着服务端签发的Token，服务端收到请求，然后去验证客户端请求里面带着的 Token，如果验证成功，就向客户端返回请求的数据。
```javascript
//Login.vue中
    login () {
      // validate 回调函数 第一个值 就是布尔值 成功返回true 失败返回false
      this.$refs.loginFromRef.validate(async valid => {
        // console.log(valid)
        if (!valid) return
        const { data: res } = await this.$http.post('login', this.loginFrom)
        if (res.meta.status !== 200) return this.$message.error('登录失败')
        this.$message.success('登录成功')
        // 1.将登录很共之后的token 保存到客户端的 sessionStorage
        // 1.1 项目中除了登录之外的其他API接口 必须在登录之后才能访问
        // 1.2 token 只应当在当前网站打开期间生效所以，将token 保存在sessionStorage 中
        // console.log(res)
        window.sessionStorage.setItem('token', res.data.token)
        // 2.通过编程式导航跳转到后台主页 路由地址 /home  然后创建一个Home.vue 并且在路由里面导入，并且新增一个路由规则
        this.$router.push('home')
    
      })
    }

//main.js 中
// 在request 拦截器中展示进度条  NProgress.start()
axios.interceptors.request.use(config => {
  //   接口文档提示 需要授权的 API ，必须在请求头中使用 Authorization 字段提供 token 令牌
  //   我们手动给他挂载一下
  config.headers.Authorization = window.sessionStorage.getItem('token')
  //  ！！！在最后必须 return config 这是固定写法
  return config
})

//路由中
// 挂载路由导航守卫  设置拦截 如果没有token  的话强制跳转回去 login
router.beforeEach((to, from, next) => {
    // to 代表将要访问的路径
    // from 表示从哪个路径跳转而来
    // next()  放行
    // next() 继续后续事情，next('./login') 强制跳转到login
    if (to.path === "/login") return next();
    // 获取 token
    const tokenStr = window.sessionStorage.getItem("token");
    //   如果没有登录强制跳转回login
    if (!tokenStr) return next("login");
    next();
});
```
<a name="oLNxb"></a>
## vue中配置@为src目录
在vue.config.js中添加如下代码:
```javascript
const path=require('path');  
function resolve (dir) {  
    path.join(__dirname, dir);  
}  
module.exports = {   
 chainWebpack: config => {  
        config.resolve.alias.set('@', resolve('src'))  
    },  
 configureWebpack: {  
        resolve: {  
            extensions: ['js', 'vue'],  
 alias: {  
                '@': resolve('src')  
            }  
        }  
    }  
}
```
<a name="lLnCH"></a>
## 请求拦截器和响应拦截器
基本骨架
```javascript
// 导出一个axios的实例  而且这个实例要有请求拦截器 响应拦截器
import axios from 'axios'
const service = axios.create() // 创建一个axios的实例
service.interceptors.request.use() // 请求拦截器
service.interceptors.response.use() // 响应拦截器
export default service // 导出axios实例
```
<a name="vDFGd"></a>
### api模块的单独封装
先把拦截器设置好才能封装api
<a name="uZh4Q"></a>
### 开发环境和生产环境

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
<br />
<br />
<br />

