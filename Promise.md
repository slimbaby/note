**参考文档：**[https://es6.ruanyifeng.com/#docs/promise](https://es6.ruanyifeng.com/#docs/promise)<br />**参考视频：**[https://www.bilibili.com/video/BV1WE411P7e6?p=20&spm_id_from=pageDriver](https://www.bilibili.com/video/BV1WE411P7e6?p=20&spm_id_from=pageDriver)（已看前20节）<br />**Promise** :是ES6中的新语法，是一个构造函数，每个new出来的Promise的实例对象，就是为了**异步编程的新方案（旧方案是纯回调形式  ）**纯回调的回调函数在启动异步任务之前就要指定相应的回调函数，而promise可以在启动异步任务之后再指定<br />**作用**：.then链式调用，调用串联多个同步/异步任务，（异步任务要用promise包裹）解决了回调地狱的问题<br />**回调地狱**：指的是回调函数中，嵌套回调函数的代码形式，如果嵌套的层级很深，回调函数的参数以上一个回调函数的结果为条件，就是回调地狱。<br />**缺点**：不利于代码的阅读，维护和后期拓展。<br />**状态：**pending、resolved、rejected,成功的结果数据称为value,失败的结果数据称为reason，先更新状态，再执行回调函数<br />声明一个promise对象
```javascript
   const p = new Promise((resolve, reject) => {
            setTimeout(() => {
                const time = Date.now()
                if (time % 2 === 0) {
                    resolve('回调成功')
                } else {
                    reject('回调失败')
                }
            }, 1000)
        })

        p.then((value) => { console.log('成功的'); }, (value) => { console.log('失败的'); })
```
**如果想终止在某个执行链的位置，可以用promise.reject(new Errroe( ))  然后就不会继续走.then 了，会进入catch**
```javascript
new Promise(function(resolve, reject) {
    resolve(1)
}).then(result => {
    return result + 1
}).then(result => {
    return result + 1
}).then(result => {
  return  Promise.reject(new Error(result + '失败'))
   // return result + 1
}).then(result => {
    return result + 1
}).catch(error => {	
    alert(error)
})
```
<a name="6bkkk"></a>
### 实例方法(挂载在原型对象prototype身上的)
<a name="MxyYp"></a>
##### .then()

- 得到异步任务正确的结果，可以同时调用多个成功的事件或者多个失败的事件，都会执行，.then本身是同步执行的代码，.then里面的回调函数是异步执行的，记住<br />
<a name="wukMs"></a>
##### .catch()

- 获取异常信息，同上<br />
<a name="8cbby"></a>
##### .finally()

- 成功与否都会执行（不是正式标准）
<a name="0fPe8"></a>
##### .allSettled()

- 不管成功失败都会回传，并传回失败成功的参数（待自己操作一下）



如果得到某个对象，是Promise类型的实例对象，那么必然可以调用.then（）为它指定成功和失败的回调，第一个必须是成功的回调，不能省略，第二个参数是失败的回调，可以被省略,可以用.catch方法，捕获前面所有.then( )中发生的错误，集中处理一个catch就够了(比如读取文件1，文件2，文件3...失败)
<a name="hGpB4"></a>
### 静态方法
<a name="YbfbX"></a>
##### .all()

- Promise.all方法接受一个数组作参数，数组中的对象（p1、p2、p3）均为promise实例（如果不是一个promise，该项会被用Promise.resolve转换为一个promise)。它的状态由这三个promise实例决定<br />
- 所有promise成功了之后才会走第一个回调，只要有一个失败了，就会走错误的回调<br />
- 不是按照回调速度进行排列结果，而是以书写顺序排列。<br />
- ![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1615985559108-a5becc4b-17bb-403a-8be5-2a080e0d4982.png#align=left&display=inline&height=94&margin=%5Bobject%20Object%5D&name=image.png&originHeight=94&originWidth=553&size=45377&status=done&style=none&width=553)
<a name="Chr0X"></a>
##### .race()
Promise.race方法同样接受一个数组作参数。当p1, p2, p3中有一个实例的状态发生改变（变为fulfilled或rejected），p的状态就跟着改变。并把第一个改变状态（成功或失败）的promise的返回值，传给p的回调函数
<a name="qJxti"></a>
##### .reject()
 是执行器的语法糖，不用执行器再进行判断，比如说产生一个值为1 的promise对象<br />const p = Promise.resolve(1)
<a name="a7hkS"></a>
##### .resolve()  同上
<a name="9B1cB"></a>
### promise的异常传透
1、当使用promise的then链式调用时，可以在最后指定失败的回调<br />2、前面任何操作出现了异常，都会传到最后失败的回调中处理，相当于给每个.then( )里面添加了一个<br />reason =>{throw reason}  或者 reason =>Promise.reject(reason)
<a name="1Up2k"></a>
### 中断promise链
1、当使用promise的then链式调用时，在中间中断，不再调用后面的回调函数<br />2、办法：在回调函数中返回一个pending状态的promise对象
<a name="p7fBm"></a>
### Promise、async和await

- async作为一个关键字放到函数前面
   - 任何一个async函数都会隐式返回一个promise<br />
- await关键字只能在使用async定义的函数中使用
   -     await后面可以直接跟一个 Promise实例对象<br />
   -     await函数不能单独使用
   -   有async 和await 的函数中，写在await函数之后的操作必定要先等await函数执行完成后再执行
   - await只会等到resolve,不会等到reject
- **async/await 让异步代码看起来、表现起来更像同步代码**
<a name="MY4R3"></a>
#### try/catch
promise 可以通过catch捕获，async/await 捕获异常要通过try/catch

![image.png](https://cdn.nlark.com/yuque/0/2021/png/12526667/1617192127082-633737ec-9a6e-435d-a00e-419f02b386a9.png#align=left&display=inline&height=212&margin=%5Bobject%20Object%5D&name=image.png&originHeight=212&originWidth=437&size=43519&status=done&style=none&width=437)
<a name="X5Ts2"></a>
### ES5怎么自定义模块
自执行函数（IIFE）
<a name="jqt41"></a>
### Promise的简易实现版本
```javascript
const PENDING = "pending";
const RESOLVED = "resolved";
const REJECTED = "rejected";
// promise主体实现
function MyPromise(fn) {
  const that = this;
  that.state = PENDING;
  that.value = null;
  //成功存放方法的数组
  that.resolvedCallbacks = [];
  //失败存放方法的数组
  that.rejectedCallbacks = [];
  function resolve(value) {
    if (that.state === PENDING) {
      that.state = RESOLVED;
      that.value = value;
      that.resolvedCallbacks.map((cb) => {
        cb(value);
      });
    }
  }
  function reject(value) {
    if (that.state === PENDING) {
      that.state = REJECTED;
      that.value = value;
      that.rejectedCallbacks.map((cb) => {
        cb(value);
      });
    }
  }
  try {
    fn(resolve, reject);
  } catch (e) {
    reject(e);
  }
}
// then的实现
MyPromise.prototype.then = function (onFulfilled, onRejected) {
  const that = this;
  onFulfilled = typeof onFulfilled === "function" ? onFulfilled : (v) => v;
  onRejected =
    typeof onRejected === "function"
      ? onRejected
      : (r) => {
          throw r;
        };
  if (that.state === PENDING) {
    that.resolvedCallbacks.push(onFulfilled);
    that.rejectedCallbacks.push(onRejected);
  }
  if (that.state === RESOLVED) {
    onFulfilled(that.value);
  }
  if (that.state === REJECTED) {
    onRejected(that.value);
  }
};

```


<a name="kLpOZ"></a>
### 区别实例对象和函数对象
实例对象：构造函数new出来的实例，叫做实例对象<br />函数对象：Fn( ),比如说Fn.call( )    call方法是挂在在Function原型身上的方法，比如说jquery的$就是函数对象<br />（括号左边是函数，.左边是对象）
<a name="HvaPV"></a>
### 回调函数的两种类型
同步函数/异步函数，怎么判断同步异步==>在适宜的位置log，判断log的顺序
<a name="NKQTP"></a>
### JS的Error处理
<a name="d7aOx"></a>
#### 错误类型
Error:所有错误的父类型<br />ReferenceError:引用的变量不存在（比如说声明了未赋值）<br />TypeError:数据类型不正确的错误（比如说b.xxx is not a function）<br />RangeError:数据值不在其所允许的范围内（比如说栈溢出）<br />SyntaxError:语法错误
<a name="8w5nr"></a>
#### 捕获错误/抛出错误
捕获错误：try{ }catch（error）{console.log(error) }<br />抛出错误：throw new Error('错误信息')，后面用catch（error）接收
<a name="akJul"></a>
#### 错误对象
error:是一个错误对象，有message和stack等一些属性<br />message:错误相关信息<br />stack：函数调用栈记录信息
<a name="JN24n"></a>
### Promise题
```javascript
     new Promise((resolve, reject) => {
            resolve(1)
        }).then(
            value=>{
                console.log('onResolved1()',value)
            },
            reason=>{
                console.log('onRejected1()',reason);
            }
        ).then(
            value=>{
                console.log('onResolved2()',value)
            },
            reason=>{
                console.log('onRejected2()',reason);
            }
        )

onResolved1(),1
onResolved2(),undefined
//跟当前执行的是成功的回调还是失败的回调没有影响，主要看抛出来的东西
//如果抛出的是异常，新promise变为rejected,reason为抛出的异常
//如果抛出的是非promise的任意值，新promise变为resolved,value为返回值
//如果返回的是另一个新promise,此promise的结果就会成为新的promise的结果
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
<br />

