vuex可以进行全局的状态管理，但刷新后刷新后数据会消失，这是我们不愿意看到的。怎么解决呢，我们可以结合本地存储做到数据持久化，也可以通过插件-vuex-persistedstate
<a name="neArF"></a>
#### 利用vuex-persistedstate插件
插件的原理其实也是结合了存储方式,只是统一的配置就不需要手动每次都写存储方法<br />1、npm install vuex-persistedstate --save<br />2、引入及配置,在store下的index.js中（默认存储到localStorage）
```javascript
import createPersistedState from "vuex-persistedstate"
const store = new Vuex.Store({
  // ...
  plugins: [createPersistedState()]
})
```
<a name="cSbBT"></a>
#### 想要存储到sessionStorage，配置如下
```javascript
import createPersistedState from "vuex-persistedstate"
const store = new Vuex.Store({
  // ...
  plugins: [createPersistedState({
      storage: window.sessionStorage
  })]
})
```
<a name="hQAlk"></a>
##### 想使用cookie同理
```javascript
import persistedState from 'vuex-persistedstate'
import * as Cookies from 'js-cookie'

export default new Vuex.Store({
  // ...
  plugins: [
    persistedState({
      storage: {
        getItem: key => Cookies.get(key),
        setItem: (key, value) => Cookies.set(key, value, { expires: 7 }),
        removeItem: key => Cookies.remove(key)
      }
    })
  ]
})
```
默认持久化所有state<br />

<a name="gKHwh"></a>
#### 指定需要持久化的state,配置如下
```javascript
import createPersistedState from "vuex-persistedstate"
const store = new Vuex.Store({
  // ...
  plugins: [createPersistedState({
      storage: window.sessionStorage,
      reducer(val) {
          return {
          // 只储存state中的assessmentData
          assessmentData: val.assessmentData
        }
     }
  })]
```
<a name="QK6oL"></a>
#### vuex引用多个插件的写法
```javascript
import createPersistedState from "vuex-persistedstate"
import createLogger from 'vuex/dist/logger'
// 判断环境 vuex提示生产环境中不使用
const debug = process.env.NODE_ENV !== 'production'
const createPersisted = createPersistedState({
  storage: window.sessionStorage
})
export default new Vuex.Store({
 // ...
  plugins: debug ? [createLogger(), createPersisted] : [createPersisted]
})
```
