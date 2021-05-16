<a name="jMoRn"></a>
## ES5中新增的数组方法
<a name="KPIc6"></a>
### 1、arr.forEach（function()）
//相当于数组遍历的 for循环 没有返回值，在forEach 里面 return 不会终止迭代<br /> arr.forEach(function(value, index, array) {<br />       //参数一是:数组元素；<br />       //参数二是:数组元素的索引；<br />       //参数三是:当前的数组本身；<br /> })
<a name="byaYy"></a>
### 2、arr.filter(function()）
筛选符合条件的元素，并将元素返回一个新数组，需要用新变量去接收。<br />const arr = [12, 66, 4, 88, 3, 7];<br />const newArr = arr.filter(function(value, index,array) <br />    //参数一是:数组元素；<br />     //参数二是:数组元素的索引；<br />     //参数三是:当前的数组本身；<br />     return value >= 20;   //需要return<br />  });<br />  console.log(newArr);//[66,88] //返回值是一个新数组
<a name="8bYOP"></a>
### 3、arr.some(function()）
some 查找数组中是否有满足条件的元素，返回值是布尔值,只要查找到满足条件的一个元素就立马终止循环。<br />         如果查询数组中唯一的元素, 用some方法更合适,在some 里面 遇到 return true 就是终止遍历 迭代效率更高<br /> var arr = [10, 30, 4];<br /> var flag = arr.some(function(value,index,array) {<br />     //参数一是:数组元素<br />     //参数二是:数组元素的索引<br />     //参数三是:当前的数组<br />     return value < 3;<br />  });<br />console.log(flag);  //false
<a name="cuxFL"></a>
### 4、arr.every(function());
`.every()` 方法将检查数组中的所有元素是否通过提供的条件。<br />如果数组中的所有元素都通过条件，则该方法将返回 true。否则，它将返回 false。<br />var arr = [10, 30, 4];<br />    var flag = arr.every(function (value, index, array) {<br />      //参数一是:数组元素<br />      //参数二是:数组元素的索引<br />      //参数三是:当前的数组<br />      return value > 3;<br />    });<br />    console.log(flag);  // ture
<a name="IGmaU"></a>
### 5、arr.find(function()）
返回数组中满足提供的测试函数的第一个元素的值。否则返回undefined，会遍历完才停止。<br />   var arr = [10, 30, 4, 6, 5, 8];<br />        var flag = arr.find(function (value, index, array) {<br />  //参数一是:数组元素<br />         //参数二是:数组元素的索引<br />         //参数三是:当前的数组<br />            return value == 4;<br />        });<br />        console.log(flag);      //  返回4；
<a name="6628b5bb"></a>
#### findIndex()
用于找出第一个符合条件的数组成员的位置索引，如果没有找到返回-1
```javascript
let ary = [1, 5, 10, 15];
let index = ary.findIndex((value, index) => value > 9); 
console.log(index); // 2
```
<a name="1mcHb"></a>
### 6、arr.map(function())
Array.map((数组元素, 数组元素的下标, 数组本身)=>{ }[,thisArray])<br />1、调用时在数组内部发生了一次从 0 到 length-1 的循环；<br />2、返回值是由每次循环调用的返回值所组成的数组；<br />3、thisArray 可选，指定函数中的 this，注意箭头函数<br />不会修改原数组<br />和foreach的不同处：**map有一个返回值，foreach则没有返回值，**当函数的执行部分{  }什么都不写时，这个返回值是一个和原数组等长度的，全部由undefined组成的元素的**新数组**，而forEach仅仅是一个undefined
```javascript
var arr1 = ['a', 'c', 'd'];
		console.log(arr1.map(function (parameter, index, arr) {})
	);     //[undefined, undefined, undefined]
```
当return 后面返回的数组参数a时，就可以得到原来数组元素一模一样的一个新数组，forEach则不能
```javascript
var arr1 = ['a', 'c', 'd'];
		console.log(arr1.map(function (parameter, index, arr) { return parameter})
	);        //["a", "c", "d"]
```
这样的话我们就可**以对a操作**，比如+10，那这样我们就得到比原数组每一个元素都大10的新数组；我们还可以*10,就得到元素大10倍的新数组等等

Foreach和map一起记，find和filter一起记，some和every一起记。
<a name="4lSDv"></a>
### 7、arr.reduce(function())
```
语法    arr.reduce(callback,[initialValue])
callback （执行数组中每个值的函数，包含四个参数）

    1、previousValue （上一次调用回调返回的值，或者是提供的初始值（initialValue））
    2、currentValue （数组中当前被处理的元素）
    3、index （当前元素在数组中的索引）
    4、array （调用 reduce 的数组）

initialValue （作为第一次调用 callback 的第一个参数。）
```
例子
```
var arr = [1, 2, 3, 4];
var sum = arr.reduce(function(prev, cur, index, arr) {
    console.log(prev, cur, index);
    return prev + cur;
})
console.log(arr, sum);
打印结果：
1 2 1
3 3 2
6 4 3
[1, 2, 3, 4] 10

//这里可以看出，上面的例子index是从1开始的，第一次的prev的值是数组的第一个值。数组长度是4，但是reduce函数循环3次。

var  arr = [1, 2, 3, 4];
var sum = arr.reduce(function(prev, cur, index, arr) {
    console.log(prev, cur, index);
    return prev + cur;
}，0) //注意这里设置了初始值
console.log(arr, sum);
0 1 0
1 2 1
3 3 2
6 4 3
[1, 2, 3, 4] 10
```
这个例子index是从0开始的，第一次的prev的值是我们设置的初始值0，数组长度是4，reduce函数循环4次。<br />结论：`如果没有提供initialValue，reduce 会从索引1的地方开始执行 callback 方法，跳过第一个索引。如果提供initialValue，从索引0开始。`**一般来说我们提供初始值通常更安全,如果遍历的数组为空，则会报错**<br />**reduce的高级用法**<br />（1）计算数组中每个元素出现的次数
```
let names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice'];
let nameNum = names.reduce((pre,cur)=>{
  if(cur in pre){
    pre[cur]++
  }else{
    pre[cur] = 1 
  }
  return pre
},{})
console.log(nameNum); //{Alice: 2, Bob: 1, Tiff: 1, Bruce: 1}
```
（2）数组去重
```
let arr = [1,2,3,4,4,1]
let newArr = arr.reduce((pre,cur)=>{
    if(!pre.includes(cur)){
      return pre.concat(cur)
    }else{
      return pre
    }
},[])
console.log(newArr);// [1, 2, 3, 4]
```
（3）将二维数组转化为一维
```
let arr = [[0, 1], [2, 3], [4, 5]]
let newArr = arr.reduce((pre,cur)=>{
    return pre.concat(cur)
},[])
console.log(newArr); // [0, 1, 2, 3, 4, 5]
```
（3）将多维数组转化为一维
```
let arr = [[0, 1], [2, 3], [4,[5,6,7]]]
const newArr = function(arr){
   return arr.reduce((pre,cur)=>pre.concat(Array.isArray(cur)?newArr(cur):cur),[])
}
console.log(newArr(arr)); //[0, 1, 2, 3, 4, 5, 6, 7]
```
（4）、对象里的属性求和
```
var result = [
    {
        subject: 'math',
        score: 10
    },
    {
        subject: 'chinese',
        score: 20
    },
    {
        subject: 'english',
        score: 30
    }
];
var sum = result.reduce(function(prev, cur) {
    return cur.score + prev;
}, 0);
console.log(sum) //60
```


<a name="XFyKu"></a>
### 6、剩余参数...args
剩余参数语法允许我们将一个不定数量的参数表示为一个数组，不定参数定义方式，这种方式很方便的去声明不知道参数情况下的一个函数
```javascript
function sum (first, ...args) {
     console.log(first); // 10
     console.log(args);  // [20, 30] 
 }
 sum(10, 20, 30)
```
<a name="8NB1r"></a>
### 六、添加删除数组元素的方法push()
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612103460066-71c1095e-28dc-4a41-8781-e5f656f011b1.png#align=left&display=inline&height=211&margin=%5Bobject%20Object%5D&name=image.png&originHeight=236&originWidth=718&size=95091&status=done&style=none&width=641)
<a name="isF4q"></a>
### 七、数组排序
![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612103493921-d47d2eb2-c7ec-4881-8d8b-15832570ab1a.png#align=left&display=inline&height=100&margin=%5Bobject%20Object%5D&name=image.png&originHeight=110&originWidth=700&size=41907&status=done&style=none&width=639)<br />arr.reverse( )<br />注意：sort方法需要传入参数来设置升序、降序排序

- 如果传入“function(a,b){ return a-b;}”，则为升序<br />
- 如果传入“function(a,b){ return b-a;}”，则为降序<br />

例：arr.sort(function (a, b) { return a - b; })
<a name="zfW8d"></a>
### 八、数组转换为字符串join/toString
数组中有把数组转化为字符串的方法，部分方法如下表<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612104687883-569c3eda-cde8-4153-91d5-ced1078bdbc0.png#align=left&display=inline&height=94&margin=%5Bobject%20Object%5D&name=image.png&originHeight=114&originWidth=707&size=38741&status=done&style=none&width=582)<br />注意：join方法如果不传入参数，则按照 “ , ”拼接元素<br />其他课后了解<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612104730060-161a4a43-b862-43b3-a365-9e41b0e18a4f.png#align=left&display=inline&height=126&margin=%5Bobject%20Object%5D&name=image.png&originHeight=152&originWidth=718&size=57407&status=done&style=none&width=597)<br />arr.slice(-1),指向数组最后一个元素！！负数时，就是倒着来的。
<a name="bKOCj"></a>
### 九、伪数组
**伪数组是一个对象**<br />1、有length属性，长度不可变<br />2、**不能使用数组的方法**<br />3、可以用原型辨别：没有-proto-和prototype属性<br />4、用 arr instanceof Array   //false<br />          arr instanceof Object   //true<br />(亲测有效)
<a name="NxCLg"></a>
#### 伪数组转为真数组
对DOM元素进行map、forEach操作时候需要进行遍历，伪数组遍历会报错：'elem.map is not a function',为了避免这个问题，需要进行转换。
<a name="21JiI"></a>
### 第一种
```
var arr = [];
for(var i =0; i<weiArr.length;i++){
  arr[i] = weiArr[i];
}
console.log(arr);
```
<a name="eGmcP"></a>
### 第二种
```
var arr = [];
for (var i=0;i<weiArr.length;i++){
  arr.push(weiArr[i]);
}
console.log(arr);
```
<a name="qBEC3"></a>
### 第三种
```
var arr = [];
arr.push.apply(arr.weiArr);
console.log(arr);
```
<a name="LnYp6"></a>
### 第四种
```
var arr = [];
arr = arr.concat.apply(arr.weiArr);
console.log(arr);
```
<a name="VDdcW"></a>
### 第五种
```
var arr = Array.prototype.slice.call(weiArr,0);
console.log(arr);
```
<a name="gkLGi"></a>
### 第六种
```
var  arr =array.form(weiArr)
```
<a name="0bM25"></a>
## ES6中新增的数组方法
<a name="jsWhy"></a>
### 一、ES6 的内置对象扩展
扩展运算符可以将数组或者对象转为用逗号分隔的参数序列<br />let ary = [1, 2, 3];<br /> ...ary         // 1, 2, 3  //拓展运算符<br /> console.log(...ary);    // 1 2 3,相当于下面的代码<br /> console.log(1,2,3);
<a name="7eUqt"></a>
### 二、合并数组
// 方法一  （对象也可以用这个方法）<br /> let ary1 = [1, 2, 3];<br /> let ary2 = [4, 5, 6];<br /> let ary3 = [...ary1, ...ary2];           // [ 1, 2, 3, 4, 5, 6]<br /> // 方法二  <br /> ary1.push(...ary2);  <br />console.log( ary1 )；           // [ 1, 2, 3, 4, 5, 6]         push方法会改变原数组，若直接打印返回的结果为数组长度
<a name="MwLSo"></a>
### 三、将类数组或可遍历对象转换为真正的数组
**1、**let oDivs = document.getElementsByTagName('div');  <br />oDivs = [...oDivs];      //先加...变为用逗号分隔的参数序列，再加[ ]变成数组。<br />**2、将字符串转换为数组：**<br />let  str = 'hello world!';<br />console.log(Array.from(str)) // ["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d", "!"]
<a name="gpKe3"></a>
### 四、构造函数方法：Array.from()
Array.from()方法就是将一个伪数组对象（要有length属性，如果没有length属性，那么转换后的数组是一个空数组）或者可遍历对象转换成一个真正的数组
```javascript
//定义一个集合
let arrayLike = {
    '0': 'a',
    '1': 'b',
    '2': 'c',
    length: 3
};  
//转成数组
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
```
方法还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组
```javascript
let arrayLike = {  
     "0": 1,
     "1": 2,
     "length": 2
 }
 let newAry = Array.from(arrayLike, item => item *2)//[2,4]
```
要将一个类数组对象转换为一个真正的数组，必须具备以下条件：<br />　　1、该类数组对象必须具有length属性，用于指定数组的长度。如果没有length属性，那么转换后的数组是一个空数组。<br />　　2、该类数组对象的**属性名**必须为**数值型**或**字符串型**的数字，如果为其他数据类型则会返回undefined。<br />　　ps: 该类数组对象的属性名可以加引号，也可以不加引号<br />
<a name="mFtaB"></a>
### 五、实例方法：includes()
判断某个数组是否包含给定的值，返回布尔值。<br />字符号也可使用此方法<br />[1, 2, 3].includes(2)      // true <br />他和some的区别在于，它只能查询一层基本数据，如果是数组元素包含对象，就没法识别，要用some进行遍历
<a name="lQWAp"></a>
### 六、Set 数据结构
ES6 提供了新的数据结构  Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。<br />Set本身是一个构造函数，用来生成  Set  数据结构<br />const s = new Set();<br />Set函数可以接受一个数组作为参数，用来初始化。<br />const set = new Set([1, 2, 3, 4, 4]);//{1, 2, 3, 4}
<a name="1yR5v"></a>
##### 实例方法

- add(value)：添加某个值，返回 Set 结构本身<br />
- delete(value)：删除某个值，返回一个布尔值，表示删除是否成功<br />
- has(value)：返回一个布尔值，表示该值是否为 Set 的成员<br />
- clear()：清除所有成员，没有返回值<br />

 const s = new Set();<br /> s.add(1).add(2).add(3); // 向 set 结构中添加值 <br /> s.delete(2)             // 删除 set 结构中的2值   <br /> s.has(1)                // 表示 set 结构中是否有1这个值 返回布尔值 <br /> s.clear()               // 清除 set 结构中的所有值<br /> //注意：删除的是元素的值，不是代表的索引
<a name="gPocK"></a>
##### 遍历
Set 结构的实例与数组一样，也拥有forEach方法，用于对每个成员执行某种操作，没有返回值。<br />s.forEach(value => console.log(value))
