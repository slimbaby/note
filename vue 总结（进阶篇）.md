<a name="98x4W"></a>
# 1. 路由篇
```javascript
import Vue from 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)

const routes = [
]

const router = new VueRouter({
  routes
})

export default router
```
<a name="Pu9HV"></a>
## 1.1  各种写法
<a name="hOFwz"></a>
### 1.1.1 组件导入写法
```javascript
import Home from '../views/Home.vue'
//path  指定路径，component  指定展示的组件
const routes = [
   {
    path: '/',
    component: Home
  }
]
```
<a name="AM4DR"></a>
### 1.1.2 路由懒加载
```javascript
const routes = [
   {
    path: '/parent',
    component: ()=> import('@/views/parent.vue'),
  }
]	
```
<a name="s2LVw"></a>
### 1.1.3 动态路由匹配
```javascript
//第一种  路由中
const routes = [
  {
    // 动态路由匹配
    path: '/argu/:name',
    component: ()=> import('@/views/argu.vue')
  }
]	

//组件中
<template>
  <div>
    路由动态匹配{{ $route.params.name }}
  </div>
</template>

```


<a name="NFBYG"></a>
### 1.1.4 命名路由
```javascript
const routes = [
  {
    path: '/about',
    name: 'About',  //命名路由
    component: () => import('@/views/About.vue')
  },
]	

//组件中
<template>
  <div id="app">
    <div id="nav">
      <!-- 命名路由  to 要变成属性绑定的形式， 属性是一个对象 -->
      <router-link :to="{ name: 'About' }">About</router-link>
    </div>
    <router-view/>
  </div>
</template>
```
<a name="Ddds8"></a>
### 1.1.5 命名视图
```javascript
<template>
  <div id="app">
    <router-view/>
    <!-- 如果想在一个页面上显示不同的视图，而且让指定的视图显示在指定的位置 ,那就要用到命名视图-->
    <router-view name="email"/>
    <router-view name="tel"/>
  </div>
</template>


const routes = [
  {
    // 命名视图
    path: '/named_view',
    props: true,
    //注意 这里要带 s 因为有多个
    components: {
      //没有指定名字显示 default 指定的 指定了的话展示各自对应的
      default: ()=> import('@/views/child'),
      email: ()=> import('@/views/email.vue'),
      tel: ()=> import('@/views/tel.vue')
    }
  },
]	

```
效果如下三个被路由匹配的组件都被展示出来<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616558792197-f4896d7c-b6ba-4342-9837-e61015f640a2.png#align=left&display=inline&height=233&margin=%5Bobject%20Object%5D&name=image.png&originHeight=465&originWidth=440&size=25498&status=done&style=none&width=220)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616558857470-9d381ec0-8718-4d6b-b21b-b27a33dba165.png#align=left&display=inline&height=88&margin=%5Bobject%20Object%5D&name=image.png&originHeight=175&originWidth=353&size=8414&status=done&style=none&width=176.5)
<a name="8Obv3"></a>
### 
<a name="dO52x"></a>
### 1.1.6 重定向 （三种写法）
```javascript
  // 重定向 (第一种写法)
  {
    path: '/main', redirect: '/'
  }
```
或者这么写
```javascript
    // 重定向 (第二种写法)
	{
    path: '/main', redirect: {
      name: 'Home'  //相当于是 :to 后面跟对象指定跳转地址的方法
    }
  }
```
```javascript
  // 重定向 (第三种写法)
  {
    path: '/main', redirect: to => {
      return '/'
    }
  }
	//根据箭头函数的定义还可以简写成
  {
    path: '/main', redirect: to => '/'
  }
```
<a name="1HOhC"></a>
### 1.1.7 嵌套路由
```javascript
//默认子路由
const routes = [
  {
    path: '/',
    component: Layout,
    children: [{
      path: '',
      name: 'Home',
      component: () => import('@/views/Home')
    }]
  },
]	

// home前置页面
const routes = [
  {
    path: '/',
    component: Layout,
    redirect: '/home',
    children: [{
      path: 'home',
      name: 'Home',
      component: () => import('@/views/Home')
    }]
  },
]	


```
<a name="11en0"></a>
### 1.1.8 别名
```javascript
const routes = [
  {
    path: '/',
    //使用alias 取别名，这样访问 /home_page 直接访问'/' ，是一样的
    alias: '/home_page',
    name: 'Home',
    component: Home
  }
]
```
<a name="sQKa8"></a>
### 1.1.9 编程式导航（重点！!各种写法）（通过 this.$router 访问到路由实例）
```javascript
    handleClick () {
      
      // 后退一页
      this.$router.go(-1)
      // 前进一页
      this.$router.go(1)
      // 返回
      this.$router.back()
      // 跳转到指定页面 (写法1)
      this.$router.push('/named_view')
      // 跳转到指定页面 (写法2)
      this.$router.push({
        name: 'named'
      })
      //可以携带参数: 效果在代码结束后面
      this.$router.push({
        name: 'argu',
        query:{
          name: 'aaa'
        }
      })
      //使用params 或者直接使用path 然后用模板字符串拼接: 效果在代码结束后面
      this.$router.push({
        name: `argu`
        params: {
      		name: 'lwq'
      	}
      }
      //使用params 另一种写法                
      const name = 'lwq'
      this.$router.push({
        path: `/argu/${name}`,
      }
      //重定向（写法1）
      this.$router.replace('/named_view')
      //重定向（写法2）
      this.$router.replace({
        name: 'named'
      })
    }
```
携带参数的效果: 使用 query ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616560757073-668bc304-2f12-47da-96fe-574985a156cc.png#align=left&display=inline&height=23&margin=%5Bobject%20Object%5D&name=image.png&originHeight=45&originWidth=228&size=1646&status=done&style=none&width=114)<br />使用params ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616561182927-77e1fb9b-2300-47d8-8703-a57710ff777d.png#align=left&display=inline&height=27&margin=%5Bobject%20Object%5D&name=image.png&originHeight=53&originWidth=205&size=2572&status=done&style=none&width=102.5)
<a name="10Uc5"></a>
## 1.2 路由进阶篇
<a name="BinER"></a>
### 1.2.1路由传参 的几种模式
```javascript
const routes = [
  {
    path: '/argu/:name',
    name: 'argu',
    //路由这边先 props: true, 开始传参 和父子组件传参一样 然后 组件那边接收
    props: true,
    component: ()=> import('@/views/argu.vue')
  }
]
	//组件为中  先使用props  指定要接受的内容  第一种写法 对象的形式
   props: {
    name: {
      可以指定接收的类型， 和没有传参默认显示的内容
      type: [String, Number],
      default: 'lwq'
    }
   }

  //第二种 数组的写法
	//props: ['name'],

  //然后直接就可以渲染出来
<template>
  <div>
   	路由传参拿到的name 值：{{name}}
  </div>
</template>
```
```javascript
  //还可以直接指定携带参数     路由中
	{
    path: '/about',
    name: 'About', 
    component: () => import('@/views/About.vue'),
    props: route => {
      food: route.query.food
    }
  },

  //组件中可以指定下类型和默认值
	props:{
    food:{
      type: String,
      default: "apple"
    }
  }
```


<a name="fgNow"></a>
### 1.2.2 路由导航守卫
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616563523430-85c727c8-4a17-439f-9778-4b4d371530ba.png#align=left&display=inline&height=290&margin=%5Bobject%20Object%5D&name=image.png&originHeight=409&originWidth=816&size=300431&status=done&style=none&width=579)
```javascript
	组件内的守卫：
	针对组件进行拦截
	beforeRouteEnter (to, from, next) {
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
    next()
  },
  beforeRouteUpdate (to, from, next) {
    // 在当前路由改变，但是该组件被复用时调用
    // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
    // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave (to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
    console.log('即将离开about')
    if(confirm('当前表单没有提交？确定要离开首页？')){
      next()
    }
  }

// 挂载路由导航守卫  设置拦截 如果没有token  的话强制跳转回去 login
router.beforeEach((to, from, next) => {
    // to 代表将要访问的路径
    // from 表示从哪个路径跳转而来
    // next()  放行
    // next('./login') 强制跳转到login
    if (to.path === "/login") return next();
    // 获取 token
    const tokenStr = window.sessionStorage.getItem("token");
    //   如果没有登录强制跳转回login
    if (!tokenStr) return next("login");
    next();
});


```
<a name="UjHz7"></a>
### 1.2.3 历史路由待完善

<br />


---

<a name="E5TXA"></a>
# 2.Vuex  篇
<a name="zDnI8"></a>
## 2.1 先提一下 组件传值（并整理父子组件和兄弟组件的传参）
重点提要：

1.   ！！单向数据流： 父组件向子组件传值， 一定是通过 属性，子组件通过props 接收
1.  而子组件如果要修改父组件传过来的值，一是通过事件的方式，通过emit触发并把需要修改的值以参数的形式传递过去    （详情看例子1）

然后父组件绑定一个事件来知道子组件要改值，然后再子组件里面修改值<br />3.兄弟组件  （ 详情看例子 2）（下一篇完善）<br />例子1：<br />Ainput.vue 组件中
```javascript
// 为了区分自己封装组件最好有统一的前缀
<template>
  <input @input='handleInput' :value="val">
</template>
<script>
export default {
  name: "Ainput",
  components: {},
  props: {
    value: {
      type: [String, Number],
      default: ''
    }
  },
  data() {
    return {
      val: ''
    };
  },
  methods: {
    handleInput(event) {
      const value = event.target.value
      this.$emit('input', value)
    }
  },
}
</script>

<style scoped lang="less">

</style>

```
store.vue  中
```javascript
<template>
  <div>
    <a-input v-model="inputValue" />
    <h1>{{inputValue}}</h1>
  </div>
</template>

<script>
 // _c   这里是配置文件中配置的  相当于 src/components
import AInput from '_c/Ainput.vue'
export default {
  name: "store",
  components: {
    AInput
  },
  props: {},
  data() {
    return {
      inputValue: ''
    };
  },
}
</script>

<style scoped lang="less">

</style>

```


<a name="5kOkC"></a>
#### 2.1.1 分析
先整体分析   先Ainput 组件中书写了一个文本框，然后  给他绑定了输入事件，触发了 函数，展示的数据是数据绑定的 val， 然后 在store  ，显示导入了Ainput 这个组件 然后注册组件，在页面 显示他，     最后在双向数据绑定这个属性就可以了 <br />
<br />核心逻辑分析 ： 为什么直接  双向数据绑定就可以达成效果，<br />为什么可以直接出现效果：  是因为  v-model  相当于   :value='inputValue' @input='handleInput'   相当于属性绑定加上一个输入事件  ， 然后事件里面，<br />handleInput（val）{this.inputValue=val}  函数里面有将我们传输过来的val  ，赋值给我们定义的 inputValue  。

例子2 :<br />store.vue 中
```javascript
<template>
  <div>
    
    <a-input @input="handleInput"/>
    <a-show :content="inputValue"/>
    <!-- <h1>{{inputValue}}</h1> -->
  </div>
</template>

<script>
import AShow from '_c/Ashow.vue'
import AInput from '_c/Ainput.vue'
// import { mapState, mapMutations, mapActions, mapGetters } from 'vuex'
export default {
  name: "store",
  components: {
    AInput,
    AShow
  },
  props: {},
  data() {
    return {
      inputValue: ''
    };
  },
  methods: {
    handleInput(val){
      this.inputValue = val
    }
  }
}
</script>

<style scoped lang="less">

</style>

```

<br />Ashow 中<br />

```javascript
<template>
  <div>
    {{ content }}
  </div>
</template>

<script>
export default {
  name: "Ashow",
  components: {},
  props: {
    content: {
      type: [String, Number],
      default: ''
    }
  },
  data() {
    return {};
  },
}
</script>

<style scoped lang="less">

</style>

```
<a name="IJ9gH"></a>
## 2.2  bus 的使用 （作为交互的中介）

1. 创建一个 bus 文件夹  然后里面创建一个index .js  书写如下代码
```javascript
import Vue from 'vue'
const Bus = new Vue()
export default Bus
```

2. main.js 中书写
```javascript
//导入文件并 将其挂到vue原型上
import Bus from './bus'
Vue.prototype.$Bus = Bus
```
```javascript
//从打印中可以得只相当于 创建一个空的vue 实例 作为交互的中介
 console.log(this.$Bus)
```

<br />tel.vue 中
```javascript
<template>
  <div class="tel">
   <p> {{message}}</p>
  </div>
</template>

<script>
export default {
  name: "tel",
  data() {
    return {
      message: ''
    };
  },
  mounted() {
    this.$bus.$on('on-click', mes => {
      this.message = mes
    })
  }
}
</script>

<style scoped lang="less">
.tel {
  border: 1px solid red;
}
</style>

```
emali.vue 中
```javascript
<template>
  <div class="email">
    <button @click="handleClick">按钮</button>
  </div>
</template>

<script>
export default {
  name: "email",
  data() {
    return {};
  },
  methods: {
    handleClick() {
      this.$bus.$emit('on-click','hello')
    }
  },
}
</script>

<style scoped lang="less">
.email {
  border: 1px solid green;
}
</style>

```


<a name="FyCga"></a>
#### 2.1.1 原理： emit 可以触发当前实例上的一些事件，$on 是给当前实例绑定一个事件监听，然后事件是绑定在this.$bus 上, 所以在this.$bus 上在监听这个事件这样就形成了响应


<a name="tGoJJ"></a>
## 2.3 Vuex 基础
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616637823251-a841068b-5fb2-4297-8a8d-d52b2619c43a.png#align=left&display=inline&height=308&margin=%5Bobject%20Object%5D&name=image.png&originHeight=615&originWidth=795&size=134316&status=done&style=none&width=397.5)<br />先分析图片流程：  组件触发actions  做接口的请求等异步，请求后可以触发mutations， 然后通过mutations 去修改state 的状态值，然后state修改后，  触发组件里视图的渲染<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616638289995-a5de81ff-e2c9-4150-a513-c96c4e07864d.png#align=left&display=inline&height=281&margin=%5Bobject%20Object%5D&name=image.png&originHeight=562&originWidth=551&size=54999&status=done&style=none&width=275.5)

<a name="DXXPe"></a>
### 2.3.1 state  和组件拿到状态的各种方法
```javascript
//state.js 中
const state = {
  appName: 'admin'
}

export default state
```
<a name="juA3W"></a>
#### 2.3.1.1 组件中获取的各种方式
<a name="nqdqU"></a>
#### 第一种：通过$store 访问
```javascript
   //直接获取
		<p>{{ $store.state.appName }}</p>

	//或者在计算属性中
  computed: {
    appName(){
      return this.$store.state.appName
    }
  },
  //然后直接拿计算属性中属性
    	<p>{{ appName }}</p>
  //写在user.js 模块中  在state加上模块的名字
     userName(){
      return this.$store.state.user.userName
    }
```
<a name="zvmiN"></a>
#### 第二种 ： 使用工具函数  mapState 写法：  import { mapState } from 'vuex'  利用了解构赋值
```javascript
import { mapState } from 'vuex'
//相当于:
import vuex from 'vuex'
const mapState = vuex.mapState
```
在计算属性中使用展开运算符 ...  映射到当前组件
```javascript
//使用...  将数据扁平化，映射到当前组件，会有命名冲突的问题！！
//（传数组的写法如下）
	computed: {
    ...mapState([
      'appName'
    ])
  }
//mapState 最后会返回会是一个对象 , ... 展开运算符，会把对象的数据扁平化

		//然后就可以直接使用了
    <p>{{ appName }}</p>

//也可以传对象（传对象的写法如下）
	computed: {
    ...mapState({
      appName: state => state.appName,
      //模块中的
      userName: state => state.user.userName
    })
  }
```
<a name="0ujrF"></a>
#### 2.3.1.2 开启命名空间  模块中  添加   namespace: true,   然后使用createNamespacedHelpers
```javascript
 	//使用createNamespacedHelpers
	import { createNamespacedHelpers } from 'vuex'
	const { mapState } = createNamespacedHelpers('user')
	computed: {
    ...mapState({
      userName: state => state.userName
    })
  }
```
<a name="78XbG"></a>
#### 2.3.1.2 如果想要直接 使用 mapState  完成这种效果  需要在对象传入模块名  或者使用路径写法，mutation 之后在说不太喜欢这种模式，可读性较差每次都要this.[路径] 不方便阅读
```javascript
	computed: {
    ...mapState('user', {
      userName: state => state.userName
    })
  }
```
<a name="xyMwY"></a>
### 2.3.2 getters 
**getters.js 中**
```javascript
const getters = {
  // 传入state  代表同级别state
  appNameWithVersion: (state)=>{
    return `${state.appName}v2.0`
  }
}

export default getters
```
```javascript
//在组件计算属性中
computed: { 
	appNameWithVersion(){
      //直接访问
      return this.$store.getters.appNameWithVersion
    }
}
//展示出来
<p>{{ appNameWithVersion }}</p>

//然后如果state的appName修改就会触发 getters，getters 相当于是全局的计算属性， computed 是局部的计算属性

```
当然也有 工具辅助函数  mapGetters
```javascript
    ...mapGetters([
      'appNameWithVersion'
    ])

		//展示出来
		<p>{{ appNameWithVersion }}</p>
```
```javascript
    //模块中的引用
		...mapGetters('user', [
      'firstLetter'
    ])
```


<a name="vITm6"></a>
###  2.3.3 mutations 
<a name="9b345e2d"></a>
#### 2.3.3.1 先提一下自定义属性
```javascript
  computed: {
    appName () {
      return this.$store.state.appName
    }
  },
    
  methods: {
		handleChangeAppName(){
      // 不能直接这样修改  因为计算属性默认只有getter
      this.appName = 'newAppName'
    }
  }

```
会提示计算属性被定义但是他没有settes<br />因为计算属性默认只有getter，读取计算属性的时候会调用getter，设置的时候会调用 setter所有会报错

拓展 可以这么写: （不用在意）
```javascript
    appName: {
      set: function(newValue){
        this.inputValue = newValue + 'sd'
      },
      get: function(){
        return this.inputValue + 'sdfsdf'
      }
    }
```


<a name="M4Nkl"></a>
#### 2.3.3.2 单值写法和后面参数是对象的写法


```javascript
//组件中 

//结构中
<template>
  <div>
    <h1>{{appName}}</h1>
    <button @click="handleChangeAppName">修改state 里面的appName</button>
  </div>
</template>

	//计算属性中
	computed: {
    appName () {
      return this.$store.state.appName
    }
  },
  //方法中
  methods: {
		handleChangeAppName(){
      // 第一个参数就是方法名， 第二个就是要传递的参数  ，也可以直接传对象过去, 多值写法后面再写
      this.$store.commit('SET_APP_NAME'， 'newAppName')
      //对象写法
      //this.$store.commit('SET_APP_NAME', {
      // appName: 'newAppName',
      //})
    }
  }
    

//mutations.js 中
const mutations = {
  // 第一个参数就是同级的state， 第二个参数是载荷其实就是参数
  SET_APP_NAME (state, params) {
    // 如果是单个值直接 = params 如果是多个需要是对象， 当然也可以直接传对象过来
    state.appName = parmas
    //传的是对象的话 只改变某一项
    //state.appName = params.appName
  }
}

export default mutations	

```
<a name="uxvGa"></a>
#### 2.3.3.3 纯对象写法：  直接传递一整个对象
```javascript
    handleChangeAppName(){
      // type 指定方法名， appName 是参数
      this.$store.commit({
        type: 'SET_APP_NAME',
        appName: 'newAppName',
      })
```
<a name="HyLSF"></a>
#### 2.3.3.4 给state 添加一个 版本号的信息   使用vue 身上的set方法（后面解释为什么要用set）
```javascript
//导入 vue
import Vue from 'vue'
const mutations = {
  // 第一个参数就是同级的state， 第二个参数是载荷其实就是参数
  SET_APP_NAME (state, params) {
    state.appName = params.appName
  },
  //定义一个SET_APP_VERSION 方法
  SET_APP_VERSION (state) {
    Vue.set(state, 'appVersion', 'v2.0')
    // 错误的 会发现没有更新视图
    state.appVersion = 'v2.0'
  }
}	
```
为什么要使用 set，使用 tate.appVersion = 'v2.0' 会发现没有更新视图，

根据vue响应式原则： 在创建state实例初期，定义的状态， 通过mutattions 修改 ，<br />他会触发视图的更新，但是如果一开始没有， 在创建实例的时候不会添加set ， get方法就不会触发视图的更新<br />所以使用set方法把新的值添加到state上，并且会添加上set ，get方法，这样就会触发视图的更新

<a name="H5OED"></a>
#### 2.3.3.5 使用mapmutations 工具辅助函数
```javascript
  methods: {
    //映射到当前组件
    ...mapMutations(['SET_APP_NAME']),
    //就可以直接用this使用
		this.SET_APP_NAME('newAppName')
  }


//对象的写法
  methods: {
    ...mapMutations(['SET_APP_NAME']),
		  this.SET_APP_NAME({
        appName: 'newAppName',
      })
  }
//mutations.js 里面获取的方式记得改
  SET_APP_NAME (state, params) {
    state.appName = params
  },
    
   SET_APP_NAME (state, params) {
    // 对象
    state.appName = params.appName
  },
```


<a name="c1erZ"></a>
#### 2.3.4.6 还可以路径写法， 如果是拆分细模块且模块相互对应不推荐这样写每次 都this后面带路径 ，还是传入模块名或者使用命名空间辅助函数  
```javascript
methods: {
    ...mapmutations(['user/setUserName'])
}
//调用要这样写   模块我们进行了namespaced: true，所以引用mapmutations时需要带上 user/, 并且在使用该方法时，直接使用 this['user/setUserName']
this['user/setUserName'](this.UserName)
也可以直接触发 使用 $store 上的 dispatch 方法 
```


<a name="bCdEl"></a>
#### 2.3.3.6 模块中的话  开启和不开启命名空间的情况下（有注意点）
<a name="4VO9N"></a>
####  不开启命名空间的情况下,可以不用书写模块名，因为vuex 会把mutations 和 actions 和getters 和根级别的全部注册到当前
```javascript
    	//不开启命名空间的情况下,可以不用书写模块名，因为vuex 会把mutations 和 actions 和getters 和根级别的全部注册到当前
			...mapMutations([
      'SET_APP_NAME',
      'SET_APP_USERNAME'
      ]),
      //开启命名空间的情况下， 必须要用， 传入模块的方式，使用 命名空间辅助函数或者路径写法（懒得写了跳过）
      ...mapMutations('user',[
      'SET_APP_NAME',
      'SET_APP_USERNAME'
      ]),
```
<a name="307gy"></a>
### 2.3.4  actions  做异步操作 然后触发mutations   之后修改state 里面的数据    


<a name="zLbN1"></a>
#### 1.   在src 的api文件夹下创建 app.js，模拟请求 代码如下
```javascript
export const getAppName = ()=> {
  return new Promise((resolve, reject) => {
    const err = null
    setTimeout(() => {
      if (!err) resolve({ code: 200, info:{ appName: 'newAppName' }})
        else reject(err)
    }, timeout);
  })
}
```
<a name="5wze2"></a>
#### 2.   actions.js  中 把方法引用过来，并创建自己的方法
```javascript
// action 做异步操作  不能直接在 mutaitons  做异步任务
import { getAppName } from '@/api/app'
const actions = {
  
  //注意参数是对象形式 ，commit是用于提交一个mutations。 当然不只有commit这一种，
  //commit 提交一个mutations,  state 指代当前state实例， rootState代表根级别的state, 
  //dispatch  触发acitons，如果同级还有一个actions 用 dispatch('xxx','xxx')  后面继续深入
  
  updateAppName ({ commit }) {
    getAppName().then(res => {
      console.log(res)
      //commit 触发mutations的方法和对应的属性并传递参数
      commit('SET_APP_NAME', res.info.appName)
      //利用解构赋值也可以写成
     const { info: { appName }} = res
      commit('SET_APP_NAME', appName)
    }).catch(err => console.log(err))
  }
}

export default actions
```
```javascript
// action 做异步操作  不能直接在 mutaitons  做异步任务
import { getAppName } from '@/api/app'
const actions = {
  //使用async 和 await 优化
  async updateAppName({ commit }) {
    try {
      const { info: { appName }} = await getAppName()
      commit('SET_APP_NAME', appName)
    } catch (error) {
      console.log(error)
    }
  }
}

export default actions
```
<a name="eG2OA"></a>
#### 3.   store.vue 中使用辅助函数把actions 的方法映射到当前, 然后点击的时候触发
```javascript
  methods: {
     ...mapActions([
        'updateAppName'
     ]),
    //在点击事件的时候触发
    handleChangeAppName(){
      this.updateAppName()
    },
  }
```
<a name="bt9nP"></a>
#### 4. 开启命名空间后的路径写法 （ 不太推荐 ）
```javascript
methods: {
    ...mapActions(['user/login'])
}
//调用要这样写   模块我们进行了namespaced: true，所以引用aciton时需要带上 user/, 并且在使用该方法时，直接使用 *this['user/login'] , 使用this.user/login 语法是错误的
await this['user/login'](this.loginForm)
也可以直接触发 使用 $store 上的 dispatch 方法
```
<a name="mhP6d"></a>
#### 5. 直接使用 $store 身上的dispatch 方法
```javascript
this.$store.dispatch('需要触发的action函数',需要传递的参数)
```
效果如下  ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616808406678-f2e30fdb-da2f-4747-8390-ff0c7be376cb.png#align=left&display=inline&height=68&margin=%5Bobject%20Object%5D&name=image.png&originHeight=136&originWidth=692&size=9775&status=done&style=none&width=346)![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616809313905-2485f76f-1e9c-4be0-863d-fb1e3b498b85.png#align=left&display=inline&height=16&margin=%5Bobject%20Object%5D&name=image.png&originHeight=31&originWidth=170&size=2111&status=done&style=none&width=85)变成![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616809329611-81fafbea-3478-4233-bbc6-c8772fc0c46f.png#align=left&display=inline&height=13&margin=%5Bobject%20Object%5D&name=image.png&originHeight=25&originWidth=187&size=2391&status=done&style=none&width=93.5)<br />逻辑分析：app.js中封装了异步方法， actions 把方法导入， 进行正确和错误的处理，正确的话使用commit 触发mutations 里面的SET_APP_NAME方法，并传入参数,  stor.vue 中使用了辅助函数把方法映射到当前，点击的时候触发<br />
<br />
<br />不在赘述写在模块里上面提到： 不开启命名空间的情况下,可以不用书写模块名，因为vuex 会把mutations 和 actions 和getters 和根级别的全部注册到当前。<br />

<a name="8Wkvp"></a>
### 2.3.5 module  模块
当应用变得非常复杂时，store 对象就有可能变得相当臃肿。Vuex 允许我们将 store 分割成**模块（module）**。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割
```javascript
// 如果模块再嵌套模块, 并开启命名空间的话，怎么使用方法  实例：
// 模块名/下一级模块名
...mapActions('user/next', [
  'updateAppName'
]}
```
<a name="oO6TC"></a>
#### _动态注册模块  (先写一个 普通版本的  后面书写一个  在模块中的)_
```javascript
    <button @click="regiterModule">动态注册模块</button>
    <p v-for="(li, index) in todoList" :key="index">{{ li }}</p>
		// 计算属性中
   ...mapState({
      todoList: (state) => (state.todo ? state.todo.todoList : []),
    }),
     // 触发的方法中
     regiterModule() {
      this.$store.registerModule("todo", {
        state: {todoList: ["学习mutations","学习actions"]},
      })
```
<a name="0GWW6"></a>
#### _在模块中的_
```javascript
    <button @click="regiterModule">动态注册模块</button>
    <p v-for="(li, index) in todoList" :key="index">{{ li }}</p>
		// 计算属性中
   ...mapState({
     	//改成访问  state.user.todo 
       todoList: (state) => (state.user.todo ? state.user.todo.todoList : []),
    }),
     // 触发的方法中
     regiterModule() {
      this.$store.registerModule(['user', 'todo'], {
        state: {todoList: ["学习mutations","学习actions"]},
      })
```

<br />我们调用的是Vuex中子模块的action，该模块我们进行了namespaced: true，所以引用aciton时需要带上**`user/`**, 并且在使用该方法时，直接使用 **`this['user/login']`**, 使用this.user/login 语法是错误的
<a name="VN98p"></a>
## 总结
**vuex  五种状态   State , Getters, Mutations , Actions , Modules**<br />**辅助函数： mapState、mapActions、mapMutations，mapGetters  ，createNamespacedHelpers （命名空间辅助函数）**<br />**<br />**{ commit, state, rootState, dispatch }  ： commit 提交一个mutations,  state 指代当前state实例， rootState代表根级别的state, dispatch  触发acitons，如果同级还有一个actions 用 dispatch('xxx','xxx')**
```javascript
const actions = {
  updateAppName ( { commit, state, rootState, dispatch } ) {
  }
}
```

<br />**state => 基本数据 **<br />**getters => 从基本数据派生的数据 **<br />**mutations => 提交更改数据的方法，同步！ **<br />**actions => 像一个装饰器，包裹mutations，使之可以异步。 **<br />**modules => 模块化Vuex**<br />**
<a name="KRn8x"></a>
## 2.4vuex 进阶篇 
制定一个持久化存储的插件，其实就是一个函数 

1. 创建  plugin文件夹 里面创建 saveInLocal.js  然后书写如下代码
```javascript
// 定义一个插件， 其实就是一个函数，只有一个参数就是 store
export default store => {
  // 刷新浏览器 第一次就做的操作写在这里， 使用store.subscribe() 两个参数分别是mutation 和 state
  // 如果有 localStorage.state 这个字段，说明配置过了，怎么替换掉实例中得state 不可以直接store.state = ''这样不行需要使用store提供的replaceState方法
  // 把字符串转换成对象， 替换掉store里面的state
  if (localStorage.state) store.replaceState(JSON.params(locaStorage.state))
  store.subscribe((mutation, state) => {
    // 每次提交mutation 的时候都会触发这里
    // console.log('提交了mutation 修改state');
    // 进行一下本地存储
    localStorage.state = JSON.stringify(state)
  })
}


```
**在store 的跟文件， index.js  中导入 并 加载**
```javascript
import savueLocation from './plugin/saveInLocal'
export default new Vuex.Store({
  state,
  mutations,
  actions,
  getters,
  modules: {
    user
  }, 
  // 加载插件：注意不要漏掉s，  plugins 就是插件的意思  把我们创建的插件放进去，当然要先import 导入它
  plugins: [ saveLocation ]
})
```
<a name="I4QoI"></a>
### 2.4.1 vuex 严格模式 strict: true
```javascript
export default new Vuex.Store({
  //strict 为true开启严格模式， 为false 不开启
  strict: true,
  state,
  mutations,
  actions,
  getters,
  modules: {
    user
  }, 
  plugins: [ saveLocation ]
})

```
在严格模式下，无论何时发生了状态变更且不是由 mutation 函数引起的，将会抛出错误。这能保证所有的状态变更都能被调试工具跟踪到。

~~~~~~跳过  表单处理查阅vuex 文档

<a name="QbF19"></a>
# 3. Ajax 阶段（解决跨域问题，封装axios ， 开发实战中使用）
<a name="Oi3m6"></a>
# 3 .1 解决跨域问题
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1616817127592-dfe6ddcf-ca6e-45ae-a6e0-840d1cdcf80d.png#align=left&display=inline&height=283&margin=%5Bobject%20Object%5D&name=image.png&originHeight=565&originWidth=937&size=267045&status=done&style=none&width=468.5)

1. 在开发中，通常开发的时候配置devServer.proxy，实现请求代理，避免跨域。更具体的可以看webpack的devServer配置。
```javascript
// 在本地开发的时候开启一个开发环境，然后本地启一个node服务， 端口肯定不一样的，
// 同一域名不同端口会出现跨域问题，可以在这里配置一个代理， 会被代理到同一个端口下，
// 相当于是在配置的域下进行的请求，这样就没有跨域问题了
module.exports = {
  devServer: {
    // 配置反向代理  这里配置只是开发环境的跨域，是只存在这个电脑上的， 上线后是部署环境的跨域
    proxy: {
      // 这里的api 表示如果我们的请求地址有/api的时候,就出触发代理机制
      // localhost:8888/api/abc  => 代理给另一个服务器
      // 本地的前端  =》 本地的后端  =》 代理我们向另一个服务器发请求 （行得通）
      // 本地的前端  =》 另外一个服务器发请求 （跨域 行不通）
      // 当我们的本地的请求 有/api的时候，就会代理我们的请求地址向另外一个服务器发出请求
      '/api': {
        target: 'http://adm-java.test.net/', // 跨域请求的地址（按照自己的接口文档来配置这个请求的地址）
        changeOrigin: true // 只有这个值为true的情况下 才表示开启跨域
      }
    }
  },
}
```
如果前端没有设置基础路径会  自动拼接上localhost:8080<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1617335300300-4c4f32c7-6c50-4ca5-b520-b2e29b244b0e.png#align=left&display=inline&height=77&margin=%5Bobject%20Object%5D&name=image.png&originHeight=154&originWidth=772&size=20891&status=done&style=none&width=386)
<a name="H1SUL"></a>
### 2. 后端进行配置
允许访问的域，允许访问的请求头，允许访问的的方法，配置可这三个字段前端就不需要配置代理也可以访问<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12493200/1617346081774-84725656-667f-480f-b379-baaa0695712f.png#align=left&display=inline&height=77&margin=%5Bobject%20Object%5D&name=image.png&originHeight=154&originWidth=941&size=136266&status=done&style=none&width=470.5)
