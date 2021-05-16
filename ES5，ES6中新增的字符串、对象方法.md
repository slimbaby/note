<a name="ofLen"></a>
## ES5
<a name="U6AC8"></a>
### 1、trim()方法去除字符串两端的空格 
str.trim()   指挥去除两端的空格，不会去除字符串中间的空格
<a name="mxf67"></a>
### 2、根据字符返回位置
案例：查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数

1. 先查找第一个o出现的位置<br />
1. 然后 只要indexOf 返回的结果不是 -1 就继续往后查找<br />
1. 因为indexOf 只能查找到第一个，所以后面的查找，利用第二个参数，当前索引加1，从而继续查找 
<a name="cwi73"></a>
### 3、根据位置返回字符
字符串通过基本包装类型可以调用部分方法来操作字符串，以下是根据位置返回指定位置上的字符：<br />在上述方法中，charCodeAt方法返回的是指定位置上字符对应的ASCII码，ASCII码对照表如下：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612107134379-7cf76501-20e9-41e7-adb1-58180972e36d.png#align=left&display=inline&height=389&margin=%5Bobject%20Object%5D&name=image.png&originHeight=394&originWidth=580&size=443519&status=done&style=none&width=573)<br />案例：判断一个字符串 'abcoefoxyozzopp' 中出现次数最多的字符，并统计其次数

1. 核心算法：利用 charAt(） 遍历这个字符串<br />
1. 把每个字符都存储给对象， 如果对象没有该属性，就为1，如果存在了就 +1<br />
1. 遍历对象，得到最大值和该字符 	<br />

	注意：在遍历的过程中，把字符串中的每个字符作为对象的属性存储在对象总，对应的属性值是该字符出现的次数（参考题笔记中：找出数组中重复次数最多的元素和重复的次数）
<a name="UIWMj"></a>
### 4、字符串操作方法
字符串通过基本包装类型可以调用部分方法来操作字符串，以下是部分操作方法：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1612107265967-e7b4bfff-aac4-4003-8491-902ff58bb9a0.png#align=left&display=inline&height=164&margin=%5Bobject%20Object%5D&name=image.png&originHeight=203&originWidth=729&size=92094&status=done&style=none&width=590)
<a name="Zi1wO"></a>
#### replace()方法
	replace() 方法用于在字符串中用一些字符替换另一些字符，其使用格式如下：  <br />字符串.replace(被替换的字符串， 要替换为的字符串)；<br />只会替换找到的第一个符合要求的字符，如果要将所有字符串中都符合要求的进行替换可以进行循环遍历或者正则匹配。
<a name="weX7q"></a>
#### split()方法
	split()方法用于切分字符串，它可以将字符串切分为数组。在切分完毕之后，返回的是一个**新数组**。<br />	其使用格式如下：<br />字符串.split("分割字符")
<a name="5ghMg"></a>
#### indexOf()方法,同样适用于数组查重！
此方法返回第一次出现的指定值的调用String对象中的索引，从fromIndex开始搜索，如果未找到该值，则返回-1。
```javascript
string.indexOf(searchValue[, fromIndex])
//searchValue - 表示要搜索的值的字符串。
fromIndex - 调用字符串中用于开始搜索的位置。它可以是0到字符串长度之间的任何整数。默认值为0。
str.indexOf('春', 3)); // 从索引号是 3的位置开始往后查找
返回值
返回找到的匹配项的索引，否则返回-1（如果未找到）
```
<a name="OEh45"></a>
## ES6
<a name="sXN0V"></a>
### 1、模板字符串

- ES6新增的创建字符串的方式，使用反引号定义
- 模板字符串中可以解析变量
- 模板字符串中可以换行
- 在模板字符串中可以调用函数
<a name="ra8mf"></a>
### 二、实例方法：startsWith() 和 endsWith()

- startsWith()：表示参数字符串是否在原字符串的头部，返回布尔值<br />
- endsWith()：表示参数字符串是否在原字符串的尾部，返回布尔值<br />

let str = 'Hello world!';<br />str.startsWith('Hello')  // true  <br />str.endsWith('!')          // true
<a name="Rjr7F"></a>
### 三、实例方法：repeat()
repeat方法表示将原字符串重复n次，返回一个新字符串<br />'hello'.repeat(2)  // "hellohello"<br />
<br />
<br />
<br />
<br />

<a name="MO35I"></a>
# 遍历对象的几种方法
<a name="wBS8T"></a>
## 一、对非Array对象类型的遍历
<a name="lnkGA"></a>
### 1、for in
主要用于遍历对象的可枚举属性，包括自有属性、继承自原型的属性<br />var obj = {"name":"tom","sex":"male"}；<br />Object.defineProperty(obj, "age", {value:"18", enumerable:false});//增加不可枚举的属性age<br />Object.prototype.protoPer1 = function(){console.log("name is tom");};//通过原型链增加属性，为一个函数<br />Object.prototype.protoPer2 = 2;通过原型链增加属性，为一个整型值2<br />console.log("For In : ");<br />for(var a in obj)<br />console.log(a);<br />输出的截图为：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614323008817-175029ba-c949-4e37-ae45-8f6dda8926a7.png#align=left&display=inline&height=104&margin=%5Bobject%20Object%5D&name=image.png&originHeight=224&originWidth=501&size=14966&status=done&style=none&width=233)<br />总结：for in 主要用于遍历对象的可枚举属性(不含Symbol属性)，包括自有属性、继承自原型的属性，示例中的属性age为不可可枚举，所以没有输出。
<a name="DhNgx"></a>
### 2、Object.keys
此方法返回一个数组，元素均为对象自有可枚举的属性<br />var obj = {"name":"tom","sex":"male"}；<br />Object.defineProperty(obj, "age", {value:"18", enumerable:false});//增加不可枚举的属性age<br />Object.prototype.protoPer1 = function(){console.log("name is tom");};//通过原型链增加属性，为一个函数<br />Object.prototype.protoPer2 = 2;通过原型链增加属性，为一个整型值2<br />console.log("Object.keys:")<br />console.log(Object.keys(obj));<br />输出的截图为：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614323450345-0ea7486e-2ad6-49af-b3e1-b1a6f72b3128.png#align=left&display=inline&height=26&margin=%5Bobject%20Object%5D&name=image.png&originHeight=50&originWidth=324&size=6960&status=done&style=none&width=169)<br />总结：Object.keys主要用于遍历对象自有的可枚举属性(不含Symbol属性)，不包括继承自原型的属性和不可枚举的属性。
<a name="Lvm5R"></a>
### 3、Object.getOwnProperty
 var obj = { "name": "tom", "sex": "male" };<br />Object.defineProperty(obj, "age", {value:"18", enumerable:false});//增加不可枚举的属性age<br />Object.prototype.protoPer1 = function(){console.log("name is tom");};//通过原型链增加属性，为一个函数<br />Object.prototype.protoPer2 = 2;通过原型链增加属性，为一个整型值2<br />console.log("Object.getOwnPropertyNames: ");<br />console.log(Object.getOwnPropertyNames(obj));<br />输出的截图为：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614323777412-eec8c4ea-1e67-46c5-98f8-1ab40a3abae1.png#align=left&display=inline&height=31&margin=%5Bobject%20Object%5D&name=image.png&originHeight=57&originWidth=449&size=8498&status=done&style=none&width=241)<br />总结：Object.getOwnProperty主要用于返回对象的自有属性不含Symbol属性，包括可枚举和不可枚举的属性，不包括继承自原型的属性。
<a name="gNPLI"></a>
## 二、对Array对象类型的遍历
<a name="B06hr"></a>
### 1、for in
var arr = [1,2,3,4,5,6];<br />for(var a in arr) console.log(a);<br />输出的截图为：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614324847218-0f98b3bd-4b11-4f01-9f5a-b2d1e025797f.png#align=left&display=inline&height=111&margin=%5Bobject%20Object%5D&name=image.png&originHeight=268&originWidth=541&size=11499&status=done&style=none&width=225)<br />总结：输出为数组对象的index 值。
<a name="bFwLE"></a>
### 2、Object.keys
var arr = [1,2,3,4,5,6];<br />console.log(Object.keys(arr));<br />输出的截图为：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614324899961-2d6f097e-d204-4262-a1e1-be3f569ada31.png#align=left&display=inline&height=33&margin=%5Bobject%20Object%5D&name=image.png&originHeight=46&originWidth=459&size=7815&status=done&style=none&width=330)<br />总结：输出为数组对象的index 值。
<a name="SEApm"></a>
### 3、Object.getOwnProperty
var arr = [1,2,3,4,5,6];<br />console.log(Object.getOwnPropertyNames(arr));<br />输出的截图为：<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1614324928711-84dc8245-114b-4baa-9d2f-1b948db87ad6.png#align=left&display=inline&height=47&margin=%5Bobject%20Object%5D&name=image.png&originHeight=47&originWidth=657&size=9898&status=done&style=none&width=657)<br />总结：输出为数组对象的index 值和数组长度的属性值。<br />

