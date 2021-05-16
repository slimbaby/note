<a name="QzLAa"></a>
## vue 是什么？
•Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架<br />vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合<br />•渐进也可以理解为**提供足够的选择**，并且**没有很多强制性的要求**。使用Vue的时候，并不需要把整个框架的所有东西都用上，可以根据实际情况选择你需要的部分；<br />•vue的体系从内到外依次是**声明式渲染**(Declarative Rendering)、**组件系统**(Component System)、**客户端路由(**Client-side Routing)、**大规模状态管理**(Large Scale State Management)、**构建系统**(Build System)。声明式渲染和组件系统是Vue的核心库所包含内容，而客户端路由、状态管理、构建工具都有专门解决方案。这些解决方案相互独立，你可以在核心的基础上任意选用其他的部件，不一定要全部整合在一起。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614585196908-2f7f7006-41ed-4d51-bf46-097747f0613b.png#align=left&display=inline&height=132&margin=%5Bobject%20Object%5D&name=image.png&originHeight=132&originWidth=554&size=102962&status=done&style=none&width=554)
<a name="1eOtM"></a>
## MVVM
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615516889215-c1c64000-4ea7-4412-b1b4-8de98fe61cb2.png#align=left&display=inline&height=594&margin=%5Bobject%20Object%5D&name=image.png&originHeight=594&originWidth=806&size=550853&status=done&style=none&width=806)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615516947087-c35fe7ee-90f1-4c80-9b23-1b4a02b08a39.png#align=left&display=inline&height=685&margin=%5Bobject%20Object%5D&name=image.png&originHeight=685&originWidth=1720&size=1028907&status=done&style=none&width=1720)<br />
<br />使用Vue将helloworld  渲染到页面上<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614585236761-5e70388a-7732-4690-9956-78e6f274a50d.png#align=left&display=inline&height=414&margin=%5Bobject%20Object%5D&name=image.png&originHeight=414&originWidth=554&size=110789&status=done&style=none&width=554)<br />el:获取需要进行操作的区域；<br />data：存储数据<br />methods: 页面上的行为，比如单机事件或者鼠标事件的处理函数，例如：v-on:click="show"<br />如果methods中不同的方法之间要共享数据，一定要把共享的数据，挂载到data中 
<a name="tiESA"></a>
### Vue.js双向绑定的实现原理 object.defineProperty()数据劫持
 Vue.js 最核心的功能有两个，一是响应式的数据绑定系统，二是组件系统。<br />数据劫持：vue.js采用数据劫持结合发布者- 订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter,getter,在数据变动时发布消息给订阅者，触发相应的监听回调,**vue中的数组没有双向数据绑定**，**对象有**，比如说arr =["a","b","c"]，如果操作arr[0] = "s"不会实现双向数据绑定，但是数组里面的数据是对象，这个也可以实现双向数据绑定。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617279454046-d49407cf-97c0-4a97-91b2-f586c6690c64.png#align=left&display=inline&height=97&margin=%5Bobject%20Object%5D&name=image.png&originHeight=97&originWidth=867&size=153055&status=done&style=none&width=867)<br />数据劫持原理<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617282051448-6916b12e-0a20-4711-8a50-03979251e12d.png#align=left&display=inline&height=383&margin=%5Bobject%20Object%5D&name=image.png&originHeight=383&originWidth=548&size=22562&status=done&style=none&width=548)<br />订阅发布模式的原理<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617281935695-4640cf16-494f-429a-b21c-de10e6513965.png#align=left&display=inline&height=440&margin=%5Bobject%20Object%5D&name=image.png&originHeight=440&originWidth=406&size=28849&status=done&style=none&width=406)

 // Object.defineProperty的缺点:我们原始要代理的对象有多少个属性,我们就要写几次Object.defineProperty,<br />// 并且后面添加的属性不是响应式<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617281836681-76b459f9-d87a-4e91-87fb-c72a589abecd.png#align=left&display=inline&height=252&margin=%5Bobject%20Object%5D&name=image.png&originHeight=252&originWidth=400&size=15603&status=done&style=none&width=400)<br />proxy还可以监听引用的数据类型
<a name="2kFzR"></a>
### 指令
创建vue实例的时候，vue会把这些指令都进行解析，从而根据不同的指令，执行不同的操作，渲染不同的结果<br />•本质就是**自定义属性**<br />•Vue中指定都是以 v- 开头<br />•指令是框架中提供的概念,扩展了HTML的能力<br />指令要生效，必须被vm对象所解析
<a name="pmAIC"></a>
#### {{ }} 
插值表达式  mustache<br />存在闪烁问题<br />1、在指定的位置动态插入内容<br />2、在插值表达式中，只能使用简单的表达式，不能写语句<br />3、插值表达式只能用在元素的内容区域，不能用在元素的属性节点中<br />vue中的指令只有插值表达式是用在内容节点的，其他所有的指令都是用在属性节点。<br />可以在插值表达式中写三元表达式，但不能写for循环类似语句
<a name="Iovsj"></a>
#### v-cloak
•防止页面加载时出现闪烁问题<br />网速比较慢的时候，脚本还没加载完全，导致页面基本样式未改<br />实现原理：在vue脚本未加载完毕的时候，元素样式为不显示，在vue加载完毕的时候，通过实例化对象创造的vue实例把所有vue指令全都清除
```javascript
 <style>
    [v-cloak]{display:none}
  </style>
</head>
<body>
  <div id="bo" v-cloak>
    {{msg}}
  </div>
  <script src="./vue.js"></script>
  <script>
    const vm = new Vue({
      //  el   指定元素 id 是 app 的元素  
      el: '#app',
      //  data  里面存储的是数据
      data: {
        msg: 'Hello Vue'
      }
    })
  </script>
```
<a name="EY9yN"></a>
#### v-text
•	v-text指令用于将数据填充到标签中，作用于插值表达式类似，但是会覆盖原值，但是没有闪动问题<br />•	如果数据中有HTML标签会将html标签一并输出，无法识别html标签<br />•	注意：此处为单向绑定，数据对象上的值改变，插值会发生变化；但是当插值发生变化并不会影响数据对象的值
<a name="zozM4"></a>
#### v-html
•	用法和v-text 相似  但是他可以将HTML片段填充到标签中<br />•	可能有安全问题, 一般只在可信任内容上使用 v-html，**永不**用在用户提交的内容上<br />•	它与v-text区别在于v-text输出的是纯文本，浏览器不会对其再进行html解析，但v-html会将其当html标签解析后输出。
```javascript
<body>
  <div id="app">
    　　<p v-html="html"></p> <!-- 输出：html标签在渲染的时候被解析 -->
        <p>{{message}}</p> <!-- 输出：<span>通过双括号绑定</span> -->
    　　<p v-text="text"></p> <!-- 输出：<span>html标签在渲染的时候被源码输出</span> -->
    </div>
  <script>
    let vm = new Vue({
      el: "#app",
      data: {
       message:"<span>通过双括号绑定</span>",
       html: "<span>标签在渲染的时候被解析</span>",
       text: "<span>标签在渲染的时候被源码输出</span>"
      }
    });
  </script>
</body>
```
<a name="uv6Na"></a>
#### v-pre
显示原始信息，跳过编译过程，比如直接让页面显示{{msg}} <br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615515673068-0d20553c-2dff-4595-8592-a6aa57e9cf7e.png#align=left&display=inline&height=241&margin=%5Bobject%20Object%5D&name=image.png&originHeight=241&originWidth=611&size=68513&status=done&style=none&width=611)
<a name="qBudx"></a>
#### v-once
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615516271903-2dc9daf2-f337-4693-b783-6f580460ae8b.png#align=left&display=inline&height=66&margin=%5Bobject%20Object%5D&name=image.png&originHeight=66&originWidth=420&size=16579&status=done&style=none&width=420)
<a name="yFGSr"></a>
#### v-bind  属性绑定
基本使用：是为html属性节点动态绑定数据<br /><button v-bind:title="titleStr">按钮</button><br />应用场景：如果元素的属性值，需要动态的进行绑定,<br />**注意**：v-bind:class指令可以与普通的class特性共存<br />简写形式：v-bind  指令可以简写成  ：<br /><button :title="titleStr">按钮</button><br />**如果想要按需切换某种样式**，可以为class实现 v-bind属性绑定,v-bind:class指令可以与普通的class特性共存<br />:class="[flag? 'light' : 'dark']"  **(注意引号的使用)**<br /><img :src ="flag? img1:img2"><br /><div v-bind:style="{color:activeColor,fontSize:activeSize}">对象语法</div>
<a name="cRQGz"></a>
##### 绑定class
  v-bind 中支持绑定一个数组    数组中classA和 classB 对应为data中的数据
```javascript
这里的classA  对用data 中的  classA
这里的classB  对用data 中的  classB
<ul class="box" :class="[classA, classB]">
    <li>学习Vue</li>
    <li>学习Node</li>
    <li>学习React</li>
</ul>
<script>
var vm= new Vue({
    el:'.box',
    data:{
        classA:‘textColor‘,
        classB:‘textSize‘
    }
})
</script>
<style>
    .box{
        border:1px dashed #f0f;
    }
    .textColor{
        color:#f00;
        background-color:#eef;
    }
    .textSize{
        font-size:30px;
        font-weight:bold;
    }
</style>
```
**绑定对象和绑定数组 的区别**<br /> v-bind 中支持绑定一个对象  <br />	如果绑定的是一个对象 则 键为 对应的类名  值 为对应data中的数据 
```javascript
1、 v-bind 中支持绑定一个对象 
	如果绑定的是一个对象 则 键为 对应的类名  值 为对应data中的数据 
<!-- 
	HTML最终渲染为 <ul class="box textColor textSize"></ul>
	注意：
		textColor，textSize  对应的渲染到页面上的CSS类名	
		isColor，isSize  对应vue data中的数据  如果为true 则对应的类名 渲染到页面上 


		当 isColor 和 isSize 变化时，class列表将相应的更新，
		例如，将isSize改成false，
		class列表将变为 <ul class="box textColor"></ul>
-->

<ul class="box" v-bind:class="{textColor:isColor, textSize:isSize}">
    <li>学习Vue</li>
    <li>学习Node</li>
    <li>学习React</li>
</ul>
  <div v-bind:style="{color:activeColor,fontSize:activeSize}">对象语法</div>

<sript>
var vm= new Vue({
    el:'.box',
    data:{
        isColor:true,
        isSize:true，
    	activeColor:"red",
        activeSize:"25px",
    }
})
</sript>
```
•	绑定对象的时候 对象的属性是要渲染的类名 ，对象的属性值对应的是 data 中的数据<br />•	绑定数组的时候数组里面存的是data 中的数据
<a name="fNtOX"></a>
#### v-on  ！！引号都加一下  @click=  '事件（参数）'
•	用来绑定事件的<br />•	形式：v-on:click  缩写为 @click;<br />v-on事件函数中传入参数,例如: @click:"show"方法需要传参的时候后面也可以加小括号@click:"show('abc')"<br />只要data数据产生了变化，页面就会重新渲染<br />@click= "fn" 事件对象，默认第一个参数就是事件对象event<br />@click= "fn（$event）"  如果有小括号传参，$event就是事件对象<br />函数体里直接获取event  就是这个事件本身 event.keyCode = xxxx...
```javascript
<div>
     <!-- 如果事件直接绑定函数名称，那么默认会传递事件对象作为事件函数的第一个参数 -->
     <button v-on:click='handle1'>点击1</button>
       <!-- 2、如果事件绑定函数调用，那么事件对象必须作为最后一个参数显示传递，
          并且事件对象的名称必须是$event 
       -->
     <button v-on:click='handle2(123, 456, $event)'>点击2</button>
     </div>
```
<a name="oMoy1"></a>
#### v-model
•	v-model是一个指令，在vue中只有v-model实现了双向数据绑定，其他指令都是单向的<br /><input type = "text" v-model = "msg"><br />v-model只能和表单元素配合使用，例如input select，textarea<br />和v-bind的区别<br />v-bind只能实现单向的数据同步data-->页面<br />v-model  可以实现双向的数据同步 data <-->页面<br />应用场景：自动计算文本框中，字符串的长度<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615517212472-8a0b66e8-5c45-4c34-ad6e-b21b012ff673.png#align=left&display=inline&height=728&margin=%5Bobject%20Object%5D&name=image.png&originHeight=728&originWidth=857&size=245063&status=done&style=none&width=857)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615535430231-ac33ad4f-e857-47ea-a2a9-2b624208e344.png#align=left&display=inline&height=34&margin=%5Bobject%20Object%5D&name=image.png&originHeight=34&originWidth=1164&size=77942&status=done&style=none&width=1164)<br /> <!-- $event普通元素，它指的是事件对象<br />        如果是组件，它可以拿到子组件抛出来的值 --><br />  什么时候用v-model或sync <br />   组件既要使用传进来的值，又要修改值的时候<br />    v-model用于表单型组件 el-input<br />    sync用于非表单型组件 el-dialog<br />   可以混用
```javascript
 <!-- :属性 @update:属性可以简写 -->
        <!-- <el-dialog title="新增用户" :visible="addFormVisible" @update:visible="addFormVisible=$event">
            123
            <div slot="footer">
                <button>取消</button>
                <button>确定</button>
            </div>
        </el-dialog> -->
```
<a name="1mo4F"></a>
#### v-for
循环数组<br />用于循环的数组里面的值可以是对象，也可以是普通元素<br /><li v-for = "(循环的item项，索引) in 数组 "></li><br /> <li v-for="(item,i) in list1">{{item}}</li><br /><li v-for="item in list1">{{item.id }}</li><br />**<li  v-for="item  in list1" ：key="item.id ">{{item.id }}</li>**<br />**今后只要用到了v-for循环，一定要为循环的每一项，添加：key属性绑定**，key绑定到id值上，key的值一定要是唯一，因为这个key是用来标识数据的唯一性的.通过key绑定了数据项和数据状态之间的关系<br />•	key 的作用<br />o	key来给每个节点做一个唯一标识<br />o	key的作用主要是为了高效的更新虚拟DOM

<a name="K0Gpl"></a>
#### v-if 
•	1- 多个元素 通过条件判断展示或者隐藏某个元素。或者多个元素<br />•	2- 进行两个**视图之间的切换**<br />           如果flag为true则显示,false不显示!    
```javascript
<div v-if="type === 'A'">
   A
</div>
<div v-else-if="type === 'B'">
   B
</div>
<div v-else-if="type === 'C'">
   C
</div>
<div v-else>
   Not A/B/C
</div>
```
   <br />•	不推荐同时使用 v-if 和 v-for<br />•	当 v-if 与 v-for 一起使用时，v-for 具有比 v-if 更高的优先级。
```javascript
 <div v-if='v==13' v-for='(v,k,i) in obj'>{{v + '---' + k + '---' + i}}</div>
```
**v-show 和 v-if的区别**<br />•	v-show本质就是标签display设置为none，控制隐藏<br />o	v-show只编译一次，后面其实就是控制css，而v-if不停的销毁和创建，故v-show性能更好一点。<br />•	v-if是动态的向DOM树内添加或者删除DOM元素<br />o	v-if切换有一个局部编译/卸载的过程，切换过程中合适地销毁和重建内部的事件监听和子组件
<a name="Gs4xO"></a>
#### 事件修饰符
•	在事件处理程序中调用 event.preventDefault() 或 event.stopPropagation() 是非常常见的需求。<br />•	Vue 不推荐我们操作DOM    为了解决这个问题，Vue.js 为 v-on 提供了事件修饰符<br />•	修饰符是由点开头的指令后缀来表示的  ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615088444765-1b3e047e-8e60-4f6d-9426-11c137f6b02c.png#align=left&display=inline&height=22&margin=%5Bobject%20Object%5D&name=image.png&originHeight=22&originWidth=366&size=18271&status=done&style=none&width=366)<br />.prevent 阻止默认行为（表单提交，链接跳转等）<br />.once 只触发一次<br />.stop 阻止冒泡   <br />.self 只有在当前元素上触发事件的时候，才会调用处理函数。比如说点击事件冒泡上来不会触发这个元素的点击事件
```javascript
<!-- 修饰符可以串联   即阻止冒泡也阻止默认事件 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>

使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。
```
<a name="ZMlNn"></a>
#### 按键修饰符：都是配合文本输入框使用的
常用的按键修饰符<br />.enter =>    enter键<br />.tab => tab键<br />.delete (捕获“删除”和“退格”按键) =>  删除键<br />.esc => 取消键<br />.space =>  空格键<br />.up =>  上<br />.down =>  下<br />.left =>  左<br />.right =>  右
```javascript
<!-- 只有在 `keyCode` 是 13 时调用 `vm.submit()` -->
<input v-on:keyup.13="submit">

<!-- -当点击enter 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">

<!--当点击enter或者space时  时调用 `vm.alertMe()`   -->
<input type="text" v-on:keyup.enter.space="alertMe" >
```
•在做项目中有时会用到键盘事件，在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 v-on 在监听键盘事件时添加按键修饰符<br />自定义按键修饰符别名<br />•在Vue中可以通过config.keyCodes自定义按键修饰符别名，自定义按键修饰符名字是自定义的，但是后面的值是对应的keycode的值<br />Vue.config.keyCodes.修饰符名字 = 几几几<br />@keyup.修饰符名字 = "方法"
<a name="t14Pg"></a>
### 表单基本操作
<a name="aIX1q"></a>
#### 获取单选框中的值
通过v-model
```javascript
<!-- 
		1、 两个单选框需要同时通过v-model 双向绑定 一个值 
    2、 每一个单选框必须要有value属性  且value 值不能一样 
		3、 当某一个单选框选中的时候 v-model  会将当前的 value值 改变 data 中的 数据
		gender 的值就是选中的值，我们只需要实时监控他的值就可以了
	-->
   <input type="radio" id="male" value="1" v-model='gender'>
   <label for="male">男</label>
   <input type="radio" id="female" value="2" v-model='gender'>
   <label for="female">女</label>
<script>
    new Vue({
         data: {
             // 默认会让当前的 value 值为 2 的单选框选中
                gender: 2,  
            },
    })
</script>
```
<a name="GWWG6"></a>
#### 获取复选框中的值

- 通过v-model<br />
- 和获取单选框中的值一样 <br />
- 复选框 `checkbox` 这种的组合时   data 中的 hobby 我们要定义成数组 否则无法实现多选<br />
```javascript
	<!-- 
		1、 复选框需要同时通过v-model 双向绑定 一个值 
    2、 每一个复选框必须要有value属性  且value 值不能一样 
		3、 当某一个单选框选中的时候 v-model  会将当前的 value值 改变 data 中的 数据
		hobby 的值就是选中的值，我们只需要实时监控他的值就可以了
	-->
<div>
   <span>爱好：</span>
   <input type="checkbox" id="ball" value="1" v-model='hobby'>
   <label for="ball">篮球</label>
   <input type="checkbox" id="sing" value="2" v-model='hobby'>
   <label for="sing">唱歌</label>
   <input type="checkbox" id="code" value="3" v-model='hobby'>
   <label for="code">写代码</label>
 </div>
<script>
    new Vue({
         data: {
                // 默认会让当前的 value 值为 2 和 3 的复选框选中
                hobby: ['2', '3'],
            },
    })
</script>
```
<a name="qXAXT"></a>
#### 获取下拉框和文本框中的值
通过v-model
```javascript
<div>
      <span>职业：</span>
       <!--
			1、 需要给select  通过v-model 双向绑定 一个值 
            2、 每一个option  必须要有value属性  且value 值不能一样 
		    3、 当某一个option选中的时候 v-model  会将当前的 value值 改变 data 中的 数据
		     occupation 的值就是选中的值，我们只需要实时监控他的值就可以了
		-->
       <!-- multiple  多选 -->
      <select v-model='occupation' multiple>
          <option value="0">请选择职业...</option>
          <option value="1">教师</option>
          <option value="2">软件工程师</option>
          <option value="3">律师</option>
      </select>
         <!-- textarea 是 一个双标签   不需要绑定value 属性的  -->
        <textarea v-model='desc'></textarea>
  </div>
<script>
    new Vue({
         data: {
                // 默认会让当前的 value 值为 2 和 3 的下拉框选中
                 occupation: ['2', '3'],
             	 desc: 'nihao'
            },
    })
</script>
```
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617061701505-72c4891b-e0de-47d8-abad-91f2c2aa2175.png#align=left&display=inline&height=681&margin=%5Bobject%20Object%5D&name=image.png&originHeight=681&originWidth=1277&size=75428&status=done&style=none&width=1277)<br />

<a name="r5kAb"></a>
#### 表单修饰符

- .number  转换为数值
   - 注意点：	<br />
   - 当开始输入非数字的字符串时，因为Vue无法将字符串转换成数值<br />
   - 所以属性值将实时更新成相同的字符串。即使后面输入数字，也将被视作字符串。<br />
- .trim  自动过滤用户输入的首尾空白字符
   - 只能去掉首尾的 不能去除中间的空格<br />
- .lazy   将input事件切换成change事件
   - .lazy 修饰符延迟了同步更新属性值的时机。即将原本绑定在 input 事件的同步逻辑转变为绑定在 change 事件上<br />
- 在失去焦点 或者 按下回车键时才更新<br />
```javascript
<!-- 自动将用户的输入值转为数值类型 -->
<input v-model.number="age" type="number">

<!--自动过滤用户输入的首尾空白字符   -->
<input v-model.trim="msg">

<!-- 在“change”时而非“input”时更新 -->
<input v-model.lazy="msg" >
```
<a name="3dRzj"></a>
### **自定义指令**
<a name="Gs6GG"></a>
#### Vue.directive  注册全局指令
```javascript
<!-- 
  使用自定义的指令，只需在对用的元素中，加上'v-'的前缀形成类似于内部指令'v-if'，'v-text'的形式。 
-->
<input type="text" v-focus>
<script>
// 注意点： 
//   1、 在自定义指令中  如果以驼峰命名的方式定义 如  Vue.directive('focusA',function(){}) 
//   2、 在HTML中使用的时候 只能通过 v-focus-a 来使用 
// 注册一个全局自定义指令 v-focus
Vue.directive('focus', {
  	// 当绑定元素插入到 DOM 中。 其中 el为dom元素
  	inserted: function (el) {
    		// 聚焦元素
    		el.focus();
 	}
});
new Vue({
　　el:'#app'
});
</script>
```
<a name="vGtN9"></a>
#### Vue.directive  注册全局指令 带参数  binding
 binding 为自定义的函数形参   通过自定义属性传递过来的值 存在 binding.value 里面
```javascript
 <input type="text" v-color='msg'>
 <script type="text/javascript">
    /*
      自定义指令-带参数
      bind - 只调用一次，在指令第一次绑定到元素上时候调用

    */
    Vue.directive('color', {
      // bind声明周期, 只调用一次，指令第一次绑定到元素时调用。在这里可以进行一次性的初始化设置
      // el 为当前自定义指令的DOM元素  
      // binding 为自定义的函数形参   通过自定义属性传递过来的值 存在 binding.value 里面
      bind: function(el, binding){
        // 根据指令的参数设置背景色
        // console.log(binding.value.color)
        el.style.backgroundColor = binding.value.color;
      }
    });
    var vm = new Vue({
      el: '#app',
      data: {
        msg: {
          color: 'blue'
        }
      }
    });
  </script>
```
<a name="lwVIO"></a>
#### 自定义指令局部指令

- 局部指令，需要定义在  directives 的选项   用法和全局用法一样 <br />
- 局部指令只能在当前组件里面使用<br />
- 当全局指令和局部指令同名时以局部指令为准<br />
```javascript
<input type="text" v-color='msg'>
 <input type="text" v-focus>
 <script type="text/javascript">
    /*
      自定义指令-局部指令
    */
    var vm = new Vue({
      el: '#app',
      data: {
        msg: {
          color: 'red'
        }
      },
   	  //局部指令，需要定义在  directives 的选项
      directives: {
        color: {
          bind: function(el, binding){
            el.style.backgroundColor = binding.value.color;
          }
        },
        focus: {
          inserted: function(el) {
            el.focus();
          }
        }
      }
    });
  </script>
```
<a name="lQzLa"></a>
### 计算属性 computed

- 模板中放入太多的逻辑会让模板过重且难以维护  使用计算属性可以让模板更加的简洁<br />
- **计算属性是基于它们的响应式依赖进行缓存的**<br />
- computed比较适合对多个变量或者对象进行处理后返回一个结果值，也就是数多个变量中的某一个值发生了变化则我们监控的这个值也就会发生变化<br />
```javascript
 <div id="app">
     <!--  
        当多次调用 reverseString  的时候 
        只要里面的 num 值不改变 他会把第一次计算的结果直接返回
		直到data 中的num值改变 计算属性才会重新发生计算
     -->
    <div>{{reverseString}}</div>
    <div>{{reverseString}}</div>
     <!-- 调用methods中的方法的时候  他每次会重新调用 -->
    <div>{{reverseMessage()}}</div>
    <div>{{reverseMessage()}}</div>
  </div>
  <script type="text/javascript">
    /*
      计算属性与方法的区别:计算属性是基于依赖进行缓存的，而方法不缓存
    */
    var vm = new Vue({
      el: '#app',
      data: {
        msg: 'Nihao',
        num: 100
      },
      methods: {
        reverseMessage: function(){
          console.log('methods')
          return this.msg.split('').reverse().join('');
        }
      },
      //computed  属性 定义 和 data 已经 methods 平级 
      computed: {
        //  reverseString   这个是我们自己定义的名字 
        reverseString: function(){
          console.log('computed')
          var total = 0;
          //  当data 中的 num 的值改变的时候  reverseString  会自动发生计算  
          for(var i=0;i<=this.num;i++){
            total += i;
          }
          // 这里一定要有return 否则 调用 reverseString 的 时候无法拿到结果    
          return total;
        }
      }
    });
  </script>
```
<a name="K2fNs"></a>
### **侦听器 watch**

- 使用watch来响应数据的变化<br />
- 一般用于异步或者开销较大的操作<br />
- watch 中的属性 一定是data 中 已经存在的数据 <br />
- **当需要监听一个对象的改变时，普通的watch方法无法监听到对象内部属性的改变，只有data中的数据才能够监听到变化，此时就需要deep属性对对象进行深度监听**<br />
```javascript
 <div id="app">
        <div>
            <span>名：</span>
            <span>
        <input type="text" v-model='firstName'>
      </span>
        </div>
        <div>
            <span>姓：</span>
            <span>
        <input type="text" v-model='lastName'>
      </span>
        </div>
        <div>{{fullName}}</div>
    </div>

  <script type="text/javascript">
        /*侦听器*/
        var vm = new Vue({
            el: '#app',
            data: {
                firstName: 'Jim',
                lastName: 'Green',
                // fullName: 'Jim Green'
            },
             //watch  属性 定义 和 data 已经 methods 平级 
            watch: {
                //   注意：  这里firstName  对应着data 中的 firstName 
                //   当 firstName 值 改变的时候  会自动触发 watch
                firstName: {function(val) {
                    this.fullName = val + ' ' + this.lastName;
                },
                  deep:true/false,
                  immediate:true/false
                 }
                //   注意：  这里 lastName 对应着data 中的 lastName 
                lastName: function(val) {
                    this.fullName = this.firstName + ' ' + val;
                }
            }
        });
    </script>
```
值可以是函数：就是当你监控的家伙变化时，需要执行的函数，这个函数有两个形参，第一个是当前值，第二个是变化后的值。 <br />值也可以是函数名：不过这个函数名要用单引号来包裹。 <br />值是包括选项的对象：选项包括有三个，如下<br />
<br />第一个handler：其值是一个回调函数。即监听到变化时应该执行的函数。<br />第二个是deep：其值是true或false；确认是否深入监听。（一般监听时是不能监听到对象属性值的变化的，数组的值变化可以听到。）<br />第三个是immediate：其值是true或false；确认是否以当前的初始值执行handler的函数。<br />**
<a name="60a5X"></a>
### **过滤器**

- Vue.js允许自定义过滤器 Sun Mar 07 2021 20:45:17 GMT+0800 (中国标准时间) =>2021-03-07

概念：过滤器本质上就是一个函数，可被用作一些常见的文本格式化，

- 过滤器可以用在两个地方：**双花括号插值**和**v-bind表达式**。
- 使用过滤器的时候，管道符前面的值，必须通过function的第一个形参,一般起名：originVal  来接收，最终一定要**return**一个结果
- 过滤器应该被添加在JavaScript表达式的尾部，由“管道”符号指示 ：|   ，可以连续往后dt | a | b | c  调用多个过滤器
- 支持级联操作
- 过滤器不改变真正的data，而只是改变渲染的结果，并返回过滤后的版本：**注意：过滤器，只是对原有的数据做了一层包装，并没有修改原数据的值。**
- 全局注册时是filter，没有s的。而局部过滤器是filters，是有s的
- 过滤器是按照就近原则进行调用的
- 在过滤器的处理函数中，也可以接收参数，但是参数要从形参的第二个位置开始接收  
<a name="pFWRA"></a>
#### 全局过滤器
1、使用全局过滤器的语法  | 代表调用过滤器,每一个vue实例都可以访问这个过滤器<br /><span>{{  dt  | 过滤器的名称  }} </span><br />2、定义全局过滤器的语法<br />Vue.filter("过滤器的名称"，function（ originVal ）{/*originVal是形参， 对数据进行处理的过程，在这个function 中，最后必须return 一个处理结果 */ })**<br />3、使用过滤器的注意事项：<br />  1>
<a name="mIKIy"></a>
#### 私有过滤器
和methods平级，有一个**filters : { } (有sssssss!)**<br />dataFormat : function ( ) { }<br />私有过滤器的名称：私有过滤器的处理函数

<a name="du08u"></a>
### Vue实例.$mount("")方法，（了解）
$mount 方法是挂载的意思，表示手动指定当前vm实例要控制的区域<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615171633879-e8fca18b-96a0-49de-941e-19e569ed4c3d.png#align=left&display=inline&height=331&margin=%5Bobject%20Object%5D&name=image.png&originHeight=475&originWidth=619&size=116542&status=done&style=none&width=431)
<a name="955Uh"></a>
### template属性指定模板
和methods:{ } 平级<br />如果又指定了el,又指定了template,那么template会把el区域UI结构替换为template，template的优先级高
<a name="ZhRwn"></a>
## vue实例的生命周期（Life Cycle）
<a name="cRAhi"></a>
### 什么是生命周期（每个实例的一辈子）
生命周期：实例的生命周期，就是一个阶段，从创建到运行，再到销毁的阶段<br />生命周期函数：在实例创建-运行-销毁的过程中，在特定阶段依次触发的一些特定的事件，这些事件，叫做生命周期函数；<br />生命周期函数=生命周期钩子=生命周期事件<br />**beforeCreate:**<br />data数据和methods方法，尚未初始化，在实际开发中，一般不会在这个函数中做任何事情，因为data和methods都无法正常访问；<br />**created:（重要）**<br />这时的data和methods方法都已经准备好了，我们经常在created生命周期中，通过ajax获取页面的首屏数据。**据我写代码的经验来看：这里面调用的函数在methods中要用promise调用，不然会undefined**<br />**beforeMount:**<br />表示将要挂在，将要把内存中的模板数据，挂载到浏览器中显示，此时，页面上还看不到真实的HTML数据<br />当渲染模板的函数得到编译好后，会立即执行创建阶段的第三个生命周期函数<br />**mounted:（重要）**<br />创建阶段的第四个生命周期，此时，页面已经被首次渲染完成了，如果要操作DOM元素，最好在这个阶段<br />我们想初始化一些第三方js小插件，必须在这里面进行初始化 <br />**beforeUpdate:**<br />此时，data中的数据是最新的，但是页面上渲染的数据，还是旧的数据<br />**updated:**<br />此时，正在根据最新的data数据，重新渲染页面上的结构，当这个操作执行完，data中的数据和页面上展示的数据，都已经是最新的了。页面上的数据已经完成了更新<br />**beforeDestroy:**<br />vm实例即将被销毁，vm实例还能正常工作<br />**destroyed:**<br />vm实例已经被销毁了，就无法正常工作了<br />**文档一共十一个生命周期钩子**，还有三个分别是activated、deactivated、errCaptured,<br />activated: keep-alive 缓存的组件激活时调用（被缓存组件中的axaj请求在这里进行，每次新进页面都重新调用）,该钩子在服务器端渲染期间不被调用，说白了其就是在挂载后和更新前被调用的。但如果该组件中没有使用缓存，也就是没有被<keep-alive>包裹的话，activated是不起作用的<br />deactivated: keep-alive 被 keep-alive 缓存的组件停用时调用（同上）,该钩子在服务器端渲染期间不被调用<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615187015517-9d3c9567-50db-4501-a33e-f7af3f467615.png#align=left&display=inline&height=854&margin=%5Bobject%20Object%5D&name=image.png&originHeight=854&originWidth=364&size=362126&status=done&style=none&width=364)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615636315675-a2ef08ed-380f-4174-8581-c459f3e4b1b0.png#align=left&display=inline&height=407&margin=%5Bobject%20Object%5D&name=image.png&originHeight=407&originWidth=806&size=65206&status=done&style=none&width=806)
<a name="Tcive"></a>
### 数组变异方法

- 在 Vue 中，直接修改对象属性的值无法触发响应式。当你直接修改了对象属性的值，你会发现，只有数据改了，但是页面内容并没有改变<br />
- 变异数组方法即保持数组方法原有功能不变的前提下对其进行功能拓展<br />
- ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615636431539-1ecf4944-b89a-4e49-b48b-9dc3867415d4.png#align=left&display=inline&height=294&margin=%5Bobject%20Object%5D&name=image.png&originHeight=294&originWidth=788&size=38112&status=done&style=none&width=788)
<a name="ZORq4"></a>
### 替换数组

- 不会改变原始数组，但总是返回一个新数组<br />
- ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615636499482-ac08aed9-d92b-48ad-9b11-f0ecc2cfab64.png#align=left&display=inline&height=112&margin=%5Bobject%20Object%5D&name=image.png&originHeight=112&originWidth=797&size=18587&status=done&style=none&width=797)
<a name="7iu6W"></a>
## Vue中的动画
动画可以增加页面的趣味性，目的是为了让用户更好地理解页面的功能，但是vue中的都是简单的过度动画，并不会有CSS3那么炫酷<br />一、每个动画都分为两部分<br />给需要动画的元素绑定属性 v-show = "flag"<br />**1、入场动画**：从不可见（flag = false）->可见（flag = true）<br />**2、离场动可见****：**从可见（flag = true）->不可见（flag = false）<br />二、入场的时候，Vue把这个动画，分成了两个时间点和一个时间段<br />v-enter:入场前的样式<br />v-enter-to:入场完成以后的样式<br />v-enter-active:入场的时间段<br />三、离场的时候，Vue把这个动画，分成了两个时间点和一个时间段<br />v-leave：离场前的样式<br />v-leave-to：离场完成以后的样式<br />v-leave-active：离场的时间段<br />方法：<br />一、把需要添加动画效果的标签用<transition>标签包裹起来<br />二、在style中定义元素入场之前和离场之后的样式<br />三、定义元素入场阶段和离厂阶段的过渡<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615295127627-08b7c6fa-ff33-4e4c-96e9-7ad212f8a6f8.png#align=left&display=inline&height=543&margin=%5Bobject%20Object%5D&name=image.png&originHeight=543&originWidth=955&size=207360&status=done&style=none&width=955)<br />注意：如果页面有多个动画效果，需要将后面的transition  添加name属性 name= "XXX",类名也要用相应的XXX开头，不能重复以  v  开头<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615341152062-9a129606-4323-49f4-9a00-adfdf8bccf98.png#align=left&display=inline&height=124&margin=%5Bobject%20Object%5D&name=image.png&originHeight=124&originWidth=720&size=61821&status=done&style=none&width=720)<br />如果为单个元素添加动画效果，用transition标签，为列表项添加过渡效果要用transition-group标签，tag属性可指定在页面中渲染的标签<br />如：<transition-group tag = "ul"><br />为列表项添加动画效果，key的值一定哟是item.id     用索引值的话不准确。
<a name="mFjzJ"></a>
### 使用第三方CSS动画库
animate.css  <br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615295506612-b427c928-714e-4b69-b5e9-96aedc8a7551.png#align=left&display=inline&height=159&margin=%5Bobject%20Object%5D&name=image.png&originHeight=159&originWidth=861&size=132225&status=done&style=none&width=861) <br />
<a name="DPndf"></a>
## 在webpack中安装和配置vue
第一步：安装vue包<br />第二步：在index.html页面中设置vue控制区域，<div id = "app"></div><br />第三步：在index.js文件中配置vue，引入vue.runtime.js而不是vue.js，只有render的写法才可以<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616159279943-3a4c6fb0-1ecd-4966-aed9-9c7770708b62.png#align=left&display=inline&height=163&margin=%5Bobject%20Object%5D&name=image.png&originHeight=163&originWidth=292&size=7165&status=done&style=none&width=292)<br />第四步、<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615453636023-a6c4df34-bdcb-4c4f-a23e-007fd3217f61.png#align=left&display=inline&height=274&margin=%5Bobject%20Object%5D&name=image.png&originHeight=274&originWidth=843&size=251025&status=done&style=none&width=843)
<a name="ZDFPL"></a>
## 定义Vue组件
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615453755901-13b634ee-e124-462b-92b0-271ddfdc1065.png#align=left&display=inline&height=456&margin=%5Bobject%20Object%5D&name=image.png&originHeight=456&originWidth=919&size=260088&status=done&style=none&width=919)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615453986362-82bb69dd-8cc1-4b6b-ac7a-abed8ce78816.png#align=left&display=inline&height=344&margin=%5Bobject%20Object%5D&name=image.png&originHeight=344&originWidth=737&size=179242&status=done&style=none&width=737)<br />组件的名称全小写，中间用-连接
<a name="99E2j"></a>
##### 组件注意事项

- 组件参数的data值必须是函数同时这个函数要求返回一个对象 <br />
- 组件模板必须是单个根元素<br />
- 组件模板的内容可以是模板字符串<br />

**定义私有组件 componets**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615474884588-af31a552-ab91-4529-9ac3-2683365fcd47.png#align=left&display=inline&height=388&margin=%5Bobject%20Object%5D&name=image.png&originHeight=388&originWidth=507&size=134413&status=done&style=none&width=507)<br />
<br />**组件中也可以定义私有数据，vue规定，组件中的data必须是function ,而且必须return一个数据对象，在vm实例中data既可以是function，也可以是普通对象**<br />**可以认为：组件是特殊的VUE实例**<br />**组件中的this指向当前组件实例对象，__proto__指向vue对象，所以vue构造函数的vue对象身上挂载的成员，组件也可以去访问**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615514137135-377931a9-d831-4c3a-b364-9c994c88ce23.png#align=left&display=inline&height=483&margin=%5Bobject%20Object%5D&name=image.png&originHeight=483&originWidth=647&size=201045&status=done&style=none&width=647) <br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615514716520-36e4b25a-3d62-489b-b0c0-3dcf9c05eb23.png#align=left&display=inline&height=457&margin=%5Bobject%20Object%5D&name=image.png&originHeight=457&originWidth=458&size=142940&status=done&style=none&width=458)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615515063334-9aa28a9b-c603-4e64-a645-ed0b9a5941a6.png#align=left&display=inline&height=286&margin=%5Bobject%20Object%5D&name=image.png&originHeight=286&originWidth=810&size=225797&status=done&style=none&width=810)<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615518580892-e793e7d6-9c0a-42ec-bca0-65fe108ae389.png#align=left&display=inline&height=359&margin=%5Bobject%20Object%5D&name=image.png&originHeight=359&originWidth=896&size=249538&status=done&style=none&width=896)**<br />**
<a name="hYGPf"></a>
### vue文件
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615519070785-82f28e19-2d4c-4d4e-9f23-69325a4d65dc.png#align=left&display=inline&height=338&margin=%5Bobject%20Object%5D&name=image.png&originHeight=338&originWidth=878&size=158230&status=done&style=none&width=878)

<a name="0AeUQ"></a>
#### ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615530508414-766f3742-c6fc-4a21-a0db-484803a599e4.png#align=left&display=inline&height=303&margin=%5Bobject%20Object%5D&name=image.png&originHeight=303&originWidth=859&size=164885&status=done&style=none&width=859)
<a name="Y9JeK"></a>
#### vue文件中style标签的 scoped属性
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615529324701-3b660e95-41d9-4180-a9e8-5e59b0d4305c.png#align=left&display=inline&height=208&margin=%5Bobject%20Object%5D&name=image.png&originHeight=208&originWidth=200&size=43249&status=done&style=none&width=200)表示该样式只在此组件内部生效，不会影响其他引入来的组件内部的样式，一定要加，如果不加，这个样式就是全局的
<a name="N1g5x"></a>
#### vue文件中style标签的 lang = "less"属性
在style标签中就可以使用less  包裹标签的写法。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615529842724-818c32be-2076-41e3-9445-4abe5026ab43.png#align=left&display=inline&height=61&margin=%5Bobject%20Object%5D&name=image.png&originHeight=61&originWidth=721&size=43533&status=done&style=none&width=721)
<a name="E4Klf"></a>
### 组件之间的数据通信
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615530704243-dd602196-62cb-4ddc-9efc-56fd264956ea.png#align=left&display=inline&height=459&margin=%5Bobject%20Object%5D&name=image.png&originHeight=459&originWidth=874&size=254625&status=done&style=none&width=874)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615530727210-bad42f71-4dfc-4ff3-b720-05681695403a.png#align=left&display=inline&height=167&margin=%5Bobject%20Object%5D&name=image.png&originHeight=167&originWidth=839&size=67124&status=done&style=none&width=839)<br />**父组件动态的给子组件传递数据**<br />一、父组件中的data中定义好某个动态数据a<br />二、子组件中用props数组接收数据并起名b<br />三、父组件中子组件标签中绑定属性  ：b = a<br />四、在子组件模板中，可以使用b   注意：因为是动态的数据，此时的b要放在插值表达式中<br />**子组件向父组件传值**<br />一、子组件模板中用$emit 触发事件，如：@click = "$emit('自定义事件名称'，参数)"  =>注意单引双引<br />二、父组件中子组件的标签中添加 @事件名= "父组件中的方法（$event）"   =>$event就是形参<br />三、在父组件的methods中定义   父组件中的方法<br />**兄弟之间的传递**<br />一、提供事件中心    var hub = new Vue( )<br />二、传递数据方，在自己的模板中添加事件，事件在methods中定义，通过一个事件触发hub.$emit(方法名，传递的数据)<br />三、接收数据方，通过mounted(){ } 钩子中  触发hub.$on( '方法名',函数）<br />四、销毁事件 父组件中在methods中通过hub.$off( "方法名")方法名销毁之后无法进行传递数据 
<a name="92ghN"></a>
#### props的属性命名规则
1、在props中使用驼峰形式，模板中需要使用短横线的形式<br />2、字符串形式在模板中没有这个限制（template中，可以给里面的标签添加驼峰命名的属性，可以识别）<br />因为dom元素的属性是不区分大小写的<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615801338572-0dab35b7-8deb-41cc-b395-124ae4ffddc2.png#align=left&display=inline&height=221&margin=%5Bobject%20Object%5D&name=image.png&originHeight=221&originWidth=578&size=61995&status=done&style=none&width=578)
<a name="pGreZ"></a>
#### props属性值类型
字符串、数值、布尔值、数组、对象<br />数值（布尔值）：以（有冒号）：属性名 ="12"   //则这个数据为数值（布尔）类型的12<br />                             以（无冒号）   属性名 ="12"   //则这个数据为字符串类型的12<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615802233980-dfe9d461-5870-4284-833e-77902ecff028.png#align=left&display=inline&height=461&margin=%5Bobject%20Object%5D&name=image.png&originHeight=461&originWidth=1154&size=224800&status=done&style=none&width=1154)<br />props传递数据的原值：单向数据流，只允许父组件向子组件传递数据，不允许子组件直接操纵props中的数据<br />
<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615530741823-590bd28b-43cc-4002-9574-6b0ff403c14c.png#align=left&display=inline&height=210&margin=%5Bobject%20Object%5D&name=image.png&originHeight=210&originWidth=870&size=141453&status=done&style=none&width=870)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615530762022-496d79f0-05fd-49b5-b8b1-e33627346670.png#align=left&display=inline&height=260&margin=%5Bobject%20Object%5D&name=image.png&originHeight=260&originWidth=855&size=172212&status=done&style=none&width=855)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615808912925-91dfeb32-6a8e-4309-92a7-266ef7fdeebd.png#align=left&display=inline&height=368&margin=%5Bobject%20Object%5D&name=image.png&originHeight=368&originWidth=835&size=71385&status=done&style=none&width=835)
<a name="kN8kO"></a>
### 数组间数据的交互
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615809259367-daf226a3-2d94-4ee9-87de-b54e831d3d48.png#align=left&display=inline&height=403&margin=%5Bobject%20Object%5D&name=image.png&originHeight=403&originWidth=509&size=66260&status=done&style=none&width=509)<br />1、全局定义一个事件中心<br />2、在兄弟组件的mounted周期中注册监听事件<br />   hub.$on("事件名称"，事件函数)<br />3、在兄弟组件的methods方法中调用监听函数<br />  hub.$emit("事件名称"，传递的参数)<br />4、销毁事件，在methods方法中定义即可<br />       hub.$off("jerry-event")
<a name="nBss9"></a>
#### 组件插槽
组件复用的时候，内容不能写死，各个地方数据是不一样的，就要用到插槽来定义，<br />子组件中的提供给父组件使用的一个占位符，用<slot></slot> 表示<br />提供插槽之后，组件标签中的内容会传递给slot,如果不传递内容，slot可以提供默认的内容显示，如果传递了内容，slot中的内容会被覆盖<br />子组件的设置插槽，父组件通过 v-slot:[name] 的方式指定到对应的插槽中<br />例：![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615965981350-61fb0bc9-33e1-4a1a-bafa-7387d749c6da.png#align=left&display=inline&height=102&margin=%5Bobject%20Object%5D&name=image.png&originHeight=102&originWidth=367&size=20871&status=done&style=none&width=367)<br />**具名插槽**<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615812187822-9277ef44-f757-4300-9991-bf4810913fe1.png#align=left&display=inline&height=414&margin=%5Bobject%20Object%5D&name=image.png&originHeight=414&originWidth=899&size=112252&status=done&style=none&width=899)<br />slot插槽，只能写在一个标签中，如果有多个标签对应某个具名插槽，可以用template标签包括一下多个标签，将slot插槽写在对应的template标签上<br />**作用域插槽**<br />应用场景：父组件对子组件的内容进行加工处理<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615812954371-4c454eea-0cb4-42e4-955e-33a96ce678f8.png#align=left&display=inline&height=318&margin=%5Bobject%20Object%5D&name=image.png&originHeight=318&originWidth=1008&size=92556&status=done&style=none&width=1008)**总结：如果子组件没有使用插槽，父组件如果需要往子组件中填充模板或者html, 是没法做到的**<br />如果父组件向子组件的插槽传值，仅仅只是值不需要做改动，则可以在子标签中用prop属性接收，但是接收的数据需要进行进一步加工再渲染，就要插槽的帮助，如下图判断开关的状态<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1616677217717-9fcba5cb-8814-42a9-afe4-dd3d2a260e45.png#align=left&display=inline&height=177&margin=%5Bobject%20Object%5D&name=image.png&originHeight=177&originWidth=487&size=10679&status=done&style=none&width=487)<br />**eslink  ： **eslint-disable-next-line<br />
<br />.sync的用法
```javascript
//父组件给子组件传入一个函数
 <MyFooter :age="age" @setAge="(res)=> age = res">
 </MyFooter>
 //子组件通过调用这个函数来实现修改父组件的状态。
 mounted () {
      console.log(this.$emit('setAge',1234567));
 }
==================================
.sync方法！
//父组件将age传给子组件并使用.sync修饰符。
<MyFooter :age.sync="age">
</MyFooter>
//子组件触发事件
 mounted () {
    console.log(this.$emit('update:age',1234567));
 }
```


