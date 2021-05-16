<a name="jFrOr"></a>
## 提问：
1. 什么是面向对象
1. 类和对象关系
1. 使用class创建自定义类
1. 说出什么是继承
1. 什么是面向对象
1. 能够使用class关键字创建类并生成实例
1. 能够实现子类继承父类
1. 能够说出super关键字的作用的注意事项
1. 能够使用构造函数创建对象
1. 能够说出静态成员和实例成员
1. 能够说出构造函数的原型prototype
1. 能够说出构造函数实例对象与原型对象的三角关系
1. 能够理解原型链
1. 能够使用call、apply
1. 能够使用ES5中新增的方法
1. 能够说出函数的多种定义和调用方式
1. 能够说出和改变函数内部 this 的指向
1. 能够说出严格模式的特点
1. 能够把函数作为参数和返回值传递
1. 能够说出闭包的作用
1. 能够说出递归的两个条件
1. 能够说出深拷贝和浅拷贝的区别



<a name="XRkG8"></a>
## 一、面向过程与面向对象
<a name="O9dp0"></a>
### 1.1面向过程

- 面向过程就是分析出解决问题所需要的步骤,然后用函数把这些步骤一步一步实现，使用的时候再一个一个的依次调用。
<a name="bwWse"></a>
### 1.2面向对象

- 面向对象是把事务分解成为一个个对象，然后由对象之间分工与合作。
- 面向对象重在对象，面向过程重在过程
- 特性
   - 继承
   - 封装
   - 多态： 多态的定义：指允许不同类的对象对同一消息做出响应。即同一消息可以根据发送对象的不同而采用多种不同的行为方式。
<a name="X0OXy"></a>
## 二、对象
对象：泛指的类(某一类)，实例化对象
<a name="mizSW"></a>
### 1、面向对象思维特点：

1. 把对象公用的属性和行为方法组织成一个类
1. 把类实例化获取类的对象

对象是由属性和方法组成的：是一个无序键值对的集合,指的是一个具体的事物

- 属性：事物的特征，在对象中用属性来表示（常用名词）
- 方法：事物的行为，在对象中用方法来表示（常用动词）
<a name="xuI0F"></a>
### 2、创建对象的三种方法
//字面量创建对象<br />var ldh = {<br />    name: '刘德华',<br />    age: 18<br />}<br />console.log(ldh);     // 返回：{name: "刘德华", age: 18}<br />
<br />//new 关键字<br />var obj = new Object();<br />obj.name = "xxx";<br />obj.age = "yyy";<br />
<br />//构造函数创建对象<br />  function Star(name, age) {<br />    this.name = name;<br />    this.age = age;<br /> }<br />var ldh = new Star('刘德华', 18)//实例化对象<br />console.log(ldh);     //返回：Star {name: "刘德华", age: 18}  （因为是命名函数所以有名字）
<a name="2YdBy"></a>
### 3、获取对象的属性名
Object.keys(对象) 获取到当前对象中的属性名 ，返回值是一个数组<br />var result = Object.keys(obj)<br />console.log(result)    //[id,pname,price,num]
<a name="swCIN"></a>
### 4、8Object.defineProperty  ：访问器属性
Object.defineProperty(对象，修改或新增的属性名，{<br />      value:修改或新增的属性的值,<br />      writable:true/false,//如果值为false 不允许修改这个属性值<br />      enumerable: false,//enumerable 如果值为false 则不允许遍历<br />      configurable: false  //configurable 如果为false 则不允许删除这个属性 属性是否可以被删除或是否可以再次修改**特性**<br />}) 

<a name="h9PYe"></a>
## 三、函数
<a name="F270V"></a>
### 1、函数的四种定义方式
<a name="Nruxw"></a>
#### 1.1函数声明方式 function 关键字 (命名函数)
function 函数名 ( ) { }      //调用函数名（ ）
<a name="On3fg"></a>
#### 1.2 函数表达式(匿名函数)
var fn = function( ) { }
<a name="m9zAM"></a>
#### 1.3 箭头函数
ES6新增<br />( ) => { }        //()：代表是函数； =>：必须要的符号，指向哪一个代码块；{ }：函数体<br />箭头函数表达式的语法比函数表达式更短，并且没有自己的**this**，**arguments**，**super**或 **new.target**。<br />const fn = () => { }//代表把一个函数赋值给fn

- 函数体中只有一句代码，且代码的执行结果就是返回值，可以省略大括号
- 如果形参只有一个，可以省略小括号
- 当箭头函数后面的函数声明部分只有一行时，可以不加大括号，并且默认return
- **当箭头函数后面的函数声明部分加大括号时，必须添加return**
- 在ES6中，由于大括号被解释为代码块，所以如果箭头函数直接返回一个对象，必须在对象外面加上括号，否则会报错。
- ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615108338699-44bac0fc-e696-4598-9a7e-455fa9be8986.png#align=left&display=inline&height=264&margin=%5Bobject%20Object%5D&name=image.png&originHeight=264&originWidth=818&size=21424&status=done&style=none&width=818)
- 箭头函数不绑定this关键字，箭头函数中的this，指向的是函数定义位置的上下文this
- 箭头函数中不绑定this，箭头函数中的this指向是它所定义的位置，可以简单理解成，定义箭头函数中的作用域的this指向谁，它就指向谁。<br />
- 箭头函数的优点在于解决了this执行环境所造成的一些问题。比如：解决了匿名函数this指向的问题（匿名函数的执行环境具有全局性），包括setTimeout和setInterval中使用this所造成的问题<br />
<a name="7c2b3a99"></a>
#### 1.4new Function() (几乎不用，知道有这种方法就行)
var f = new Function('a', 'b', 'console.log(a + b)');<br />var f = new Function('参数1','参数2'..., '函数体')<br />注意<br />Function 里面参数都必须是字符串格式<br />第三种方式执行效率低，也不方便书写，因此较少使用<br />所有函数都是 Function 的实例(对象)  <br />函数也属于对象
<a name="qWEGF"></a>
### 2、函数的调用方式
/* 1. 普通函数 */<br />function fn() {<br />	console.log('人生的巅峰');<br />}<br /> fn();  <br />/* 2. 对象的方法 */<br />var o = {<br />  sayHi: function() {<br />  	console.log('人生的巅峰');<br />  }<br />}<br />o.sayHi();<br />/* 3. 构造函数*/<br />function Star() { };<br />var ldh = new Star('刘德华', 18)//实例化对象<br />/* 4. 绑定事件函数*/<br /> btn.onclick = function() { };   // 点击了按钮就可以调用这个函数<br />/* 5. 定时器函数*/<br />setInterval(function() { }, 1000);  这个函数是定时器自动1秒钟调用一次<br />/* 6. 立即执行函数(自调用函数)*/<br />(function() {<br />	console.log('人生的巅峰');<br />})();
<a name="tI9Yw"></a>
### 3、this的内部指向问题
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1611827004494-f1fca3ce-45d7-46c5-afe6-ecdc98a59397.png#align=left&display=inline&height=191&margin=%5Bobject%20Object%5D&name=image.png&originHeight=375&originWidth=1099&size=116899&status=done&style=none&width=559)<br />**拓展**
<a name="z71mS"></a>
##### 1、全局对象的 this 指向 window 对象
普通对象 obj 没有 this，里面访问的 this指向 window 对象<br />var a = 1000;   var obj = {       a: 1,       b: this.a+1  }   console.log(obj.b);    //1001
<a name="lRJ6z"></a>
##### 2、this 永远指向最后调用它的那个对象
<a name="B1gsE"></a>
##### 3、new 关键词改变了 this 指向
<a name="rnE7U"></a>
#### 1.改变函数内部 this 指向
<a name="mRO5f"></a>
##### 1、call方法
call()方法调用一个对象。简单理解为调用函数的方式，但是它可以改变函数的 this 指向<br />应用场景:  经常做继承. <br />var o = {<br />    name: 'andy'<br />}<br /> function fn(a, b) {<br />      console.log(this);<br />      console.log(a+b)<br />};<br />fn(1,2)// 此时的this指向的是window 运行结果为3<br />fn.call(o,1,2)//此时的this指向的是对象o,参数使用逗号隔开,运行结果为3<br />call方法仅仅改变this指向<br />假设某个函数  **arr**.**padStart**(字符串长度，缺的以什么补齐 )    arr.padStart.call( this指向，字符串长度，缺的以什么补齐 )  一样,如果省略第二个参数，默认使用空格补全长度。<br />该方法一定要是字符串使用

<a name="wAwaq"></a>
#### 2、apply方法
apply() 方法调用一个函数。简单理解为调用函数的方式，但是它可以改变函数的 this 指向。<br />应用场景:  经常跟数组有关系，第一个对象是新this,第二个对象传参需要传入一个数组。<br />var o = {<br />	name: 'andy'<br />}<br /> function fn(a, b) {<br />      console.log(this);<br />      console.log(a+b)<br />};<br />fn()// 此时的this指向的是window 运行结果为3<br />fn.apply(o,[1,2])//此时的this指向的是对象o,参数使用数组传递 运行结果为3。<br />
<br /> var arr = [1, 66, 3, 99, 4];<br /> var max = Math.max.apply(Math, arr);<br />        var min = Math.min.apply(Math, arr);<br />        console.log(max, min);     //99 1
<a name="778b45d0"></a>
####  3、bind方法
bind() 方法不会调用函数,但是能改变函数内部this 指向,返回的是原函数改变this之后   **产生的新函数**<br />如果只是想改变 this 指向，并且不想调用这个函数的时候，可以使用bind<br />应用场景:不调用函数,但是还想改变this指向<br /> var o = {<br /> name: 'andy'<br /> };<br />function fn(a, b) {<br />	console.log(this);<br />	console.log(a + b);<br />};<br />var f = fn.bind(o, 1, 2); //此处的f是bind返回的新函数<br />f();//调用新函数  this指向的是对象o 参数使用逗号隔开
<a name="q1ACH"></a>
##### 4、call、apply、bind三者的异同

- 共同点 : 都可以改变this指向
- 不同点:
   - call 和 apply  会调用函数, 并且改变函数内部this指向.
   - call 和 apply传递的参数不一样,call传递参数使用逗号隔开,apply使用数组传递
   - bind  不会调用函数, 可以改变函数内部this指向.生成一个新函数
- 应用场景
   1. call 经常做继承. 
   1. apply经常跟数组有关系.  比如借助于数学对象实现数组最大值最小值
   1. bind  不调用函数,但是还想改变this指向. 比如改变定时器内部的this指向. 
<a name="NbsYo"></a>
## 四、类
<a name="l7XUp"></a>
### 1、概念
在 ES6 中新增加了类的概念，可以使用 class 关键字声明一个类，之后以这个类来实例化对象。<br />类抽象了对象的公共部分，它泛指某一大类（class），而对象特指某一个通过类实例化一个具体的对象。<br />语法：<br />//步骤1 使用class关键字<br />class  ClassName {<br /> constructor(x,y) {<br />this.x = x;<br />this.y =y;<br />   }<br />  // class body<br />}      <br />//步骤2使用定义的类创建实例  注意new关键字<br />var xxx = new ClassName();     <br />console.log(xxx);                    //返回一个叫ClassName 的对象： ClassName{}<br />通过结果我们可以看出,运行结果和使用构造函数方式一样
<a name="GQlIf"></a>
### 2、类创建添加===属性/_方法_===
1.类的共有属性放到 constructor 里面 constructor是 构造器或者构造函数<br />constructor(uname, age) {<br />this.uname = uname;<br />}                                   //注意,方法与方法之间不需要添加逗号(案例中constructor（）和sing（）均为函数)<br />sing(song) {<br />console.log(this.uname + '唱' + song);<br />  }<br />}<br />**注意哟:**

1. 通过class 关键字创建类, 类名我们定义首字母大写
1. 类里面有个constructor 函数,可以接受传递过来的参数,同时返回实例对象
1. constructor 函数 只要 new 生成实例时,就会自动调用这个函数, 如果我们不写这个函数,类也会自动生成这个函数
1. 多个函数方法之间不需要添加逗号分隔
1. 生成实例 new 不能省略
1. 语法规范, 创建类 类名后面不要加小括号,生成实例（调用）类名后面加小括号, 构造函数不需要加function·3
<a name="2K1zz"></a>
### 3、类的继承
1.子类用extends继承父类的属性和方法<br />class Father{    }  <br />class  Son  extends Father {  }<br />2.子类使用super关键字（写在子类constructor里）访问父类的构造函数<br /> constructor(x, y) {<br />          super(x, y); //使用super调用了父类中的构造函数<br />          this.x = x;<br />          this.y = y;<br />        }<br />**不能在子类里重新定义constructor并且不用super，会报错，相当于重新给子类构造函数赋值。**<br />**如果子类想要继承父类的方法,同时在自己内部扩展自己的方法,利用super 调用父类的构造函数,super 必须在子类this之前调用**
<a name="j50D6"></a>
### 4、使用类的注意事项

1. 在 ES6 中类没有变量提升，所以必须先定义类，才能通过类实例化对象.在定义完class之后new
1. 类里面使用公有属性和方法的时候，必须通过this.去调用;

  3.时刻注意this的指向问题,类里面的共有的属性和方法一定要加this使用.

      1. constructor中的this指向的是new出来的实例对象
      1. 自定义的方法,一般也指向的new出来的实例对象
      1. 绑定事件之后this指向的就是触发事件的事件源

**核心：谁调用就指向谁**
<a name="uduJc"></a>
## 五、构造函数和原型
<a name="QoC9q"></a>
### 1.实例成员和静态成员
<a name="vkyP6"></a>
#### 实例成员
实例成员:构造函数内部通过this添加的成员，实例成员只能通过实例化的对象  例：cat.uname来访问
<a name="PiF5r"></a>
#### 静态成员
静态成员:在构造函数本身上添加的成员,静态成员只能通过构造函数来访问 例 Animal.sex
<a name="H4bg2"></a>
### 2.构造函数
详见创建对象的三种方法中的最后一种方法<br />构造函数的问题：如果构造函数有方法，那每个实例化对象在产生时都会在内存开辟一个地方存放方法，即使方法一样造成浪费内存的问题。
<a name="806e0485"></a>
#### 1、构造函数原型对象prototype
构造函数通过原型分配的函数是所有实例化对象所共享的。<br />JavaScript 规定，每一个构造函数都有一个prototype 属性，指向另一个对象。注意这个prototype就是一个对象，这个对象的所有属性和方法，都会被构造函数所拥有。我们可以把那些不变的方法，直接定义在 prototype 对象上，例：Animal.prototype.sing = function(){};这样所有对象的实例就可以共享这些方法 例：cat.sing()。
<a name="DsPxx"></a>
#### 2、对象原型__proto__
对象都会有一个属性 __proto__ 指向构造函数的 prototype 原型对象，之所以我们对象可以使用构造函数 prototype 原型对象的属性和方法，就是因为对象有 __proto__ 原型的存在。<br />__proto__对象原型和原型对象 prototype 是等价的<br />__proto__对象原型的意义就在于为对象的查找机制提供一个方向，或者说一条路线，但是它是一个非标准属性，因此实际开发中，不可以使用这个属性赋值等操作，它只是内部指向原型对象 prototype<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1611719043966-5325be0a-cc47-40d4-82b0-0a992811eb12.png#align=left&display=inline&height=311&margin=%5Bobject%20Object%5D&name=image.png&originHeight=380&originWidth=684&size=38940&status=done&style=none&width=559)<br />1.构造函数的prototype属性指向了构造函数原型对象<br />2.实例对象是由构造函数创建的,实例对象的__proto__属性指向了构造函数的原型对象<br />3.构造函数的原型对象的constructor属性指向了构造函数,实例对象的原型的constructor属性也指向了构造函数
<a name="kqUSA"></a>
#### 3、constructor构造函数
对象原型（ __proto__）和构造函数（prototype）原型对象里面都有一个属性 constructor 属性 ，constructor 我们称为构造函数，因为它指回构造函数本身。constructor 主要用于记录该对象引用于哪个构造函数，它可以让原型对象重新指向原来的构造函数。<br />一般情况下，对象的方法都在构造函数的原型对象中设置。如果有多个对象的方法，我们可以给原型对象采取对象形式赋值，但是这样就会覆盖构造函数原型对象原来的内容，这样修改后的原型对象 constructor  就不再指向当前构造函数了。此时，我们可以在修改后的原型对象中，添加一个 constructor 指向原来的构造函数。<br />      Star.prototype = { // 如果我们修改了原来的原型对象,给原型对象赋值的是一个对象,则必须手动的利用constructor指回原来的构造函数<br />                  constructor: Star, // 手动设置指回原来的构造函数,如果不指回，Star则没有constructor属性。<br />                  sing: function() {<br />                  console.log('我会唱歌');<br />            },
<a name="4MSkA"></a>
#### 4、原型链<br />
当访问一个实例对象的某个属性时，会先在这个对象本身属性上查找，如果没有找到，则会去它的__proto__隐式原型上查找，即它的构造函数的prototype，如果还没有找到就会再在构造函数的prototype的__proto__中查找，这样一层一层向上查找就会形成一个链式结构，我们称为原型链。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1611719015646-e27ee5dd-2773-44c6-ba56-bc34c0a4770a.png#align=left&display=inline&height=403&margin=%5Bobject%20Object%5D&name=image.png&originHeight=403&originWidth=778&size=54493&status=done&style=none&width=778)<br />
<br />

<a name="84cHV"></a>
#### 5、原型链和成员的查找机制
当访问一个对象的属性（包括方法）时，首先查找这个对象自身有没有该属性，有就返回。<br />如果没有就查找它的原型（也就是 __proto__指向的 prototype 原型对象），有就返回。<br />如果还没有就查找原型对象的原型（Object的原型对象），有就返回。<br />依此类推一直找到 Object 为止（null）。
<a name="1fEiq"></a>
#### 6、原型对象中this指向
构造函数中的this和原型对象的this,都指向我们new出来的实例对象
<a name="DOVWq"></a>
#### 7、通过原型为数组扩展内置方法
 Array.prototype.sum = function() { }  //实例数组可直接调用sum（）方法。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614688880729-8db1eecf-13e8-4475-95f3-b9d1e7e45dc7.png#align=left&display=inline&height=609&margin=%5Bobject%20Object%5D&name=image.png&originHeight=609&originWidth=1102&size=459919&status=done&style=none&width=1102)
<a name="bu1c7"></a>
### 3、继承
<a name="YEOHO"></a>
#### 1、call()

- call()可以调用函数 fn.call();
- call()可以修改this的指向,使用call()的时候 参数一是修改后的this指向,参数2,参数3..使用逗号隔开连接  fn.call(newThis,a,b,...)

其他改变this指向方法参考函数第三点。
<a name="6MIf3"></a>
#### 2、子构造函数继承父构造函数中的（属性）
// **1.** 设定一个父构造函数<br /> function Father(uname) { // this 指向父构造函数的对象实例<br />   this.uname = uname;<br /> }<br />  //** 2** .设定一个子构造函数  <br />function Son(uname, score) {// this 指向子构造函数的对象实例<br />Father.call(this, uname);       //**3**.在子构造函数内部调用父函数，使用call 实现继承的属性，这里面的this指的是子函数。<br />  this.score = score;<br />}<br />var son = new Son('刘德华', 100);<br />console.log(son);            //  Son {uname: "刘德华", score: 100}
<a name="eHjov"></a>
#### 3、子构造函数继承父构造函数中的（方法）
// **1**. 创建一个父构造函数<br />function Father(uname) {   // this 指向父构造函数的对象实例<br />            this.uname = uname;<br />        }<br />        Father.prototype.money = function () { //给父构造函数添加一个叫money的方法<br />            console.log(100000);<br />        };<br />  // **2** .创建一个子构造函数  <br />        function Son(uname, score) {   // this 指向子构造函数的对象实例<br />            Father.call(this, uname);  //还是用call方法<br />            this.score = score;<br />        }<br />    // Son.prototype = Father.prototype;  这样直接赋值会有问题,如果修改了子原型对象,父原型对象也会跟着一起变化<br />        Son.prototype = new Father();   // 如果利用对象的形式修改了原型对象,别忘了利用constructor 指回原来的构造函数<br />        Son.prototype.constructor = Son;<br />        Son.prototype.exam = function () {  // 给子构造函数添加一个叫考试的方法<br />            console.log('孩子要考试');<br />        }<br />        var son = new Son('刘德华', 100);<br />        console.log(son);    <br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1611727848733-443e26f8-2159-4b8c-9204-340fac0825c2.png#align=left&display=inline&height=185&margin=%5Bobject%20Object%5D&name=image.png&originHeight=239&originWidth=512&size=14959&status=done&style=none&width=397)
<a name="HGBcs"></a>
## 六、严格模式
<a name="8P23L"></a>
### 什么是严格模式
JavaScript 除了提供正常模式外，还提供了严格模式（strict mode）。ES5 的严格模式是采用具有限制性 JavaScript变体的一种方式，即在严格的条件下运行 JS 代码。<br />严格模式在 IE10 以上版本的浏览器中才会被支持，旧版本浏览器中会被忽略。<br />严格模式对正常的 JavaScript 语义做了一些更改： <br />1.消除了 Javascript 语法的一些不合理、不严谨之处，减少了一些怪异行为。<br />2.消除代码运行的一些不安全之处，保证代码运行的安全。<br />3.提高编译器效率，增加运行速度。<br />4.禁用了在 ECMAScript 的未来版本中可能会定义的一些语法，为未来新版本的 Javascript 做好铺垫。比如一些保留字如：class,enum,export, extends, import, super 不能做变量名<br />5.严格模式不允许删除变量<br />严格模式下全局作用域中函数中的 this 是 undefined<br />严格模式下,如果构造函数不加new调用, this 指向的是undefined 如果给他赋值则 会报错.<br />严格模式下，定时器 this 还是指向 window
<a name="QDf6u"></a>
#### 情况一 :为脚本开启严格模式
有的 script 脚本是严格模式，有的 script 脚本是正常模式，这样不利于文件合并，所以可以将整个脚本文件放在一个立即执行的匿名函数之中。这样独立创建一个作用域而不影响其他script 脚本文件。<br /><script><br />  　"use strict"; //当前script标签开启了严格模式<br /></script>
<a name="8RjSD"></a>
#### 情况二: 为函数开启严格模式
要给某个函数开启严格模式，需要把“use strict”;  (或 'use strict'; ) 声明放在函数体所有语句之前。<br />function fn(){<br />  "use strict";        //当前fn函数开启了严格模式<br />  return "123";<br />} 
<a name="nJR46"></a>
## 七、高阶函数
函数也是一种数据类型，同样可以作为参数，传递给另外一个参数使用。同理函数也可以作为返回值传递回来。<br />最典型的就是作为回调函数。
<a name="kbbx1"></a>
## 八、闭包
<a name="f9jJd"></a>
### 1、概念：
闭包（closure）指有权访问另一个函数作用域中变量的函数。<br />简单理解就是 ，一个作用域可以访问另外一个函数内部的局部变量。 <br />变量根据作用域的不同分为两种：全局变量和局部变量。

1. 函数内部可以使用全局变量。
1. 函数外部不可以使用局部变量。
1. 当函数执行完毕，本作用域内的局部变量会销毁。
<a name="GQJxx"></a>
### 2、闭包的作用
作用：延伸变量的作用范围。<br />function fn( ) {<br />   var num = 10;<br />   function fun( ) {<br />       console.log(num);<br />  }<br />    return fun;<br /> }<br />var f = fn();<br />f();<br />打断点的时候才能看到闭包
<a name="J42vd"></a>
## 九、递归
<a name="CqNXN"></a>
### 1、什么是递归
满足递归的两个条件

- 可以通过递归调用来缩小问题规模，且新问题与原问题有着相同的形式。
- 存在一种简单情境，可以使递归在简单情境下退出。

**递归：**如果一个函数在内部可以调用其本身，那么这个函数就是递归函数。简单理解:函数内部自己调用自己, 这个函数就是递归函数<br />**注意：**递归函数的作用和循环效果一样，由于递归很容易发生“栈溢出”错误（stack overflow），所以必须要加退出条件return。<br />//利用递归函数求1~n的阶乘 1 * 2 * 3 * 4 * ..n<br /> function fn(n) {<br />     if (n == 1) {      //结束条件<br />       return 1;<br />     }<br />     return n * fn(n - 1);<br /> }<br /> console.log(fn(3));
<a name="wrgWV"></a>
## 十、浅拷贝和深拷贝
<a name="9Gsu1"></a>
### 浅拷贝
**浅拷贝是指拷贝对象时仅仅拷贝对象本身和对象中的基本变量，而不拷贝对象包含的引用指向的对象。**<br />**深拷贝不仅拷贝对象本身，而且拷贝对象包含的引用指向的所有对象。**<br />如何区分深拷贝与浅拷贝，简单点来说，就是假设B复制了A，当修改A时，看B是否会发生变化，如果B也跟着变了，说明这是浅拷贝，如果B没变，那就是深拷贝。<br />2.Object.assign(target,...sources)    es6新增方法可以浅拷贝
<a name="ur9MZ"></a>
### 深拷贝
1、深拷贝拷贝多层，每一级别的数据都会拷贝<br />        const o = { };   //创一个新数组接收<br />        function fn(newObj, oldObj) {<br />            for (let k in oldObj){   //k是属性名  obj[k]是属性值<br />                const item = oldObj[k];<br />                if(Array.isArray(oldObj[k])){  //判断是否为数组类型，要写在对象判断之前，因为数组本质也是对象<br />                    newObj[k] =[];<br />                    fn(newObj[k], item);<br />                }else if( item instanceof Object){  //判断是否为对象类型<br />                    newObj[k] ={};<br />                    fn(newObj[k], item)<br />                }else{<br />                    newObj[k]=item;  //剩下基本数据类型<br />                }<br />            }<br />        }<br />       fn(o,obj);<br />       console.log(o);<br />应用场景<br />后端返回的数据，有多个地方需要调用，其中有某几处的方法需要修改原数组，那就不能直接改，要先拷贝一份再进行处理
<a name="g7MUh"></a>
## 十一、正则表达式
<a name="0DNpq"></a>
### 1、正则表达式  _regexp_
正则表达式（ Regular Expression ）是用于匹配字符串中字符组合的模式。在JavaScript中，正则表达式也是对象。<br />正则表通常被用来检索、替换那些符合某个模式（规则）的文本，例如验证表单：用户名表单只能输入英文字母、数字或者下划线， 昵称输入框中可以输入中文(匹配)。此外，正则表达式还常用于过滤掉页面内容中的一些敏感词(替换)，或从字符串中获取我们想要的特定部分(提取)等 。        /**不加引号！**/

方式一：通过调用RegExp对象的构造函数创建 <br />const regexp = new RegExp(/123/);<br />     console.log(regexp);<br />方式二：利用字面量创建 正则表达式<br />const  rg = /123/;
<a name="cUG4J"></a>
### 测试正则表达式 test( )
test() 正则对象方法，用于检测字符串是否符合该规则，该对象会返回 true 或 false，其参数是测试字符串。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612265493118-8ec3517a-c83f-40af-b25e-f9983a8f6664.png#align=left&display=inline&height=191&margin=%5Bobject%20Object%5D&name=image.png&originHeight=191&originWidth=888&size=19273&status=done&style=none&width=888)
<a name="zz6O8"></a>
### 2、边界符
正则表达式中的边界符（位置符）用来提示字符所处的位置，主要有两个字符

| 边界符 | 说明 |
| --- | --- |
| ^ | 表示匹配行首的文本（以谁开始） |
| $ | 表示匹配行尾的文本（以谁结束） |

如果 ^和 $ 在一起，表示必须是精确匹配。
<a name="17Do5"></a>
### 3、字符类
<a name="5hY7g"></a>
#### 1、 [] 方括号
表示有一系列字符可供选择，只要匹配其中一个就可以了<br />var rg1 = /^[abc]$/; // 三选一 只有是a 或者是 b  或者是c 这三个字母才返回 true
<a name="INSKF"></a>
#### 2、量词符
量词符用来设定某个模式出现的次数。

| 量词 | 说明 |
| :--- | --- |
| * | 重复0次或更多次 |
| + | 重复1次或更多次 |
| ? | 重复0次或1次 |
| {n} | 重复n次 |
| {n,} | 重复n次或更多次 |
| {n,m} | 重复n到m次 |

<a name="QJ96y"></a>
#### 3、括号总结
1.大括号  量词符.  里面表示重复次数<br />2.中括号 字符集合。匹配方括号中的任意字符. <br />3.小括号表示优先级，或表示提取的内容<br />**提取分组 （ ）**<br />**正则中用（）扩起来的为一个分组，可以通过新声明的变量接收**<br />const newReg = 正则表达式.exec(待匹配的字符串)<br />如果 exec() 找到了匹配的文本，则返回一个结果数组。否则，返回 null。此数组的第 0 个元素是与正则表达式相匹配的文本，第 1 个元素是与 RegExpObject 的第 1 个子表达式相匹配的文本（如果有的话），第 2 个元素是与 RegExpObject 的第 2 个子表达式相匹配的文本（如果有的话），以此类推。除了数组元素和 length 属性之外，exec() 方法还返回两个属性。index 属性声明的是匹配文本的第一个字符的位置。input 属性则存放的是被检索的字符串 string。我们可以看得出，在调用非全局的 RegExp 对象的 exec() 方法时，返回的数组与调用方法 String.match() 返回的数组是相同的。
```javascript
 const str = "abcdefg!hijklmn."
   const reg = /e(fg)!/
   const newStr = reg.exec(str);
   console.log(newStr);
```
<br />
<a name="WAEC7"></a>
#### 4、预定义类
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1611922761663-5e31586e-fb10-44c4-b8f0-2202f0acd3b5.png#align=left&display=inline&height=192&margin=%5Bobject%20Object%5D&name=image.png&originHeight=268&originWidth=803&size=68710&status=done&style=none&width=574)<br />正则表达式  \.   用来匹配点字符
<a name="fJPLM"></a>
#### 5、正则替换replace
 const str = 'cqyzsC012QzAabcd';<br />        const newstr =str.replace(/a|c|q/gi,"你好")    //用 | 分隔      **g表示全部替换  i表示忽略大小写 ** **gi表示既忽略大小写又全部替换 ，放在/最后**<br />   replace() 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。<br />stringObject.replace(_regexp/substr_,_replacement_)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612403815593-e194efb6-433e-4118-8ad1-72b76b1e94bd.png#align=left&display=inline&height=175&margin=%5Bobject%20Object%5D&name=image.png&originHeight=175&originWidth=810&size=16436&status=done&style=none&width=810)<br />字符串 stringObject 的 replace() 方法执行的是查找并替换的操作。它将在 stringObject 中查找与 regexp 相匹配的子字符串，然后用 replacement 来替换这些子串。如果 regexp 具有全局标志 g，那么 replace() 方法将替换所有匹配的子串。否则，它只替换第一个匹配子串。<br />replacement 可以是字符串，也可以是函数。如果它是字符串，那么每个匹配都将由字符串替换。但是 replacement 中的 $ 字符具有特定的含义。如下表所示，它说明从模式匹配得到的字符串将用于替换。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612403906121-9ceb0491-d75b-4502-956c-0de99cbef595.png#align=left&display=inline&height=236&margin=%5Bobject%20Object%5D&name=image.png&originHeight=236&originWidth=821&size=15410&status=done&style=none&width=821)
```javascript
//在本例中，我们将把 "Doe, John" 转换为 "John Doe" 的形式：
		name = "Doe, John";
		const abc = /(\w+)\s*, \s*(\w+)/;
		const newName = name.replace(abc, "$2 $1");
		console.log(newName);	   //  John Doe
```
<a name="2RJvN"></a>
### 模板引擎的使用方法
jQ方法下：<br />html页面引入 template-web.js<br />html页面引入模板<br /> <script type="text/html" id="**tpl-table"**><br />        {{each data}}<br />        <tr><br />          <td>{{$value.name}}</td><br />          <td>{{$value.alias}}</td><br />          <td><br />            <button type="button" class="layui-btn layui-btn-xs">编辑</button><br />            <button type="button" class="layui-btn layui-btn-danger layui-btn-xs">删除</button><br />          </td><br />        </tr><br />        {{/each}}<br />      </script><br />在js文件中，进行ajax请求的时候<br /> const result = template("**tpl-table**",**res**);<br />                $("tbody").html(result)<br />

<a name="mcm7A"></a>
### 不同js文件之间调用方法
不同js文件无法相互调用对方的方法，有一种情况下可以<br />在后台管理系统中让两个页面有从属关系，这样一来，子页面中的可以通过<br />window.parent.方法名（）或者<br />window.top.方法名（）来调用父页面中定义的方法。<br />（可以用iframe来建立页面嵌套）。<br />html结构内<br /> <iframe src="xxxxxxxxxxxxx" name="fm"></iframe><br /><a href="目标文件" target="fm">基本资料</a><br />
<br />foreach  和for  in获取数据是一开始就获取完毕<br />for of 和  for循环是动态获取数据，会导致栈溢出<br />

<a name="OxbTw"></a>
## JS通过Object.create创建对象内部原理分析研究
**通过Object.create()方法创建一个新对象，使新对象的__proto__原型指向通过create传入的对象**
```javascript
let foo = {
      age:10
  };
  let f = Object.create(foo);
  console.log(f.age);//10
```
<a name="dNRnb"></a>
### create的内部原理
```javascript
 Object.create => function(obj){
      var f = function(){};
      f.prototype = obj;
      return new f();
  }
```

1. **先在内部创建一个空构造函数**
1. **把构造函数的原型指向传进来的obj对象**
1. **通过new创建对象并返回**

**因此新创建出来的对象调用的属性和方法都会去传入对象上去找**
