vue单文件组件：template、script、style，组件中没有el
<a name="hU6aC"></a>
### 在webpack项目中使用vue
注意：在webpack中使用vue的时候，导入的不是最全的vue，是阉割版的vue，只适用于用render函数来渲染<br />1、运行npm i vue -s<br />2、在src -> index.js入口文件中，通过 import Vue from 'vue' 来导入vue构造函数<br />3、创建vue实例对象，并指定要控制的el区域<br />4、通过render函数渲染App根组件
```javascript
import Vue from 'vue'  
import App from './components/App.vue'

const vm = new Vue({
	el:'#app',   //指定vm实例要控制的页面区域
  render:h=>h(App)  //通过render函数，把指定的组件渲染到el区域中
})
```
<a name="VrW6U"></a>
#### 注册组件的两种方式
1、注册全局组件
```javascript
import 组件名 from './components/某子组件.vue'
Vue.component('my-home',组件名)  //把单文件组件注册为全局组件使用
```
2、组件中导入其他组件，定义为自己的私有组件
```javascript
import 组件名 from './components/某子组件.vue'
components:{        //通过components属性，定义私有组件
	'my-home':组件名
}                     
```
<a name="xMC4l"></a>
### vue-cli脚手架
用于快速生成vue项目基础架构<br />1、安装3.x版本的Vue脚手架,在终端中输入vue -V命令查看脚手架的版本号
```javascript
npm i -g @vue/cli
```
基于3.x版本的脚手架创建vue项目的方法<br />1、vue creat my-project(必须是英文，不能包含特殊字符)<br />2、vue ui
<a name="DVWnJ"></a>
#### 操作步骤
一、创建vue项目 vue creat 项目名称<br />选 Manually select features （自定义勾选配置）<br />->选分别选择：Babel：es6 转 es5Router：路由Vuex：数据容器，存储共享数据CSS Pre-processors：CSS 预处理器，后面会提示你选择 less、sass、stylus 等Linter / Formatter：代码格式校验<br />->选是否使用 history 路由模式，这里输入 n 不使用<br />->选择 CSS 预处理器，这里选择我们熟悉的 Less<br />->选择校验工具，这里选择 ESLint + Standard config<br />->选择在什么时机下触发代码格式校验：

- Lint on save：每当保存文件的时候<br />
- Lint and fix on commit：每当执行 git commit 提交的时候<br />

这里建议两个都选上，更严谨。<br />->Babel、ESLint 等工具会有一些额外的配置文件，这里的意思是问你将这些工具相关的配置文件写到哪里,这里建议选择第 1 个，保存到单独的配置文件，这样方便我们做自定义配置。<br />->npm run serve命令将项目跑起来
<a name="JbbW5"></a>
#### vue脚手架的自定义配置
通过单独的配置文件配置vue.config.js（推荐，易维护）
```javascript
module.exports = {
	devServer: {
  	port:8888,   //配置端口号
    open:true   //是否自动打开
  }
}
```
