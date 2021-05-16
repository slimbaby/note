![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617156647256-08fa98b5-b0b0-4170-9c2d-ac553ddd35e7.png#align=left&display=inline&height=344&margin=%5Bobject%20Object%5D&name=image.png&originHeight=344&originWidth=602&size=40420&status=done&style=none&width=602)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1619417533383-a0f9f0a5-b681-4555-9cc8-8c3aab299682.png#align=left&display=inline&height=222&margin=%5Bobject%20Object%5D&name=image.png&originHeight=272&originWidth=724&size=52193&status=done&style=none&width=592)<br />专为 Vue.js 应用程序开发的**状态管理模式**。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1619417656318-87806780-d91a-41ac-8aeb-d31f54f0a287.png#align=left&display=inline&height=404&margin=%5Bobject%20Object%5D&name=image.png&originHeight=404&originWidth=752&size=152453&status=done&style=none&width=752)<br />组件中可以使用  **this.$store** 获取到vuex中的store对象实例，辅助函数和延展运算符要一起用<br />**state:  （**state中数据，定义在组件内的计算属性中**）**<br />获取数据：this.$store.state.xxx<br />辅助函数：mapState<br />延展运算符：...mapState(['xxx'])<br />**mutations:（**mutations的方法导入了methods中**）**<br />mutations是一个对象，对象中存放修改state的方法，同步更新，立即得到新的视图状态<br />方法里参数 第一个参数是当前store的state属性,payload 载荷 运输参数 调用mutaiions的时候 可以传递参数 传递载荷<br />直接调用： this.$store.commit('muations方法名称', 参数)<br />辅助函数：mapMutations<br />延展运算符： ...mapMutations(['同步方法名称'])<br />**actions:（**actions的方法导入了methods中**）**<br />actions内的方法第一个参数是context,表示当前的store的实例，可以通过 context.state 获取状态 也可以通过context.commit 来提交mutations， 也可以 context.diapatch调用其他的action<br />直接调用： this.$store.dispatch('异步方法名称', 参数)<br />辅助函数：mapActions<br />延展运算符： ...mapActions(['异步方法名称'])<br />**getters：（**getters中数据，定义在组件内的计算属性中**）**<br /> // getters函数的第一个参数是 state // 必须要有返回值<br />原始方式：$store.getters.方法名<br />辅助函数：mapGetters<br />延展运算符： ...mapGetters(['计算属性名称'])
```
 getters: {   //根级别的getters
   token: state => state.user.token,
   name: state => state.setting.name
 } 
 **通过mapGetters引用**
 computed: {
       ...mapGetters(['token', 'name'])
 }
```
<a name="BqqA4"></a>
### 模块化中的命名空间
因为所有的模块如果不注册命名空间的话，所有模块下的五大模块都没有区分，都可以直接通过全局的方式调用，为了增加维护性和可读性，建立了命名空间的概念<br />在五大模块同级加一个 namespaced: true,属性<br />调用子模块的五大模块方法<br />方法一：this.$store.dispatch('子模块名称/子模块方法名') // 直接调用方法<br />方法二：辅助函数
```
 methods: {
       ...mapMutations(['user/updateToken']),
       test () {
           this['user/updateToken']()  //需要加()立即执行，不然只是获取了方法
       }
   }
```
方法三： **createNamespacedHelpers**  创建基于某个命名空间辅助函数
```
import { mapGetters, createNamespacedHelpers } from 'vuex'
const { mapMutations } = createNamespacedHelpers('user')
<button @click="updateToken">修改token2</button>
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
<br />
<br />
<br />
<br />

