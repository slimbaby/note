<a name="lHO2t"></a>
## 目标
- 能够说出使用let关键字声明变量的特点<br />
- 能够使用解构赋值从数组中提取值<br />
- 能够说出箭头函数拥有的特性<br />
- 能够使用剩余参数接收剩余的函数参数<br />
- 能够使用拓展运算符拆分数组<br />
- 能够说出模板字符串拥有的特性<br />
<a name="NbzJ4"></a>
## ES6
泛指2015年6月之后的JavaScript版本
<a name="oR3Am"></a>
## 一、let
ES6中新增了用于声明变量的关键字let  (防止循环变量变成全局变量)

- let声明的变量只在所处于的块级有效
- 不存在变量提升
- 暂时性死区   //利用let声明的变量会绑定在这个块级作用域，不会受外界的影响
<a name="h1H9R"></a>
## 二、const
声明常量，常量就是值（内存地址）不能变化的量

- 具有块级作用域
- 声明常量时必须赋值
- 常量赋值后，值不能修改
- 既然是常量不能重新进行赋值，如果是基本数据类型，不能更改值，如果是复杂数据类型，不能更改地址值(复杂数据类型可以改属性值)<br />
- 声明 const时候必须要给**定值**

**
<a name="NCIM1"></a>
## 三、let、const、var 的区别

- 使用 var 声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象<br />
- 使用 let 声明的变量，其作用域为该语句所在的代码块内，不存在变量提升<br />
- 使用 const 声明的是常量，在后面出现的代码中不能再修改该常量的值<br />

![](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612005953545-8a76f586-be04-4e99-ba93-590bc535aa63.png#align=left&display=inline&height=136&margin=%5Bobject%20Object%5D&originHeight=136&originWidth=551&size=0&status=done&style=none&width=551)<br />
<br />**只有var声明的变量挂在window上，let const 定义的都挂在script身上**<br />**<br />ES5 只有两种声明变量的方法：`var`命令和`function`命令。ES6 除了添加`let`和`const`命令，另外两种声明变量的方法：`import`命令和`class`命令。所以，ES6 一共有 **6 **种声明变量的方法
<a name="uSal4"></a>
## 四、解构赋值
只要某种数据结构具有 Iterator 接口，都可以采用数组形式的解构赋值

<a name="rXCAp"></a>
### 一、数组解构
let [变量名1，变量名2，变量名3] = [1,2,3]
```javascript
let [a, b, c] = [1, 2, 3];
 console.log(a)//1
 console.log(b)//2
 console.log(c)//3
//如果解构不成功，变量的值为undefined
```
<a name="iZkWe"></a>
### 二、对象解构
```javascript
let person = { name: 'zhangsan', age: 20 }; 
 let { name, age } = person;
 console.log(name); // 'zhangsan' 
 console.log(age); // 20

 let {name: myName, age: myAge} = person; // myName myAge 属于别名
 console.log(myName); // 'zhangsan' 
 console.log(myAge); // 20
```

- 解构赋值就是把数据结构分解，然后给变量进行赋值
- 如果结构不成功，变量跟数值个数不匹配的时候，变量的值为undefined<br />
- 数组解构用中括号包裹，多个变量用逗号隔开，对象解构用花括号包裹，多个变量用逗号隔开<br />
- 利用解构赋值能够让我们方便的去取对象中的属性跟方法
- let { , b}={1,2}        //  b=2
<a name="DMMMM"></a>
## Set 和 Map
<a name="IaI7a"></a>
### Set
定义: Set 对象允许你存储任何类型的唯一值，无论是原始值或者是对象引用，Set对象是值的集合，你可以按照插入的顺序迭代它的元素。Set中的元素只会出现一次，即 Set 中的元素是唯一的<br />Set本身是一个构造函数，用来生成 Set 数据结构<br />**基本使用**

-  语法

new Set([iterable]) 接收一个数组（或者具有 iterable 接口的其他数据结构）, 返回一个新的**Set对象**

1. const set = new Set([1,2,1,2])  
1. console.log(set) // {1,2}  

上面代码可以看出 Set 是可以去除数组中的重复元素<br />**属性**

-  size: 返回集合中所包含的元素的数量 
1. console.log(new Set([1,2,1,2]).size) // 2 普通对象没有这个方法

**操作方法**

-  add(value): 向集合中添加一个新的项
-  delete(value): 从集合中删除一个值
-  has(value): 如果值在集合中存在，返回ture, 否则返回false
-  clear(): 移除集合中的所有项 
1. let set = new Set()  
1. set.add(1)  
1. set.add(2)  
1. set.add(2)  
1. set.add(3)  
1. console.log(set) // {1,2,3}  
1. set.has(2) // true  
1. set.delete(2)    
1. set.has(2) // false  
1. set.clear()  

**遍历方法**

-  keys(): 返回键名的遍历器
-  values(): 返回键值的遍历器
-  entries(): 返回键值对的遍历器
-  forEach(): 使用回调函数遍历每个成员 
1. let set = new Set([1,2,3,4])  
1. // 由于set只有键值，没有键名，所以keys() values()行为完全一致  
1. console.log(Array.from(set.keys())) // [1,2,3,4]  
1. console.log(Array.from(set.values())) // [1,2,3,4]  
1. console.log(Array.from(set.entries())) //  [[1,1],[2,2],[3,3],[4,4]]  
1. set.forEach((item) =**>** { console.log(item)}) // 1,2,3,4 
1. **应用场景**

因为 Set 结构的值是唯一的，我们可以很轻松的实现以下

1. // 数组去重  
1. let arr = [1, 1, 2, 3];  
1. let unique = [... new Set(arr)];  
1. let a = new Set([1, 2, 3]);  
1. let b = new Set([4, 3, 2]);    
1. // 并集  
1. let union = [...new Set([...a, ...b])]; // [1,2,3,4]  
1. // 交集  
1. let intersect = [...new Set([...a].filter(x =**>** b.has(x)))]; [2,3]    
1. // 差集  
1. let difference = Array.from(new Set([...a].filter(x =**>** !b.has(x)))); [1] 
<a name="PqVjm"></a>
#### WeakSet
WeakSet 对象是一些对象值的集合, 并且其中的每个对象值都只能出现一次。在WeakSet的集合中是唯一的<br />WeakSet 的出现主要解决弱引用对象存储的场景, 其结构与Set类似<br />与Set的区别

-  与Set相比，WeakSet 只能是对象的集合，而不能是任何类型的任意值
-  WeakSet集合中对象的引用为弱引用。如果没有其他的对WeakSet中对象的引用，那么这些对象会被当成垃圾回收掉。这也意味着WeakSet中没有存储当前对象的列表。正因为这样，WeakSet 是不可枚举的

WeakSet 的属性跟操作方法与 Set 一致，不同的是 WeakSet 没有遍历方法，因为其成员都是弱引用，弱引用随时都会消失，遍历机制无法保证成员的存在<br />**上面一直有提到弱引用，那弱引用到底是指什么呢？**<br />弱引用是指不能确保其引用的对象不会被垃圾回收器回收的引用，换句话说就是可能在任意时间被回收
<a name="doHDR"></a>
### Map
Map 对象保存键值对，并且能够记住键的原始插入顺序。任何值(对象或者原始值) 都可以作为一个键或一个值。一个Map对象在迭代时会根据对象中元素的插入顺序来进行 — 一个  for...of 循环在每次迭代后会返回一个形式为[key，value]的数组<br />**基本使用**

-  语法

new Map([iterable]) Iterable（迭代） 可以是一个数组或者其他 iterable 对象，其元素为键值对(两个元素的数组，例如: [[ 1, 'one' ],[ 2, 'two' ]])。每个键值对都会添加到新的 Map

1. let map = new Map()  
1. map.set('name', 'vuejs.cn');  
1. console.log(map.get('name')) 

**属性及方法**<br />基本跟 Set 类似，同样具有如下方法属性

-  size: 返回 Map 结构的元素总数 
1. let map = new Map()  
1. map.set('name', 'vuejs.cn'); 
1. console.log(map.size) // 1  
1. console.log(new Map([['name','vue3js.cn'], ['age','18']]).size) // 2 

**操作方法**

-  set(key, value): 向 Map 中加入或更新键值对
-  get(key): 读取 key 对用的值，如果没有，返回 undefined
-  has(key): 某个键是否在 Map 对象中，在返回 true 否则返回 false
-  delete(key): 删除某个键，返回 true, 如果删除失败返回 false
-  clear(): 删除所有元素 
1. let map = new Map()  
1. map.set('name','vue3js.cn')  
1. map.set('age','18') 
1. console.log(map) // Map {"name" =**>** "vuejs.cn", "age" =**>** "18"}  
1. map.get('name') // vue3js.cn   
1. map.has('name') // true  
1. map.delete('name')    
1. map.has(name) // false  
1. map.clear() // Map {}  

**遍历方法**

-  keys()：返回键名的遍历器
-  values()：返回键值的遍历器
-  entries()：返回所有成员的遍历器
-  forEach()：遍历 Map 的所有成员 
1. let map = new Map()  
1. map.set('name','vue3js.cn')  
1. map.set('age','18')   
1. console.log([...map.keys()])  // ["name", "age"]  
1. console.log([...map.values()])  // ["vue3js.cn", "18"]  
1. console.log([...map.entries()]) // [['name','vue3js.cn'], ['age','18']]  
1. // name vuejs.cn  
1. // age 18  
1. map.forEach((value, key) =**>** { console.log(key, value)})  

**应用场景**<br />Map 会保留所有元素的顺序, 是在基于可迭代的基础上构建的，如果考虑到元素迭代或顺序保留或键值类型丰富的情况下都可以使用，下面摘抄自 vue3 源码中依赖收集的核心实现

1. let depsMap = targetMap.get(target)  
1.  if (!depsMap) {  
1.    targetMap.set(target, (depsMap = new Map()))  
1.  }  
1.  let dep = depsMap.get(key)  
1.  if (!dep) {  
1.    depsMap.set(key, (dep = new Set()))  
1.  }  
1.  if (!dep.has(activeEffect)) {  
1.    dep.add(activeEffect)  
1.    activeEffect.deps.push(dep)  
1.    ...  
1.  } 
<a name="Q8nmu"></a>
#### WeakMap
WeakMap 对象是一组键/值对的集合，其中的键是弱引用的。其键必须是对象，而值可以是任意的<br />与Map的区别

-  Map 的键可以是任意类型，WeakMap 的键只能是对象类型
-  WeakMap 键名所指向的对象，不计入垃圾回收机制

WeakMap 的属性跟操作方法与 Map 一致，同 WeakSet 一样，因为是弱引用，所以 WeakSet 也没有遍历方法<br />**类型的转换**

-  Map 转为 Array 
1. // 解构  
1. const map = new Map([[1, 1], [2, 2], [3, 3]])  
1. console.log([...map]) // [[1, 1], [2, 2], [3, 3]]  
1. // Array.from()  
1. const map = new Map([[1, 1], [2, 2], [3, 3]])  
1. console.log(Array.from(map)) // [[1, 1], [2, 2], [3, 3]] 
-  Array 转为 Map 
7. const map = new Map([[1, 1], [2, 2], [3, 3]])  
7. console.log(map) // Map {1 =**>** 1, 2 =**>** 2, 3 =**>** 3} 
-     Map 转为 Object 
9. // 非字符串键名会被转换为字符串  
9. function mapToObj(map) {  
9.     let obj = Object.create(null)  
9.     for (let [key, value] of map) {  
9.         obj[key] = value  
9.     }  
9.     return obj  
9. }  
9. const map = new Map().set('name', 'vue3js.cn').set('age', '18')  
9. mapToObj(map)  // {name: "vue3js.cn", age: "18"} 
-  Object 转为 Map 
19. let obj = {"a":1, "b":2};  
19. let map = new Map(Object.entries(obj)) 

**总结**

-  Set、Map、WeakSet、WeakMap、都是一种集合的数据结构
-  Set、WeakSet 是[值,值]的集合，且具有唯一性
-  Map 和 WeakMap 是一种[键,值]的集合，Map 的键可以是任意类型，WeakMap 的键只能是对象类型
-  Set 和 Map 有遍历方法，WeakSet 和 WeakMap 属于弱引用不可遍历
<a name="xh0VL"></a>
## ES6模块化语法
<a name="R7DI0"></a>
### 默认导入和导出
导入：import 接收名称 from '模块名称'<br />导出：export default { a,c,show }
<a name="wlUUN"></a>
### 按需导入和导出
导入：import {s1,s2 as ss2,say} from './m1.js';<br />导出：export let s1 = 'aaa';//向外按需导出变量 s1<br />    export let s2 = 'ccc';//向外按需导出变量 s2<br />    export function say (){} //向外按需导出方法 say
<a name="xdiWd"></a>
### 直接导入并执行模块代码
//m1.js<br />for (let i = 0; i < 3; i++) {<br />	console.log(i);<br />}<br />//index.js<br />**import './m1.js'**
