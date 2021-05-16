用到的技术：<br />vue/vue-cli/vant/iconfont/axios/
<a name="bAWI9"></a>
### 操作步骤
一、创建vue项目 vue creat 项目名称<br />选 Manually select features （自定义勾选配置）<br />->选分别选择：Babel：es6 转 es5Router：路由Vuex：数据容器，存储共享数据CSS Pre-processors：CSS 预处理器，后面会提示你选择 less、sass、stylus 等Linter / Formatter：代码格式校验<br />->选是否使用 history 路由模式，这里输入 n 不使用<br />->选择 CSS 预处理器，这里选择我们熟悉的 Less<br />->选择校验工具，这里选择 ESLint + Standard config<br />->选择在什么时机下触发代码格式校验：

- Lint on save：每当保存文件的时候<br />
- Lint and fix on commit：每当执行 git commit 提交的时候<br />

这里建议两个都选上，更严谨。<br />->Babel、ESLint 等工具会有一些额外的配置文件，这里的意思是问你将这些工具相关的配置文件写到哪里,这里建议选择第 1 个，保存到单独的配置文件，这样方便我们做自定义配置。
<a name="vmN1K"></a>
### git提交
```javascript
快速有效的直接克隆远程指定分支
git clone -b <指定分支名> <远程仓库地址>
# 创建本地仓库
git init
# 将文件添加到暂存区
git add 文件
# 提交历史记录
git commit "提交日志"
# 添加远端仓库地址
git remote add origin 你的远程仓库地址
# 推送提交
git push -u origin master

如果已有本地仓库（Vue CLI 已经帮我们初始化好了）。
# 添加远端仓库地址
git remote add origin 你的远程仓库地址
# 推送提交
git push -u origin master

如果之后项目代码有了变动需要提交：
git add
git commit -m
git push
```
<a name="Lx8Fx"></a>
### 调整结构目录
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1618126573770-24f9aa75-759d-435d-9ecb-aa958b84f896.png#align=left&display=inline&height=447&margin=%5Bobject%20Object%5D&name=image.png&originHeight=447&originWidth=731&size=35290&status=done&style=none&width=731)
<a name="nm7Q4"></a>
###  创建自己的图标库
https://www.iconfont.cn/<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1618127017421-c940c085-a4f2-45a1-904e-d33c1ea8a94c.png#align=left&display=inline&height=52&margin=%5Bobject%20Object%5D&name=image.png&originHeight=52&originWidth=53&size=1130&status=done&style=none&width=53)新建自己的图标库，引入所需要的图标文件后，生成链接

1. 在styles目录下创建icon.less,将对应的图标样式代码复制过来<br />
1. 在index.less中引用图标样式<br />
```javascript
// 加载图标样式图标
@import './icon.less';
使用字体图标库
 <i class="toutiao toutiao-lishi"></i>
```
<a name="r8qpX"></a>
### 引入Vant组件库--（移动端的element ui）
-> npm i vant<br />在main.js中注册
```javascript
import Vant from 'vant'
import 'vant/lib/index.css'
Vue.use(Vant)
```
<a name="9cZYJ"></a>
### 移动端REM适配 lib-flexible + postcss-pxtorem
Vant 中的样式默认使用 px 作为单位，如果需要使用 rem 单位，推荐使用以下两个工具：

- lib-flexible 用于设置 rem 基准值
- postcss-pxtorem 是一款 postcss 插件，用于将单位转化为 rem

一、安装：npm i amfe-flexible   引入进main.js：import 'amfe-flexible'(动态设置 REM 基准值（html 标签的字体大小,font-size为十分之一)<br />二、postcss插件是一个平台，与已有的构建工具进行集成。使用 postcss-pxtorem 将 px 转为 rem,该插件**不能转换行内样式**中的 px<br />->npm install postcss-pxtorem -D<br />->然后在项目根目录中创建 .postcssrc.js 文件
```javascript
module.exports = {
  plugins: {
    'autoprefixer': {
      browsers: ['Android >= 4.0', 'iOS >= 8']
    },
    'postcss-pxtorem': {
      rootValue ({ file }) {
        return file.indexOf('vant') !== -1 ? 37.5 : 75
      },
      propList: ['*']
    }
  }
}
```
<a name="CQAih"></a>
### 封装请求模块
-> npm i axios<br />->在src/utils/request.js文件中,我们把每一个请求都封装成每个独立的功能函数，在需要的时候加载调用，这种做法更便于接口的管理和维护
```javascript
/**
 * 封装 axios 请求模块
 */
import axios from "axios"
const request = axios.create({
  baseURL: "http://ttapi.research.itcast.cn/" // 基础路径
})
export default request
```
<a name="MtQ1H"></a>
### 创建登录页面
创建 src/views/login/index.vue <br />然后在 src/router/index.js 中配置登录页的路由表(路由懒加载)
```javascript
{
  path: '/login',
  name: 'login',
  component: () => import('@/views/login')
}
```

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

