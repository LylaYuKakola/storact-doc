## STORACT

使用 'react-hooks API', 类似redux的react状态管理工具

源码及示例: [github](https://github.com/LylaYuKakola/storact)

### 介绍

对比redux，做出了以下修改

1. 使用react-hooks，通过use的方式代替'mapStateToProps'和'mapDispatchToProps'
2. 去掉声明式的action
3. 固化基础的reducer，减少基础操作的定义
4. 参考dva，增加effects的定义
5. 增加dispatch的配置，使其拥有延迟触发、防抖节流、异步挂起的功能
6. 参考dva，去掉"单一数据源"的概念，改为多数据源，并真正实现各个数据源隔离

### 示例

```
git clone https://github.com/LylaYuKakola/storact.git
npm intall
npm start
```
/dome/src/

### 开始

```
npm install storact
```

#### step 1

```javascript
import storact from 'storact'

const {
  useDispatch,
  useStoreState,
  Provider,
} = storact({
  initialState, // store的初始状态 - optional
  middlewares, // 中间件集合 - optional
  effects, // effect集合 - optional
  namespace, // 命名空间 - optional
})

export { useDispatch, useStoreState, Provider }
```
