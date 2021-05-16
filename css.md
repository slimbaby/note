<a name="7M3pv"></a>
## input
<a name="gA3qv"></a>
### <input> 标签的 accept 属性
<form><br />  <input type="file" name="pic" id="pic" `accept="image/gif, image/jpeg"` /><br /></form><br />如果不限制图像的格式，可以写为：accept="image/*"<br />accept 属性只能与 <input type="file"> 配合使用。它规定能够通过文件上传进行提交的文件类型。<br />提示：请避免使用该属性。应该在服务器端验证文件上传。<br />var pwd = $('input [name=password]').val()  [ ]获取属性元素

<input type="text" readonly></input><br />readonly属性，表示只读
<a name="2ILX2"></a>
## 什么是回流（reflow），什么是重绘(repaint)，有什么区别？
<a name="nXe7u"></a>
### html 加载时发生了什么
在页面加载时，浏览器把获取到的HTML代码解析成1个DOM树，DOM树里包含了所有HTML标签，包括display:none隐藏，还有用JS动态添加的元素等。<br />浏览器把所有样式(用户定义的CSS和用户代理)解析成样式结构体<br />DOM Tree 和样式结构体组合后构建render tree, render tree类似于DOM tree，但区别很大，因为render tree能识别样式，render tree中每个NODE都有自己的style，而且render tree不包含隐藏的节点(比如display:none的节点，还有head节点)，因为这些节点不会用于呈现，而且不会影响呈现的，所以就不会包含到 render tree中。我自己简单的理解就是DOM Tree和我们写的CSS结合在一起之后，渲染出了render tree。
<a name="E886K"></a>
### 什么是回流
当render tree中的一部分(或全部)因为元素的规模尺寸，布局，隐藏等改变而需要重新构建。这就称为回流(reflow)。每个页面至少需要一次回流，就是在页面第一次加载的时候，这时候是一定会发生回流的，因为要构建render tree。在回流的时候，浏览器会使渲染树中受到影响的部分失效，并重新构造这部分渲染树，完成回流后，浏览器会重新绘制受影响的部分到屏幕中，该过程成为重绘。
<a name="jPxqZ"></a>
### 什么是重绘
当render tree中的一些元素需要更新属性，而这些属性只是影响元素的外观，风格，而不会影响布局的，比如background-color。则就叫称为重绘。
<a name="eXH6b"></a>
### 区别：
他们的区别很大：<br />回流必将引起重绘，而重绘不一定会引起回流。比如：只有颜色改变的时候就只会发生重绘而不会引起回流<br />当页面布局和几何属性改变时就需要回流<br />比如：添加或者删除可见的DOM元素，元素位置改变，元素尺寸改变——边距、填充、边框、宽度和高度，内容改变
<a name="m6ZAT"></a>
### 扩展：
<a name="rGayp"></a>
##### 浏览器的帮忙
所以我们能得知回流比重绘的代价要更高，回流的花销跟render tree有多少节点需要重新构建有关系<br />因为这些机制的存在，所以浏览器会帮助我们优化这些操作，浏览器会维护1个队列，把所有会引起回流、重绘的操作放入这个队列，等队列中的操作到了一定的数量或者到了一定的时间间隔，浏览器就会flush队列，进行一个批处理。这样就会让多次的回流、重绘变成一次回流重绘。
<a name="YWl7O"></a>
##### 自己的优化
但是靠浏览器不如靠自己，我们可以改变一些写法减少回流和重绘<br />比如改变样式的时候，不去改变他们每个的样式，而是直接改变className 就要用到cssText 但是要注意有一个问题，会把原有的cssText清掉，比如原来的style中有’display:none;’，那么执行完上面的JS后，display就被删掉了。<br />为了解决这个问题，可以采用cssText累加的方法，但是IE不支持累加，前面添一个分号可以解决。<br />还有添加节点的时候比如要添加一个div里面有三个子元素p，如果添加div再在里面添加三次p，这样就触发很多次回流和重绘，我们可以用cloneNode(true or false) 来避免，一次把要添加的都克隆好再appened就好了，还有其他很多的方法就不一一说了<br />
<br />bootstrap引入后<br />生成table模板的快捷键:bs3-table(下拉可选)<br />生成头部模板的快捷键  bs3-panel:primary(蓝色头部，下拉可选)<br />生成输入框快捷键   bs3-input-group-addon：...(下拉可选)
<a name="eV6Em"></a>
### 什么是CSS hack
由于不同厂商的流览器或某浏览器的不同版本（如IE6-IE11,Firefox/Safari/Opera/Chrome等），对CSS的支持、解析不一样，导致在不同浏览器的环境中呈现出不一致的页面展现效果。这时，我们为了获得统一的页面效果，就需要针对不同的浏览器或不同版本写特定的CSS样式，我们把这个针对不同的浏览器/不同版本写相应的CSS code的过程，叫做CSS hack!
<a name="e05706e1"></a>
#### CSS Hack大致有3种表现形式，
CSS属性前缀法、选择器前缀法以及IE条件注释法（即HTML头部引用if IE）Hack<br />
<br />属性前缀法(即类内部Hack)：例如 IE6能识别下划线"_"和星号" * "，IE7能识别星号" * "，但不能识别下划线"_"，IE6~IE10都认识"\9"，但firefox前述三个都不能认识。<br />选择器前缀法(即选择器Hack)：例如 IE6能识别*html .class{}，IE7能识别*+html .class{}或者*:first-child+html .class{}。<br />IE条件注释法(即HTML条件注释Hack)：针对所有IE(注：IE10+已经不再支持条件注释)： <!--[if IE]>IE浏览器显示的内容 <![endif]-->，针对IE6及以下版本： <!--[if lt IE 6]>只在IE6-显示的内容 <![endif]-->。这类Hack不仅对CSS生效，对写在判断语句里面的所有代码都会生效。<br />具体后面碰到再研究<br />


