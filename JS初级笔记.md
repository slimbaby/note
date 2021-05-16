<a name="rWdhY"></a>
## 一、JS概念
JavaScript 是一种运行在客户端的脚本语言 （Script 是脚本的意思），最初为了表单动态校验（密码强度检测）<br />组成：ECMAScript（js语法）、 DOM（页面文档对象类型）、BOM（浏览器对象模型）
<a name="ZpBBl"></a>
## 二、注释
单行注释  ctrl + /        效果 :   //<br />多行注释  shift + alt + a       效果：/*    */
<a name="8TL11"></a>
## 三、三种书写方式
行内式、内嵌式、外部引入JS文件<br />
<br />3.字符串长度<br />字符串是由若干字符组成的，这些字符的数量就是字符串的长度。通过字符串的 length 属性可以获取整个字符串的长度。  str.length<br />4.字符串拼接<br />+ 号总结口诀：数值相加 ，字符相连<br />
<a name="mj2fu"></a>
## 五、数据类型
<a name="w826U"></a>
### 一、简单数据类型
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612059424718-6a99ae5d-b145-45a5-a8ac-3abc03e111a5.png#align=left&display=inline&height=148&margin=%5Bobject%20Object%5D&name=image.png&originHeight=200&originWidth=696&size=70002&status=done&style=none&width=515)<br />还有object （万物皆对象）和 Symbol （一种类似于字符串的ES6 新增数据类型） <br />Symbol函数可以接受一个字符串作为参数，表示对 Symbol 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分。<br />let s1 = Symbol('foo'); 不能用new,这是因为生成的 Symbol 是一个原始类型的值，不是对象。也就是说，由于 Symbol 值不是对象，所以不能添加属性。基本上，它是一种**类似于字符串的数据类型**。<br />   2.字符串转义符<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612059621221-03129ed2-6273-4997-9092-db640a119c63.png#align=left&display=inline&height=210&margin=%5Bobject%20Object%5D&name=image.png&originHeight=275&originWidth=668&size=15347&status=done&style=none&width=511)<br />5.获取变量数据类型<br />var num = 18;<br />console.log(typeof num)          // 结果 number   **(typeof后为空格！不加点，变量名放在of后面)**<br />**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060099146-f413be02-6332-41d4-81c2-d4ee102bd9c6.png#align=left&display=inline&height=191&margin=%5Bobject%20Object%5D&name=image.png&originHeight=233&originWidth=698&size=34176&status=done&style=none&width=572)**<br />6.数据类型转换

 使用**表单、prompt **获取过来的数据默认是字符串类型的，此时就不能直接简单的进行加法运算，而需要转换变量的数据类型。通俗来说，就是把一种数据类型的变量转换成另外一种数据类型。<br />6.1转换为字符串<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060220564-8da7539d-f67f-4db6-856b-883c72e9f60d.png#align=left&display=inline&height=162&margin=%5Bobject%20Object%5D&name=image.png&originHeight=204&originWidth=670&size=57456&status=done&style=none&width=533)<br />6.2转换为数字型（重点）<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060260589-688c3eed-c796-4345-b3ac-137858bd9594.png#align=left&display=inline&height=193&margin=%5Bobject%20Object%5D&name=image.png&originHeight=241&originWidth=687&size=73941&status=done&style=none&width=550)<br />6.3转换为布尔型<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060299969-a662c154-673b-4dbe-860a-4f54eedc35a1.png#align=left&display=inline&height=114&margin=%5Bobject%20Object%5D&name=image.png&originHeight=143&originWidth=711&size=22685&status=done&style=none&width=568)
<a name="YTpYM"></a>
### 二、复杂数据类型
复杂数据类型（引用类型）：在存储时变量中存储的仅仅是地址（引用），通过 new 关键字创建的对象（系统对象、自定义对象），如 Object、Array、Date等；
<a name="xSsXm"></a>
## 六、堆和栈

- 堆栈空间分配区别：<br />

　　1、栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。其操作方式类似于数据结构中的栈；<br />简单数据类型存放到栈里面<br />　　2、堆（操作系统）：存储复杂类型(对象)，一般由程序员分配释放，若程序员不释放，由垃圾回收机制回收。

- 简单数据类型的存储方式

值类型变量的数据直接存放在变量（栈空间）中<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612107805659-65ee0e24-77cb-4bd3-82f2-5f3b89a05c6f.png#align=left&display=inline&height=118&margin=%5Bobject%20Object%5D&name=image.png&originHeight=137&originWidth=542&size=7639&status=done&style=none&width=467)

- 复杂数据类型的存储方式

引用类型变量（栈空间）里存放的是地址，真正的对象实例存放在堆空间中<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612107824474-07bdcd54-fd0c-4fc9-9a43-f044f6924469.png#align=left&display=inline&height=205&margin=%5Bobject%20Object%5D&name=image.png&originHeight=205&originWidth=460&size=8658&status=done&style=none&width=460)
<a name="FZjJ5"></a>
## 传参
<a name="e9c090ea"></a>
### 简单类型传参
	函数的形参也可以看做是一个变量，当我们把一个值类型变量作为参数传给函数的形参时，其实是把变量在栈空间里的值复制了一份给形参，那么在方法内部对形参做任何修改，都不会影响到的外部变量。<br />num1 = 10<br />num2 = num1<br />num2 += 1;<br />console.log(num1); //10<br />console.log(num2); //11
<a name="ae10a1a1"></a>
###  复杂数据类型传参
	函数的形参也可以看做是一个变量，当我们把引用类型变量传给形参时，其实是把变量在栈空间里保存的堆地址复制给了形参，形参和实参其实保存的是同一个堆地址，所以操作的是同一个对象。<br />var obj1 = {<br />  name : "111"<br />};<br />var obj2 = obj1;<br />console.log(obj2.name); //111<br />obj2.name = "222";<br />console.log(obj1.name); //222
<a name="8YM9S"></a>
## 七、运算符
<a name="iEFeI"></a>
### 一、算术运算符
%  +  -  *  /              余数 加 减 乘 除<br />不要直接判断两个浮点数是否相等 ，（有精度问题）
<a name="PhPAO"></a>
### 二、递增和递减运算符
前置递增运算符<br />++num 前置递增，就是自加1，类似于 num =  num + 1，但是 ++num 写起来更简单。<br />使用口诀：先自加，后返回值<br />后置递增运算符<br />num++ 后置递增，就是自加1，类似于 num =  num + 1 ，但是 num++ 写起来更简单。<br />使用口诀：先返回原值，后自加 
<a name="6u83G"></a>
### 三、比较运算符
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060834481-37287753-80a7-4bf0-bafb-cfe6a6a17546.png#align=left&display=inline&height=185&margin=%5Bobject%20Object%5D&name=image.png&originHeight=258&originWidth=667&size=47724&status=done&style=none&width=477)<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060843859-e2501c09-75e3-4deb-b21e-e5db684d09f4.png#align=left&display=inline&height=94&margin=%5Bobject%20Object%5D&name=image.png&originHeight=138&originWidth=693&size=34648&status=done&style=none&width=473)
<a name="Ys8Wx"></a>
### 四、逻辑运算符
与或非<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612060883022-1738f611-54d9-4e39-b7a0-460cc4baee5a.png#align=left&display=inline&height=97&margin=%5Bobject%20Object%5D&name=image.png&originHeight=141&originWidth=693&size=30038&status=done&style=none&width=479)<br />短路运算（**逻辑中断**）<br />原理：当有多个表达式（值）时,左边的表达式值可以确定结果时,就不再继续运算右边的表达式的值;<br />逻辑与<br />语法： 表达式1 && 表达式2<br />- 如果第一个表达式的值为真，则返回表达式2<br />- 如果第一个表达式的值为假，则返回表达式1<br />逻辑或<br />语法： 表达式1 || 表达式2<br />- 如果第一个表达式的值为真，则返回表达式1<br />- 如果第一个表达式的值为假，则返回表达式2
<a name="DKgfv"></a>
### 五、赋值运算符
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612061016579-9c2c7ab6-44c3-4585-943f-4440140bf604.png#align=left&display=inline&height=105&margin=%5Bobject%20Object%5D&name=image.png&originHeight=148&originWidth=718&size=39219&status=done&style=none&width=509)
<a name="fbBOh"></a>
### 六、运算符优先级
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612061043019-e4797bda-a3ab-4670-bba9-10bb93a7e360.png#align=left&display=inline&height=225&margin=%5Bobject%20Object%5D&name=image.png&originHeight=291&originWidth=675&size=42074&status=done&style=none&width=521)
<a name="g84O9"></a>
### 八、流程控制
顺序结构、分支结构、循环结构<br />分支结构<br />一、if ( ) { } ;<br />二、if ( ) { } else if ( ) { } else { } ;<br />三、三元表达式：<br />     ** return** 表达式1   ?   表达式2   :   表达式3;<br />四、switch分支  （break 和 default不要忘记）<br />switch( 表达式 ){  <br />    case value1:      // 表达式 等于 value1 时要执行的代码<br />       **break** ;<br />    case value2:     // 表达式 等于 value2 时要执行的代码<br />       **break** ;<br />   **default **:           // 表达式 不等于任何一个 value 时要执行的代码<br />}<br />
<br />

<a name="HFmnv"></a>
### 循环结构
一、for 循环<br />for(初始化变量; 条件表达式; 操作表达式 ){<br />    //循环体<br />}<br />二、while循环<br />while 语句可以在条件表达式为真的前提下，循环执行指定的一段代码，直到表达式不为真时结束循环。<br />while语句的语法结构如下：<br />while (条件表达式) {<br />    // 循环体代码  <br />}<br />**注意**：<br />

- 使用 while 循环时一定要注意，它必须要有退出条件，否则会成为死循环<br />
- while 循环和 for 循环的不同之处在于 while 循环可以做较为复杂的条件判断，比如判断用户名和密码



do...while<br />do... while 语句其实是 while 语句的一个变体。该循环会先执行一次代码块，然后对        条件表达式进行判断，如果条件为真，就会重复执行循环体，否则退出循环。<br />do... while 语句的语法结构如下：<br />do {<br />    // 循环体代码 - 条件表达式为 true 时重复执行循环体代码<br />} while(条件表达式)<br />**注意**：先再执行循环体，再判断，do…while循环语句至少会执行一次循环体代码

<a name="ytgdC"></a>
### continue、break
continue 关键字用于立即跳出本次循环，继续下一次循环（本次循环体中 continue 之后的代码就会少执行一次）。<br />break 关键字用于立即跳出整个循环（循环结束）。
<a name="WtGxx"></a>
## 九、数组
<a name="5a09b36f"></a>
### 数组的概念

- 数组可以把一组相关的数据一起存放，并提供方便的访问(获取）方式。<br />
- 数组是指**一组数据的集合**，其中的每个数据被称作**元素**，在数组中可以**存放任意类型的元素**。数组是一种将一组数据存储在单个变量名下的优雅方式。

**二维数组：**二维数组的本质：数组中的元素又是数组
<a name="7AhlT"></a>
### 二、创建数组
一、利用  new 创建数组  <br />var 数组名 = new Array( ) ；<br />二、利用数组字面量创建数组<br />var  数组名 = [ ]；
<a name="uFeB5"></a>
### 三、获取数组中的元素
索引 (下标) ：用来访问数组元素的序号（数组下标从 0 开始）。数组名[索引]    arr [ 0 ]<br />注意：如果访问时数组没有和索引值对应的元素，则得到的值是undefined
<a name="Mmafo"></a>
## 十、函数
概念：就是封装了一段可被重复调用执行的代码块。通过此代码块可以实现大量代码的重复使用。
<a name="nngEJ"></a>
### 一、声明方法
声明一（命名函数）：<br />function 函数名 ( ) {<br />            //函数体代码<br />}<br />调用函数的代码既可以放到声明函数的前面，也可以放在声明函数的后面

声明二（匿名函数）：<br />var 变量名 = function(){...}；<br />变量名 ( );<br />// 调用的方式，函数调用必须写到函数体下面<br />
<br />拓展：匿名函数的8种立即调用方法<br />方法一：  (function() { alert("你好"); }) ( )<br />方法二：  (function() { alert("你好");} ( ))<br />方法三：  [function() { alert("你好");} ( )]<br />方法四： +function() { alert("你好"); } ( )<br />方法五： -function() { alert("你好"); } ( )<br />方法六： ~function() { alert("你好"); } ( )<br />方法七：  !function(){ document.write("你好");} ( )  //在页面上显示一个你好，！必备不可省略<br />方法八：  void function() { alert("你好"); } ( )<br />
<br />多个立即执行函数之间要用 ；分开<br />应用场景：为了防止变量命名冲突（变量污染），采用立即执行函数，此中的this指向全局变量window。

另外两种声明方式：箭头函数和new Function( )见JS高级笔记
<a name="l3gsn"></a>
### 二、函数参数语法

- 形参：函数定义时设置接收调用时传入<br />
- 实参：函数调用时传入小括号内的真实数据<br />

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612063747172-d9162a59-a456-4624-9fe1-c5c6d89c939e.png#align=left&display=inline&height=73&margin=%5Bobject%20Object%5D&name=image.png&originHeight=111&originWidth=711&size=40790&status=done&style=none&width=468)<br />函数形参和实参数量不匹配时<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612063808384-8b61865e-d3ce-4426-acc0-4db53e8e1b30.png#align=left&display=inline&height=98&margin=%5Bobject%20Object%5D&name=image.png&originHeight=128&originWidth=614&size=28815&status=done&style=none&width=469)
<a name="ZHibr"></a>
### 三、函数的返回值 return
返回值：函数调用整体代表的数据；函数执行完成后可以通过return语句将指定数据返回 

- 在使用 return 语句时，函数会停止执行，并返回指定的值<br />
- 如果函数没有 return ，返回的值是 undefined

**return  必须写在函数里才能返回，写在其他数据类型中会报错！**
<a name="8E8K0"></a>
## 十一、作用域
<a name="Gtu0h"></a>
### 一、分类，es6之前

- 全局作用域

作用于所有代码执行的环境(整个 script 标签内部)或者一个独立的 js 文件。

- 局部作用域（函数作用域）

作用于函数内的代码环境，就是局部作用域。 因为跟函数有关系，所以也称为函数作用域。
<a name="viZvB"></a>
### 二、变量作用域

- 全局变量

在任何一个地方都可以使用，只有在浏览器关闭时才会被销毁，因此比较占内存<br />

- 局部变量

只在函数内部使用（函数形参），当其所在的代码块被执行时，会被初始化；当代码块运行结束后，就会被销毁，因此更节省内存空间<br />**在函数内部 var 声明的变量是局部变量**

- **作用域链**

如果函数中还有函数，那么在这个作用域中就又可以诞生一个作用域；根据在[**内部函数可以访问外部函数变量**]的这种机制，用链式查找决定哪些数据能被内部函数访问，就称作作用域链 ：**采取就近原则的方式来查找变量最终的值。**

- **预****解析**

预解析会把变量和函数的声明在代码执行之前执行完成。<br />预解析也叫做变量、函数提升。<br />变量提升（变量预解析）： 变量的声明会被提升到当前作用域的最上面，变量的赋值不会提升。<br />函数提升： 函数的声明会被提升到当前作用域的最上面，但是不会调用函数。
<a name="2cM9d"></a>
## 十二、对象
<a name="8fkDD"></a>
### 概念
对象是一组无序的相关属性和方法的集合，所有的事物都是对象，例如字符串、数值、数组、函数等。

- 属性：事物的特征，在对象中用属性来表示（常用名词）<br />
- 方法：事物的行为，在对象中用方法来表示（常用动词）
<a name="VCGBy"></a>
### 创建对象的三种方式
<a name="NPEyY"></a>
#### 一、利用字面量创建对象  {花括号里采取键值对的形式表示}
var 对象名 = {属性A : 值 ，属性B : 值...}<br />访问对象的属性

- 对象里面的属性调用 : 对象.属性名 ，这个小点 . 就理解为“ 的 ”  <br />

对象里面属性的另一种调用方式 : 对象[‘属性名’]，注意方括号里面的属性必须加         引号      <br />示例代码如下<br />console.log(star.name)     // 调用名字属性<br />console.log(star['name'])  // 调用名字属性

- 调用对象的方法

对象里面的方法调用：对象.方法名( ) ，注意这个方法名字后面一定加括号 <br />示例代码如下<br />star.sayHi( );  <br />

<a name="8xJMJ"></a>
#### 二、利用 new Object 创建对象 
var andy = new Obect( );<br />//给空对象添加属性和方法<br />andy.name = 'pink';<br />andy.age = 18;<br />andy.sex = '男';<br />andy.sayHi = function( ){<br />        alert('大家好啊~');<br />}<br />

<a name="FIG2s"></a>
#### 三、使用构造函数创建对象
构造函数

- 构造函数：是一种特殊的函数，主要用来初始化对象，即为对象成员变量赋初始值，它总与 new 运算符一起使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封装到这个函数里面。<br />
- 构造函数的封装格式：<br />

function 构造函数名(形参1,形参2,形参3) {<br />     this.属性名1 = 参数1;<br />     this.属性名2 = 参数2;<br />     this.属性名3 = 参数3;<br />     this.方法名 = 函数体;<br />}<br />//调用构造函数<br />var obj = new 构造函数名(实参1，实参2，实参3)<br />注意事项

1. 构造函数约定首字母大写。<br />
1. 函数内的属性和方法前面需要添加 this ，表示当前对象的属性和方法。<br />
1. 构造函数中不需要 return 返回结果。
1. 当我们创建对象的时候，必须用 new 来调用构造函数
<a name="9AEZH"></a>
### 遍历对象 for( 变量 in 对象名称)   /for of
for-in是ES5标准，遍历的是key（可遍历对象、数组或字符串的key(不要遍历数组，遍历顺序可能随机)）；for-of是ES6标准，遍历的是value（可遍历对象、数组或字符串的value）。<br />for (var k in obj) {<br />    console.log(k);      // 这里的 k 是属性名<br />    console.log(obj[k]); // 这里的 obj[k] 是属性值<br />}<br />for-of可以简单、正确地遍历数组（不遍历原型method和name）<br />与forEach()不同的是，它可以正确响应break、continue和return语句。<br />因此建议是使用for-of遍历数组，因为for-of遍历的只是数组内的元素，而不包括数组的原型属性method和索引name。<br />
<br />简单总结就是，for in遍历的是数组的索引（即键名），而for of遍历的是数组元素值。<br />for-in总是得到对象的key或数组、字符串的下标。<br />for-of总是得到对象的value或数组、字符串的值，另外还可以用于遍历Map和Set。<br />

<a name="Dj7ag"></a>
### 内置对象
JavaScript 中的对象分为3种  自定义对象 、内置对象、 浏览器对象
<a name="PLZSD"></a>
### **一、宿主对象：**
宿主对象就是执行JS脚本的环境提供的对象。对于嵌入到网页中的JS来说，其宿主对象就是浏览器提供的对象，所以又称为浏览器对象，如IE、Firefox等浏览器提供的对象。不同的浏览器提供的宿主对象可能不同，即使提供的对象相同，其实现方式也大相径庭！这会带来浏览器兼容问题，增加开发难度。浏览器对象有很多，如Window和Documen，Element，form，image，等等。<br />DOM对象：就是HTML标签寄放在javascript中，叫作对象。即用JavaScript可以操作HTML标签<br />BOM对象：是把浏览器窗口及其浏览器的组成部分寄放在JavaScript中，叫作对象，即可以用JavaScript操作浏览器窗口和它的组成部分。
<a name="pToS9"></a>
### **二、内部对象（JavaScript语言自身的对象）**
**   1. 内置对象**<br />官方的代码创建好了，所以，叫作内置对象（这句话需要深思）<br />内置对象，就是不用创建，可以直接使用的对象，如：Math。函数中的arguments和this；事件处理函数中的event对象等等，都是直接使用，而不用new的。<br />如：Math，arguments，this，event等等<br />**     2.本地对象**<br />需要程序员自己new的对象，所以，叫作本地对象（这句话需要深思）<br />本地的意思可以简单理解为程序员的代码。对于程序员角色来说，本地就是自己的代码了。<br />如：<br />Date要使用，必须new；<br />Array要使用也必须new（方括号简写的方式也是new出来的），<br />Set，<br />Map，<br />XMLHttpRequest<br />RegExp<br />Promise<br />等等
<a name="SPm7u"></a>
#### Math对象，挂在 window身上
	Math 对象不是构造函数，所以我们不需要new 来调用。它具有数学常数和函数的属性和方法。跟数学相关的运算（求绝对值，取整、最大值等）可以使用 Math 中的成员。<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612102723705-9a30669d-2ee8-426e-b33f-408878bb063c.png#align=left&display=inline&height=283&margin=%5Bobject%20Object%5D&name=image.png&originHeight=369&originWidth=761&size=31046&status=done&style=none&width=584)<br />**获取指定范围内的随机整数**<br />function getRandom(min, max) {<br />  return Math.floor(Math.random( ) * (max - min + 1)) + min;  <br />}<br />
<br />**Javascript中的Math.max方法可以求出给定参数中最大的数。** <br />> Math.max('1','2','3.1','3.2')            < 3.2<br />> Math.min(1,0,-1)           < -1 <br /> **但如果是数组，就不能这样调用了。**<br />此时就用到了apply方法：

调用函数，并用指定对象替换函数的 this 值，同时用指定数组替换函数的参数。<br />apply([thisObj[,argArray]])<br />thisObj    可选。 要用作 this 对象的对象。<br />argArray  可选。 要传递到函数的一组参数。  //详见JS基础案例中apply输出最大值
<a name="ZKnot"></a>
#### 日期对象
Date 对象和 Math 对象不一样，Date是一个构造函数，所以使用时需要实例化后才能使用其中具体方法和属性。Date 实例用来处理日期和时间

- 使用Date实例化日期对象
   - 获取当前时间必须实例化：<br />

var now = new Date( );

   - 获取指定时间的日期对象(三种写法)

var future = new Date( '2020/10/21' );<br />console.log(new Date ( 2020,10, 21 ));<br />console.log(new Date ( "2020,10,21" ));<br />注意：如果创建实例时并未传入参数，则得到的日期对象是当前时间对应的日期对象

- 通过Date实例获取总毫米数

      总毫秒数的含义：基于1970年1月1日（世界标准时间）起的毫秒数

- 获取总毫秒数

// 实例化Date对象<br />var now = new Date( );<br />// 1. 用于获取对象的原始值<br />console.log(date.valueOf( ))  <br />console.log(date.getTime( ))  <br />// 2. 简单写可以这么做<br />var now = + new Date( );    <br />// 3. HTML5中提供的方法，有兼容性问题<br />var now = Date.now( );<br />**获取年月日时间**<br />const _date = new Date( 形参 );<br />const _year = _date.getFullYear();<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612104468644-ab48c92f-a74c-4fd5-8405-f124eb58ac54.png#align=left&display=inline&height=257&margin=%5Bobject%20Object%5D&name=image.png&originHeight=277&originWidth=702&size=82904&status=done&style=none&width=652)<br />假设某个函数  **arr**.**padStart**(字符串长度，缺的以什么补齐 )    arr.padStart( 字符串长度，缺的以什么补齐 )  一样,如果省略第二个参数，默认使用空格补全长度。<br />padEnd的用法和padStart一样，一个是在开头补全，一个是在末尾进行补全。<br />**该方法一定要是字符串使用**
<a name="i7zbq"></a>
#### 数组对象
以创建数组的两种方式创建<br />const arr =  [1,2,3,4,5] <br />const arr1 = new Array( );<br />其中用new Array( )方式创建的

      - 如果只传入一个参数，则参数规定了数组的长度  new Array(8 )  数组长度为8
      - 如果传入了多个参数，则参数称为数组的元素
<a name="K9utD"></a>
#### 检测是否为数组 
<a name="2BWJh"></a>
##### instance of    既可以检测数组也可以检测对象，of后面为空格
```javascript
var arr = [1, 23];
var obj = {};
console.log(arr instanceof Array); // true
console.log(obj instanceof Object); //  true
```
<a name="nVh7n"></a>
##### Array.isArray()
Array.isArray(数组名称)  用于判断一个对象是否为数组，是 HTML5 中提供的方法
<a name="BVIlk"></a>
### 字符串对象
<a name="fpyvN"></a>
#### 基本包装类型
为了方便操作基本数据类型，JavaScript 还提供了三个特殊的引用类型：String、Number和 Boolean。基本包装类型就是把简单数据类型包装成为复杂数据类型，这样基本数据类型就有了属性和方法。<br />
<br />js 会把基本数据类型包装为复杂数据类型，其执行过程如下 ：<br />// 1. 生成临时变量，把简单类型包装为复杂数据类型<br />var temp = new String('andy');<br />// 2. 赋值给我们声明的字符变量<br />str = temp;<br />// 3. 销毁临时变量<br />temp = null;
<a name="wiiJn"></a>
#### 字符串的不可变
指的是里面的值不可变，虽然看上去可以改变内容，但其实是地址变了，内存中新开辟了一个内存空间。<br />当重新给字符串变量赋值的时候，变量之前保存的字符串不会被修改，依然在内存中重新给字符串赋值，会重新在内存中开辟空间，这个特点就是字符串的不可变。<br />由于字符串的不可变，在**大量拼接字符串**的时候会有效率问题
<a name="PwSB8"></a>
### href和src
总结：href用于建立当前页面与引用资源之间的关系（链接），而src则会替换当前标签。遇到href，页面会并行加载后续内容；而src则不同，浏览器需要加载完毕src的内容才会继续往下走。
<a name="b8tr7"></a>
### 路径
“./”：代表目前所在的目录。<br />“../”：代表上一层目录。<br />“/”：代表根目录。
<a name="okz3P"></a>
### toUpperCase() /toLowerCase() 方法
stringObject.toUpperCase()<br />toUpperCase() 方法用于把字符串转换为大写。<br />toLowerCase() 方法用于把字符串转换为小写

<a name="EchVW"></a>
### 是否加分号的情况
<a name="PAkjO"></a>
#### ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615109314368-6c1d6134-72d5-4160-928b-3acb147c060d.png#align=left&display=inline&height=28&margin=%5Bobject%20Object%5D&name=image.png&originHeight=28&originWidth=433&size=23851&status=done&style=none&width=433)
左中括号，左小括号，加，减，除 这五个开头的语句之前要加 ； 其他的都可以不加
