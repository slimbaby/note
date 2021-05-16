webpack是前端项目的构建工具<br />优点：1、优化项目的性能，比如合并压缩文件等<br />    2、书写更高级的ES代码不用考虑兼容性<br />webpack4.0版本默认约定：打包入口文件是src=>index.js   输出文件是dist=>main.js<br />npm卸载包：npm uninstall 包名称
<a name="7f2d53d7"></a>
### 配置过程：
1、在英文项目文件夹下运行终端，输入npm init -y<br />2、新建src源代码目录文件夹，并在里面创建index.html<br />3、在index.html中创建ul>li{这是第$个li}*9<br />4、安装npm i jquery -S<br />5、运行 npm i webpack webpack-cli<br />6、在项目根目录中，创建名为webpack.config.js的webpack配置文件，并在配置文件中初始化以下基本配置
```javascript
module.exports={
    mode:'development'//这种模式下不会进行代码的压缩与混淆，production生成模式就会压缩和混淆
}
```
7、在package.json配置文件中的scripts节点下，新增dev脚本,在终端中运行npm run dev 命令，启动webpack进行项目打包
```javascript
 "scripts": {
    "dev":"webpack",
  },
```
8、将index.html里引入的js文件路径改为打包完成之后的dist文件夹下的main.js,刷新页面
<a name="Ql7eC"></a>
### 修改打包的入口与出口,配置在webpack.config.js
```javascript
const path = require('path')  导入node.js中专门操作路径的模块
module.exports = {
	entry:path.join(__dirname,'路径地址')，//打包入口文件的路径
  output:{
		path:path.join(__dirname,'路径地址')，//输出文件的存放路径
    filename："输出的文件名称.js"   //输出文件的名称
	}
}
```
<a name="VpCQm"></a>
### 配置webpack自动打包功能
1、运行 npm i webpack-dev-server -D<br />2、修改package.json  中scripts的dev命令   "dev" : "webpack-dev-server"<br />3、index.html文件引入js:<script src="/main.js"></script><br />**只要配置了webpack-dev-server，文件必须要在本地服务器上查看**![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615448774669-2337d0e3-a720-49f3-b846-274967b0679f.png#align=left&display=inline&height=152&margin=%5Bobject%20Object%5D&name=image.png&originHeight=152&originWidth=439&size=7541&status=done&style=none&width=439)****亲测这三个版本可以成功**
<a name="DoXfJ"></a>
### 配置一打开就是首页功能
接下来做首页。url地址一打开就是首页html-webpack-plugin插件就是为了复制html文件,还会把自动打包好的文件，注入到复制出来的页面底部<br />1、npm i html-webpack-plugin -D<br />2、在webpack.config.js中导入插件并配置
```javascript
const HtmlPlugin = require("html-webpack-plugin")
const htmlPlugin = new HtmlPlugin({
    template: "./src/index.html",
    filename: "index.html"
})
module.exports = {
    mode: "development",
    plugins: [htmlPlugin]
}
```
<a name="hgojo"></a>
### 配置自动打开浏览器，热更新和配置浏览器的默认端口号
--open 自动打开浏览器<br />--host 配置IP地址<br />--port 配置端口号<br />--hot 热更新；最新的代码，以打补丁的形式，替换到页面上，加快编译的速度<br />例： "dev" : "webpack-dev-server --open --host 127.0.0.1 --port 3001"
<a name="ajOiJ"></a>
### webpack中的加载器
webpack默认只能打包以.js后缀名结尾的模块，其他后缀需要调用loader才可以正常打包<br />![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1619766966912-5807b1a1-d430-49a6-b774-1b512bd05611.png#align=left&display=inline&height=262&margin=%5Bobject%20Object%5D&name=image.png&originHeight=379&originWidth=856&size=95269&status=done&style=none&width=591)
<a name="kJejn"></a>
#### 打包处理css文件
1、运行npm i style-loader css-loader -D<br />2、在webpack.config.js的module.exports 中添加module属性 -> rules数组中，添加loader规则
```javascript
module:{
	rules:[
    { test:/\.css$/,use:['style-loader','css-loader']}
  ]
}
```
注意：use数组中指定的loader顺序是固定的，多个loader的调用顺序是，从后往前调用
<a name="oSa63"></a>
#### 打包处理less文件
1、运行npm i less-loader less -D<br />2、同上添加打包规则
```javascript
  { test:/\.less$/,use:['style-loader','css-loader','less-loader']}
```
<a name="cqIrb"></a>
#### 打包处理scss文件（名字叫sass,文件后缀是scss）
1、运行npm i sass-loader node-sass -D<br />2、同上添加打包规则
```javascript
 { test:/\.scss$/,use:['style-loader','css-loader','sass-loader']}
```
<a name="Bwn49"></a>
#### 配置postCSS自动添加css的兼容性前缀
1、运行 npm i post-loader autoprefixer -D<br />2、在根目录文件中创建postcss的配置文件  postcss.config.js,并初始化以下配置
```javascript
const autoprefixer = require('autoprefixer')
module.exports = {
	plugins:[autoprefixer]  //挂载插件
}
```
3、在webpack.config.js的module => rules 数组中，修改css的loader规则
```javascript
 { test:/\.css$/,use:['style-loader','css-loader','postcss-loader']}  //加了一个postcss-loader
```
<a name="KDbUI"></a>
#### 打包样式表中的图片和字体文件
1、运行npm i url-loader file-loader -D<br />2、同上添加打包规则(use可以配置成数组，也可以配置成引号引起来的名称)
```javascript
{test:/\.jpg|png|gif|bmp|ttf|eot|svg|woff|woff2$/,use:'url-loader?limit=16950'}
```
limit指的是界限，如果图片比这这个数值大，就还是图片，如果比这个数值小，就用base64格式，<br />根据 base64 的编码原理，大小比原文件大小大 1/3
<a name="U5H3L"></a>
#### 处理高级的JS语法
1、安装babel转换器相关的包：npm i babel-core babel-loader babel-plugin-transform-runtime -D<br />                                                  npm i babel-preset-env babel-preset-stage-0 -D<br />2、在webpack.config.js中的rules数组中，添加loader规则（只让babel-loader转换程序员自己手写的代码，提高转换的效率，防止不必要的报错）
```javascript
 { test:/\.js$/,use:'babel-loader',exclude:'/node_modules'}
```
3、根目录下创建babel.config.js  文件
```javascript
module.exports = {
    presets: [
        ['@babel/preset-env']
    ],
    plugins: ['@babel/plugin-proposal-class-properties']
}

```
<a name="Gr08K"></a>
#### 配置vue组件的加载器
1、运行 npm i vue-loader vue-template-compiler -D<br />2、在webpack.config.js配置文件中，添加vue-loader的配置如下
```javascript
const VueLoaderPlugin = require('vue-loader/lib/plugin')
module.exports = {
	module:{
  	rules:[
    	//...其他规则
      {test:/\.vue$/,loader:'vue-loader'}
    ]
  },
  plugins:[
  	//...其他插件
    new VueLoaderPlugin()  //引入这个插件
  ]
}
```
<a name="HDuhH"></a>
### webpack打包发布
通过package.json文件配置打包指令
```javascript
 "scripts": {
'		"build":"webpack -p"
  },
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

