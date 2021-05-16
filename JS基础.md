<a name="6VRdL"></a>
## 1、JS中数据类型的判断
1. **typeof** 对于原始类型来说，除了 null 都可以显示正确的类型
```javascript
console.log(typeof 2);               // number
console.log(typeof true);            // boolean
console.log(typeof 'str');           // string
console.log(typeof []);              // object     []数组的数据类型在 typeof 中被解释为 object
console.log(typeof function(){});    // function
console.log(typeof {});              // object
console.log(typeof undefined);       // undefined
console.log(typeof null);            // object     null 的数据类型被 typeof 解释为 object
```
**instanceof**<br />instanceof 可以正确的判断对象的类型，因为内部机制是通过判断对象的原型链中是不是能找到类型的 prototype。instanceof可以精准判断引用数据类型（Array，Function，Object），而基本数据类型不能被instanceof精准判断。<br />instanceof 在MDN中的解释：instanceof 运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性。
```javascript
console.log(2 instanceof Number);                    // false
console.log(true instanceof Boolean);                // false 
console.log('str' instanceof String);                // false  
console.log([] instanceof Array);                    // true
console.log(function(){} instanceof Function);       // true
console.log({} instanceof Object);                   // true    
// console.log(undefined instanceof Undefined);      //报错，未定义
// console.log(null instanceof Null);                //报错，未定义
```
**constructor**
```javascript
console.log((2).constructor === Number); // true
console.log((true).constructor === Boolean); // true
console.log(('str').constructor === String); // true
console.log(([]).constructor === Array); // true
console.log((function() {}).constructor === Function); // true
console.log(({}).constructor === Object); // true
这里有一个坑，如果我创建一个对象，更改它的原型，constructor就会变得不可靠了
function Fn(){};
Fn.prototype=new Array();
var f=new Fn();
console.log(f.constructor===Fn);    // false
console.log(f.constructor===Array); // true 
```
**Object.prototype.toString.call()** 使用 Object 对象的原型方法 toString ，使用 call 进行狸猫换太子，借用Object的 toString 方法
```javascript
var a = Object.prototype.toString;
		console.log(a.call(2));         //[object Number]
```


<a name="bFISw"></a>
## 说说ES5的继承和ES6的继承
<a name="sEM8d"></a>
### es5中继承的方式
<a name="VLPdu"></a>
#### 1、原型链继承
基本思想：利用原型让一个引用类型继承另一个引用类型的属性和方法，即让原型对象等于另一个类型的实例

- 别忘记默认的原型，所有的引用类型都继承自Object，所有函数的默认原型都是Object的实例，因此默认原型里都有一个指针，指向object.prototype<br />
- 谨慎地定义方法，给原型添加方法的代码一定要放在替换原型的语句之后，不能使用对象字面量添加原型方法，这样会重写原型链<br />
```javascript
 function father() {
      this.property = true;
    }
    father.prototype.getSuperValue = function () {
      return this.property;
    };
    function Son() {
      this.subproperty = false;
    }
    //  继承了SuperType
    Son.prototype = new father();

    Son.prototype.getSubValue = function () {
      return this.subproperty;
    };
    var instance = new Son();
    alert(instance.getSuperValue());     //true
```
<a name="1q3Db"></a>
#### 2、借用构造函数（对象冒充继承）
基本思想：通过使用apply()和call()方法可以在将来新创建的对象上执行构造函数<br />通过call或者apply方法，我们实际上是在将来新创建的son实例的环境下调用了father构造函数。这样一来，就会在新son对象上执行father函数中定义的所有对象初始化代码，因此，每一个Son的实例都会有自己的colors对象的副本
```javascript
    function father() {
      this.colors = ["red", "blue", "green"];
    }

    function Son() {
      //借调了超类型的构造函数
      father.call(this);
    }

    var instance1 = new Son();
    //["red","blue","green","black"]
    instance1.colors.push("black");
    console.log(instance1.colors);

    var instance2 = new Son();
    //["red","blue","green"]
    console.log(instance2.colors);
  
```
<a name="MfxiF"></a>
#### 3、**组合继承**
基本思想：将原型链和借用构造函数技术组合到一起。使用原型链实现对原型属性和方法的继承，用借用构造函数模式实现对实例属性的继承。这样既通过在原型上定义方法实现了函数复用，又能保证每个实例都有自己的属性<br />缺点：无论在什么情况下，都会调用两次父构造函数，一次是在创建子类型原型的时候，一次是在子类型构造函数的内部
```javascript
    function father(name) {
      this.name = name;
      this.colors = ["red", "green", "blue"];
    }

    father.prototype.sayName = function () {
      console.log(this.name);
    };

    function Son(name, age) {
      //继承属性
      father.call(this, name);
      this.age = age;
    }

    //继承方法
    Son.prototype = new father();
    Son.prototype.constructor = Son;
    Son.prototype.sayAge = function () {
      console.log(this.age);
    };

    var instance1 = new Son('Annika', 21);
    instance1.colors.push("black");
    //["red", "green", "blue", "black"]
    console.log(instance1.colors);
    instance1.sayName(); //Annika
    instance1.sayAge();  //21

    var instance2 = new Son('Anna', 22);
    //["red", "green", "blue"]
    console.log(instance2.colors);
    instance2.sayName();   //Anna
    instance2.sayAge();    //22
```
<a name="Hlns5"></a>
#### 4、原型式继承
不用严格意义上的构造函数，借助原型可以根据已有的对象创建新对象，还不必因此创建自定义类型，因此最初有如下函数   <br />从本质上讲，object()对传入其中的对象执行了一次浅复制<br />用这种方法指定的任何属性都会覆盖掉原型对象上的同名属性<br />用处：创造两个相似的对象，但是包含引用类型的值的属性始终会共享响应的值
```javascript
 var person = {
      name: 'Annika',
      friendes: ['Alice', 'Joyce']
    };

    var anotherPerson = object(person);
    anotherPerson.name = 'Greg';
    anotherPerson.friendes.push('Rob');

    var yetAnotherPerson = object(person);
    yetAnotherPerson.name = 'Linda';
    yetAnotherPerson.friendes.push('Sophia');

    console.log(person.friends);   //['Alice','Joyce','Rob','Sophia']

```
**
<a name="CXve2"></a>
#### 5、寄生式继承
寄生式继承是与原型式继承紧密相关的一种思路，它创造一个仅用于封装继承过程的函数，在函数内部以某种方式增加对象，最后再返回对象。<br />使用寄生式继承来为对象添加函数，会因为做不到函数复用而降低效率，这个与构造函数模式类似
```javascript
function Supertype(name) {
      this.name = name;
      this.colors = ["red", "green", "blue"];
    }
    Supertype.prototype.sayName = function () {
      console.log(this.name);
    };
    function Subtype(name, age) {
      //继承属性
      Supertype.call(this, name);
      this.age = age;
    }
    //继承方法
    inheritPrototype(Subtype, Supertype);
    Subtype.prototype.sayAge = function () {
      console.log(this.age);
    };
```
<br />
<a name="9u8si"></a>
### es6中的继承方式
<a name="bu1c7"></a>
### 继承
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
// **1**. 创建一个父构造函数<br />function Father(uname) {   // this 指向父构造函数的对象实例<br />            this.uname = uname;<br />        }<br />        Father.prototype.money = function () { //给父构造函数添加一个叫money的方法<br />            console.log(100000);<br />        };<br />  // **2** .创建一个子构造函数  <br />        function Son(uname, score) {   // this 指向子构造函数的对象实例<br />            Father.call(this, uname);  //还是用call方法<br />            this.score = score;<br />        }<br />    // Son.prototype = Father.prototype;  这样直接赋值会有问题,如果修改了子原型对象,父原型对象也会跟着一起变化<br />        Son.prototype = new Father();   // 如果利用对象的形式修改了原型对象,别忘了利用constructor 指回原来的构造函数<br />        Son.prototype.constructor = Son;<br />        Son.prototype.exam = function () {  // 给子构造函数添加一个叫考试的方法<br />            console.log('孩子要考试');<br />        }<br />        var son = new Son('刘德华', 100);<br />        console.log(son);    

